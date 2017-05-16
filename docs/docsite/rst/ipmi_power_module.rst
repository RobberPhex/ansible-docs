.. _ipmi_power:


ipmi_power - Power management for machine
+++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Use this module for power management


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * pyghmi


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
        <td><div>Hostname or ip address of the BMC.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password to connect to the BMC.</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>623</td>
        <td></td>
        <td><div>Remote RMCP port.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>on -- Request system turn on</li><li>off -- Request system turn off without waiting for OS to shutdown</li><li>shutdown -- Have system request OS proper shutdown</li><li>reset -- Request system reset without waiting for OS</li><li>boot -- If system is off, then 'on', else 'reset'</li></ul></td>
        <td><div>Whether to ensure that the machine in desired state.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td></td>
        <td><div>Maximum number of seconds before interrupt request.</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Username to use to connect to the BMC.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure machine is powered on.
    - ipmi_power:
        name: test.testdomain.com
        user: admin
        password: password
        state: on

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
        <td> powerstate </td>
        <td> The current power state of the machine. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> True </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
