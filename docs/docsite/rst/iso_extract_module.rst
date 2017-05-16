.. _iso_extract:


iso_extract - Extract files from an ISO image.
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module mounts an iso image in a temporary directory and extracts files from there to a given destination.




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
                <tr><td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The destination directory to extract files to.</div>        </td></tr>
                <tr><td>files<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>A list of files to extract from the image.</div><div>Extracting directories does not work.</div>        </td></tr>
                <tr><td>image<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The ISO image to extract files from.</div></br>
    <div style="font-size: small;">aliases: path, src<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Extract kernel and ramdisk from a LiveCD
      iso_extract:
        image: /tmp/rear-test.iso
        dest: /tmp/virt-rear/
        files:
        - isolinux/kernel
        - isolinux/initrd.cgz


Notes
-----

.. note::
    - Only the file hash (content) is taken into account for extracting files from the ISO image.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
