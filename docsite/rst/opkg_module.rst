.. _opkg:


opkg - Package manager for OpenWrt
++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages OpenWrt packages




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
    <td>force<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>absent</td>
        <td><ul><li></li><li>depends</li><li>maintainer</li><li>reinstall</li><li>overwrite</li><li>downgrade</li><li>space</li><li>postinstall</li><li>remove</li><li>checksum</li><li>removal-of-dependent-packages</li></ul></td>
        <td><div>opkg --force parameter used</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of package to install/remove</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>state of the package</div></td></tr>
            <tr>
    <td>update_cache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>update the package db first</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - opkg: name=foo state=present
    - opkg: name=foo state=present update_cache=yes
    - opkg: name=foo state=absent
    - opkg: name=foo,bar state=absent
    - opkg: name=foo state=present force=overwrite




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

