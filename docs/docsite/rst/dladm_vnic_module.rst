.. _dladm_vnic:


dladm_vnic - Manage VNICs on Solaris/illumos systems.
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create or delete VNICs on Solaris/illumos systems.




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
        <td><div>VNIC underlying link name.</div>        </td></tr>
                <tr><td>mac<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets the VNIC's MAC address. Must be valid unicast MAC address.</div></br>
    <div style="font-size: small;">aliases: macaddr<div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>VNIC name.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Create or delete Solaris/illumos VNIC.</div>        </td></tr>
                <tr><td>temporary<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Specifies that the VNIC is temporary. Temporary VNICs do not persist across reboots.</div>        </td></tr>
                <tr><td>vlan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enable VLAN tagging for this VNIC. The VLAN tag will have id <em>vlan</em>.</div></br>
    <div style="font-size: small;">aliases: vlan_id<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create 'vnic0' VNIC over 'bnx0' link
    - dladm_vnic:
        name: vnic0
        link: bnx0
        state: present
    
    # Create VNIC with specified MAC and VLAN tag over 'aggr0'
    - dladm_vnic:
        name: vnic1
        link: aggr0
        mac: '00:00:5E:00:53:23'
        vlan: 4
    
    # Remove 'vnic0' VNIC
    - dladm_vnic:
        name: vnic0
        link: bnx0
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
        <td> state </td>
        <td> state of the target </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> present </td>
    </tr>
            <tr>
        <td> temporary </td>
        <td> VNIC's persistence </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> name </td>
        <td> VNIC name </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> vnic0 </td>
    </tr>
            <tr>
        <td> link </td>
        <td> VNIC underlying link name </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> igb0 </td>
    </tr>
            <tr>
        <td> vlan </td>
        <td> VLAN to use for VNIC </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 42 </td>
    </tr>
            <tr>
        <td> mac </td>
        <td> MAC address to use for VNIC </td>
        <td align=center> if mac is specified </td>
        <td align=center> string </td>
        <td align=center> 00:00:5E:00:53:42 </td>
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
