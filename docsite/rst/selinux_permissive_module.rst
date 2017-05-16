.. _selinux_permissive:


selinux_permissive - Change permissive domain in SELinux policy
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Add and remove domain from the list of permissive domain.


Requirements
------------

  * policycoreutils-python


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
            <tr>
    <td>domain<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the domain that will be added or removed from the list of permissive domains</div></td></tr>
            <tr>
    <td>no_reload<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>automatically reload the policy after a change</div><div>default is set to 'false' as that's what most people would want after changing one domain</div><div>Note that this doesn't work on older version of the library (example EL 6), the module will silently ignore it in this case</div></td></tr>
            <tr>
    <td>permissive<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>indicate if the domain should or should not be set as permissive</div></td></tr>
            <tr>
    <td>store<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the SELinux policy store to use</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - selinux_permissive: name=httpd_t permissive=true


Notes
-----

.. note:: Requires a version of SELinux recent enough ( ie EL 6 or newer )


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

