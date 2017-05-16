.. _win_disk_image:


win_disk_image - Manage ISO/VHD/VHDX mounts on Windows hosts
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages mount behavior for a specified ISO, VHD, or VHDX image on a Windows host. When ``state`` is ``present``, the image will be mounted under a system-assigned drive letter, which will be returned in the ``mount_path`` value of the module result. Requires Windows 8+ or Windows Server 2012+.




Options
-------

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">parameter</th>
    <th class="head">required</th>
    <th class="head">default</th>
    <th class="head">choices</th>
    <th class="head">comments</th>
    </tr>
                <tr><td>image_path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>path to an ISO, VHD, or VHDX image on the target Windows host (the file cannot reside on a network share)</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>whether the image should be present as a drive-letter mount or not.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # ensure an iso is mounted
    - win_disk_image:
        image_path: C:\install.iso
        state: present
      register: disk_image_out
    
    # run installer from mounted iso
    - win_package:
        path: '{{ disk_image_out.mount_path }}setup\setup.exe'
        product_id: '35a4e767-0161-46b0-979f-e61f282fee21'
        state: present
    
    # unmount iso
    - win_disk_image:
        image_path: C:\install.iso
        state: absent
    

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> mount_path </td>
        <td> filesystem path where the target image is mounted </td>
        <td align=center> when C(state) is C(present) </td>
        <td align=center> string </td>
        <td align=center> F:\ </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
