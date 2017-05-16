.. _selinux:


selinux - Change policy and state of SELinux
++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Configures the SELinux mode and policy. A reboot may be required after usage. Ansible will not issue this reboot but will let you know when it is required.


Requirements (on host that executes module)
-------------------------------------------

  * libselinux-python


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
                <tr><td>conf<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/etc/selinux/config</td>
        <td></td>
        <td><div>path to the SELinux configuration file, if non-standard</div>        </td></tr>
                <tr><td>policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>name of the SELinux policy to use (example: <code>targeted</code>) will be required if state is not <code>disabled</code></div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>enforcing</li><li>permissive</li><li>disabled</li></ul></td>
        <td><div>The SELinux mode</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Enable SELinux
    - selinux:
        policy: targeted
        state: enforcing
    
    # Put SELinux in permissive mode, logging actions that would be blocked.
    - selinux:
        policy: targeted
        state: permissive
    
    # Disable SELinux
    - selinux:
        state: disabled


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
