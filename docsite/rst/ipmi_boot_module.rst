.. _ipmi_boot:


ipmi_boot - Management of order of boot devices
+++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Use this module to manage order of boot devices


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
            <tr>
    <td>bootdev<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>network -- Request network boot</li><li>hd -- Boot from hard drive</li><li>safe -- Boot from hard drive, requesting 'safe mode'</li><li>optical -- boot from CD/DVD/BD drive</li><li>setup -- Boot into setup utility</li><li>default -- remove any IPMI directed boot device request</li></ul></td>
        <td><div>Set boot device to use on next reboot</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Hostname or ip address of the BMC.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Password to connect to the BMC.</div></td></tr>
            <tr>
    <td>persistent<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If set, ask that system firmware uses this device beyond next boot. Be aware many systems do not honor this.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>623</td>
        <td><ul></ul></td>
        <td><div>Remote RMCP port.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present -- Request system turn on</li><li>absent -- Request system turn on</li></ul></td>
        <td><div>Whether to ensure that boot devices is desired.</div></td></tr>
            <tr>
    <td>uefiboot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If set, request UEFI boot explicitly. Strictly speaking, the spec suggests that if not set, the system should BIOS boot and offers no "don't care" option. In practice, this flag not being set does not preclude UEFI boot on any system I've encountered.</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Username to use to connect to the BMC.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure bootdevice is HD.
    - ipmi_boot: name="test.testdomain.com" user="admin" password="password" bootdev="hd"
    # Ensure bootdevice is not Network
    - ipmi_boot: name="test.testdomain.com" user="admin" password="password" bootdev="network" state=absent

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
        <td> bootdev </td>
        <td> The boot device name which will be used beyond next boot. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> default </td>
    </tr>
            <tr>
        <td> uefimode </td>
        <td> If True, system firmware will use UEFI boot explicitly beyond next boot. </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> persistent </td>
        <td> If True, system firmware will use this device beyond next boot. </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> False </td>
    </tr>
        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

