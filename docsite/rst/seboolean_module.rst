.. _seboolean:


seboolean - Toggles SELinux booleans.
+++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Toggles SELinux booleans.




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
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the boolean to configure</div></td></tr>
            <tr>
    <td>persistent<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Set to <code>yes</code> if the boolean setting should survive a reboot</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Desired boolean value</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Set (httpd_can_network_connect) flag on and keep it persistent across reboots
    - seboolean: name=httpd_can_network_connect state=yes persistent=yes


Notes
-----

.. note:: Not tested on any debian based system


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

