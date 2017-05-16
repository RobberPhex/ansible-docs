.. _dladm_vlan:


dladm_vlan - Manage VLAN interfaces on Solaris/illumos systems.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create or delete VLAN interfaces on Solaris/illumos systems.




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
                <tr><td>link<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>VLAN underlying link name.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>VLAN interface name.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Create or delete Solaris/illumos VNIC.</div>        </td></tr>
                <tr><td>temporary<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies that the VLAN interface is temporary. Temporary VLANs do not persist across reboots.</div>        </td></tr>
                <tr><td>vlan_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>VLAN ID value for VLAN interface.</div></br>
    <div style="font-size: small;">aliases: vid<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    name: Create 'vlan42' VLAN over 'bnx0' link
    dladm_vlan: name=vlan42 link=bnx0 vlan_id=42 state=present
    
    name: Remove 'vlan1337' VLAN interface
    dladm_vlan: name=vlan1337 state=absent

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
        <td> temporary </td>
        <td> specifies if operation will persist across reboots </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> state </td>
        <td> state of the target </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> present </td>
    </tr>
            <tr>
        <td> link </td>
        <td> VLAN's underlying link name </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> e100g0 </td>
    </tr>
            <tr>
        <td> name </td>
        <td> VLAN name </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> vlan42 </td>
    </tr>
            <tr>
        <td> vlan_id </td>
        <td> VLAN ID </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 42 </td>
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
