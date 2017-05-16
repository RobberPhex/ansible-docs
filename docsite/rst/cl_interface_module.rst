.. _cl_interface:


cl_interface - Configures a front panel port, loopback or management port on Cumulus Linux.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Configures a front panel, sub-interface, SVI, management or loopback port on a Cumulus Linux switch. For bridge ports use the cl_bridge module. For bond ports use the cl_bond module. When configuring bridge related features like the "vid" option, please follow the guidelines for configuring "vlan aware" bridging. For more details review the Layer2 Interface Guide at http://docs.cumulusnetworks.com


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
        <td><ul><li>loopback</li><li>dhcp</li></ul></td>
        <td><div>Address method.</div></td></tr>
            <tr>
    <td>alias_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Description of the port.</div></td></tr>
            <tr>
    <td>clagd_enable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Enables the clagd daemon. This command should only be applied to the clag peerlink interface.</div></td></tr>
            <tr>
    <td>clagd_peer_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>IP address of the directly connected peer switch interface.</div></td></tr>
            <tr>
    <td>clagd_priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Integer that changes the role the switch has in the clag domain. The lower priority switch will assume the primary role. The number can be between 0 and 65535.</div></td></tr>
            <tr>
    <td>clagd_sys_mac<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Clagd system mac address. Recommended to use the range starting with 44:38:39:ff. Needs to be the same between 2 Clag switches.</div></td></tr>
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
    <td>location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>[u'/etc/network/interfaces.d']</td>
        <td><ul></ul></td>
        <td><div>Interface directory location</div></td></tr>
            <tr>
    <td>mstpctl_bpduguard<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Enables BPDU Guard on a port in vlan-aware mode.</div></td></tr>
            <tr>
    <td>mstpctl_portadminedge<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Enables admin edge port.</div></td></tr>
            <tr>
    <td>mstpctl_portnetwork<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
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
    <td>speed<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Set speed of the swp(front panel) or management(eth0) interface. speed is in MB.</div></td></tr>
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
        </table>
    </br>



Examples
--------

 ::

    # Options ['virtual_mac', 'virtual_ip'] are required together
    # configure a front panel port with an IP
    cl_interface: name=swp1  ipv4=10.1.1.1/24
    notify: reload networking
    
    # configure front panel to use DHCP
    cl_interface: name=swp2 addr_family=dhcp
    notify: reload networking
    
    # configure a SVI for vlan 100 interface with an IP
    cl_interface: name=bridge.100 ipv4=10.1.1.1/24
    notify: reload networking
    
    # configure subinterface with an IP
    cl_interface: name=bond0.100  alias_name='my bond' ipv4=10.1.1.1/24
    notify: reload networking
    
    # define cl_interfaces once in tasks
    # then write interfaces in variables file
    # with just the options you want.
    cl_interface:
      name: "{{ item.key }}"
      ipv4: "{{ item.value.ipv4|default(omit) }}"
      ipv6: "{{ item.value.ipv6|default(omit) }}"
      alias_name: "{{ item.value.alias_name|default(omit) }}"
      addr_method: "{{ item.value.addr_method|default(omit) }}"
      speed: "{{ item.value.link_speed|default(omit) }}"
      mtu: "{{ item.value.mtu|default(omit) }}"
      clagd_enable: "{{ item.value.clagd_enable|default(omit) }}"
      clagd_peer_ip: "{{ item.value.clagd_peer_ip|default(omit) }}"
      clagd_sys_mac: "{{ item.value.clagd_sys_mac|default(omit) }}"
      clagd_priority: "{{ item.value.clagd_priority|default(omit) }}"
      vids: "{{ item.value.vids|default(omit) }}"
      virtual_ip: "{{ item.value.virtual_ip|default(omit) }}"
      virtual_mac: "{{ item.value.virtual_mac|default(omit) }}"
      mstpctl_portnetwork: "{{ item.value.mstpctl_portnetwork|default('no') }}"
      mstpctl_portadminedge: "{{ item.value.mstpctl_portadminedge|default('no') }}"
      mstpctl_bpduguard: "{{ item.value.mstpctl_bpduguard|default('no') }}"
    with_dict: cl_interfaces
    notify: reload networking
    
    
    # In vars file
    # ============
    cl_interfaces:
        swp1:
            alias_name: 'uplink to isp'
            ipv4: '10.1.1.1/24'
        swp2:
            alias_name: 'l2 trunk connection'
            vids: [1, 50]
        swp3:
            speed: 1000
            alias_name: 'connects to 1G link'
    ##########
    #   br0 interface is configured by cl_bridge
    ##########
        br0.100:
            alias_name: 'SVI for vlan 100'
            ipv4: '10.2.2.2/24'
            ipv6: '10:2:2::2/127'
            virtual_ip: '10.2.2.254'
            virtual_mac: '00:00:5E:00:10:10'
    
    

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

