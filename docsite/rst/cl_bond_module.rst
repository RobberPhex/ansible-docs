.. _cl_bond:


cl_bond - Configures a bond port on Cumulus Linux
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Configures a bond interface on Cumulus Linux To configure a bridge port use the cl_bridge module. To configure any other type of interface use the cl_interface module. Follow the guidelines for bonding found in the Cumulus User Guide at http://docs.cumulusnetworks.com.


Requirements (on host that executes module)
-------------------------------------------

  * Alternate Debian network interface manager - ifupdown2 @ github.com/CumulusNetworks/ifupdown2


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
    <td>addr_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>dhcp</li></ul></td>
        <td><div>Configures the port to use DHCP. To enable this feature use the option <em>dhcp</em>.</div></td></tr>
            <tr>
    <td>alias_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Description of the port.</div></td></tr>
            <tr>
    <td>clag_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify a unique clag_id for every dual connected bond on each peer switch. The value must be between 1 and 65535 and must be the same on both peer switches in order for the bond to be considered dual-connected.</div></td></tr>
            <tr>
    <td>ipv4<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of IPv4 addresses to configure on the interface. In the form <em>X.X.X.X/YY</em>.</div></td></tr>
            <tr>
    <td>ipv6<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of IPv6 addresses to configure on the interface. In the form <em>X:X:X::X/YYY</em>.</div></td></tr>
            <tr>
    <td>lacp_bypass_all_active<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Activate all interfaces for bypass. It is recommended to configure all_active instead of using bypass_priority.</div></td></tr>
            <tr>
    <td>lacp_bypass_allow<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Enable LACP bypass.</div></td></tr>
            <tr>
    <td>lacp_bypass_period<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Period for enabling LACP bypass. Max value is 900.</div></td></tr>
            <tr>
    <td>lacp_bypass_priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of ports and priorities. Example <em>"swp1=10, swp2=20"</em>.</div></td></tr>
            <tr>
    <td>lacp_rate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>The lacp rate.</div></td></tr>
            <tr>
    <td>location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>[u'/etc/network/interfaces.d']</td>
        <td><ul></ul></td>
        <td><div>Interface directory location.</div></td></tr>
            <tr>
    <td>miimon<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>100</td>
        <td><ul></ul></td>
        <td><div>The mii link monitoring interval.</div></td></tr>
            <tr>
    <td>min_links<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>Minimum number of links.</div></td></tr>
            <tr>
    <td>mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>802.3ad</td>
        <td><ul></ul></td>
        <td><div>The bond mode, as of Cumulus Linux 2.5 only LACP bond mode is supported.</div></td></tr>
            <tr>
    <td>mstpctl_bpduguard<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Enables BPDU Guard on a port in vlan-aware mode.</div></td></tr>
            <tr>
    <td>mstpctl_portadminedge<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Enables admin edge port.</div></td></tr>
            <tr>
    <td>mstpctl_portnetwork<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Enables bridge assurance in vlan-aware mode.</div></td></tr>
            <tr>
    <td>mtu<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set MTU. Configure Jumbo Frame by setting MTU to <em>9000</em>.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the interface.</div></td></tr>
            <tr>
    <td>pvid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>In vlan-aware mode, defines vlan that is the untagged vlan.</div></td></tr>
            <tr>
    <td>slaves<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Bond members.</div></td></tr>
            <tr>
    <td>vids<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>In vlan-aware mode, lists VLANs defined under the interface.</div></td></tr>
            <tr>
    <td>virtual_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Define IPv4 virtual IP used by the Cumulus Linux VRR feature.</div></td></tr>
            <tr>
    <td>virtual_mac<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Define Ethernet mac associated with Cumulus Linux VRR feature.</div></td></tr>
            <tr>
    <td>xmit_hash_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>layer3+4</td>
        <td><ul></ul></td>
        <td><div>Transmit load balancing algorithm. As of Cumulus Linux 2.5 only <em>layer3+4</em> policy is supported.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Options ['virtual_mac', 'virtual_ip'] are required together
    # configure a bond interface with IP address
    cl_bond: name=bond0  slaves="swp4-5" ipv4=10.1.1.1/24
    notify: reload networking
    
    # configure bond as a dual-connected clag bond
    cl_bond: name=bond1 slaves="swp1s0 swp2s0" clag_id=1
    notify: reload networking
    
    # define cl_bond once in tasks file
    # then write interface config in variables file
    # with just the options you want.
    cl_bond:
      name: "{{ item.key }}"
      slaves: "{{ item.value.slaves }}"
      clag_id: "{{ item.value.clag_id|default(omit) }}"
      ipv4:  "{{ item.value.ipv4|default(omit) }}"
      ipv6: "{{ item.value.ipv6|default(omit) }}"
      alias_name: "{{ item.value.alias_name|default(omit) }}"
      addr_method: "{{ item.value.addr_method|default(omit) }}"
      mtu: "{{ item.value.mtu|default(omit) }}"
      vids: "{{ item.value.vids|default(omit) }}"
      virtual_ip: "{{ item.value.virtual_ip|default(omit) }}"
      virtual_mac: "{{ item.value.virtual_mac|default(omit) }}"
      mstpctl_portnetwork: "{{ item.value.mstpctl_portnetwork|default('no') }}"
      mstpctl_portadminedge: "{{ item.value.mstpctl_portadminedge|default('no') }}"
      mstpctl_bpduguard: "{{ item.value.mstpctl_bpduguard|default('no') }}"
    with_dict: cl_bonds
    notify: reload networking
    
    # In vars file
    # ============
    cl_bonds:
        bond0:
            alias_name: 'uplink to isp'
            slaves: ['swp1', 'swp3']
            ipv4: '10.1.1.1/24'
        bond2:
            vids: [1, 50]
            clag_id: 1

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
        <td> msg </td>
        <td> human-readable report of success or failure </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> interface bond0 config updated </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> whether the interface was changed </td>
        <td align=center> changed </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: As this module writes the interface directory location, ensure that ``/etc/network/interfaces`` has a 'source /etc/network/interfaces.d/\*' or whatever path is mentioned in the ``location`` attribute.
.. note:: For the config to be activated, i.e installed in the kernel, "service networking reload" needs be be executed. See EXAMPLES section.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

