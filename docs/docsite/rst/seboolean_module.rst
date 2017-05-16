.. _seboolean:


seboolean - Toggles SELinux booleans.
+++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Toggles SELinux booleans.


Requirements (on host that executes module)
-------------------------------------------

  * libselinux-python
  * libsemanage-python


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
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the boolean to configure</div>        </td></tr>
                <tr><td>persistent<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Set to <code>yes</code> if the boolean setting should survive a reboot</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Desired boolean value</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Set (httpd_can_network_connect) flag on and keep it persistent across reboots
    - seboolean:
        name: httpd_can_network_connect
        state: yes
        persistent: yes


Notes
-----

.. note::
    - Not tested on any debian based system



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
