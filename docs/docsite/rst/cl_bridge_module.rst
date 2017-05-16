.. _cl_bridge:


cl_bridge - Configures a bridge port on Cumulus Linux
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2

DEPRECATED
----------

Deprecated in 2.3. Use :ref:`nclu <nclu>` instead.

Synopsis
--------

* Configures a bridge interface on Cumulus Linux To configure a bond port use the cl_bond module. To configure any other type of interface use the cl_interface module. Follow the guidelines for bridging found in the Cumulus User Guide at http://docs.cumulusnetworks.com


Requirements (on host that executes module)
-------------------------------------------

  * Alternate Debian network interface manager ifupdown2 @ github.com/CumulusNetworks/ifupdown2


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
                <tr><td>addr_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>dhcp</li></ul></td>
        <td><div>Configures the port to use DHCP. To enable this feature use the option <em>dhcp</em>.</div>        </td></tr>
                <tr><td>alias_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Description of the port.</div>        </td></tr>
                <tr><td>ipv4<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of IPv4 addresses to configure on the interface. In the form <em>X.X.X.X/YY</em>.</div>        </td></tr>
                <tr><td>ipv6<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of IPv6 addresses to configure on the interface. In the form <em>X:X:X::X/YYY</em>.</div>        </td></tr>
                <tr><td>location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>[u'/etc/network/interfaces.d']</td>
        <td></td>
        <td><div>Interface directory location.</div>        </td></tr>
                <tr><td>mstpctl_treeprio<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set spanning tree root priority. Must be a multiple of 4096.</div>        </td></tr>
                <tr><td>mtu<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set MTU. Configure Jumbo Frame by setting MTU to <em>9000</em>.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the interface.</div>        </td></tr>
                <tr><td>ports<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>List of bridge members.</div>        </td></tr>
                <tr><td>pvid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>In vlan-aware mode, defines vlan that is the untagged vlan.</div>        </td></tr>
                <tr><td>stp<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Enables spanning tree Protocol. As of Cumulus Linux 2.5 the default bridging mode, only per vlan RSTP or 802.1d is supported. For the vlan aware mode, only common instance STP is supported</div>        </td></tr>
                <tr><td>vids<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>In vlan-aware mode, lists VLANs defined under the interface.</div>        </td></tr>
                <tr><td>virtual_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Define IPv4 virtual IP used by the Cumulus Linux VRR feature.</div>        </td></tr>
                <tr><td>virtual_mac<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Define Ethernet mac associated with Cumulus Linux VRR feature.</div>        </td></tr>
                <tr><td>vlan_aware<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Enables vlan-aware mode.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Options ['virtual_mac', 'virtual_ip'] are required together
    # configure a bridge vlan aware bridge.
    - cl_bridge:
        name: br0
        ports: 'swp1-12'
        vlan_aware: 'yes'
      notify: reload networking
    
    # configure bridge interface to define a default set of vlans
    - cl_bridge:
        name: bridge
        ports: 'swp1-12'
        vlan_aware: 'yes'
        vids: '1-100'
      notify: reload networking
    
    # define cl_bridge once in tasks file
    # then write interface config in variables file
    # with just the options you want.
    - cl_bridge:
        name: "{{ item.key }}"
        ports: "{{ item.value.ports }}"
        vlan_aware: "{{ item.value.vlan_aware|default(omit) }}"
        ipv4:  "{{ item.value.ipv4|default(omit) }}"
        ipv6: "{{ item.value.ipv6|default(omit) }}"
        alias_name: "{{ item.value.alias_name|default(omit) }}"
        addr_method: "{{ item.value.addr_method|default(omit) }}"
        mtu: "{{ item.value.mtu|default(omit) }}"
        vids: "{{ item.value.vids|default(omit) }}"
        virtual_ip: "{{ item.value.virtual_ip|default(omit) }}"
        virtual_mac: "{{ item.value.virtual_mac|default(omit) }}"
        mstpctl_treeprio: "{{ item.value.mstpctl_treeprio|default(omit) }}"
      with_dict: "{{ cl_bridges }}"
      notify: reload networking
    
    # In vars file
    # ============
    ---
    cl_bridge:
      br0:
        alias_name: 'vlan aware bridge'
        ports: ['swp1', 'swp3']
        vlan_aware: true
        vids: ['1-100']

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

.. note::
    - As this module writes the interface directory location, ensure that ``/etc/network/interfaces`` has a 'source /etc/network/interfaces.d/\*' or whatever path is mentioned in the ``location`` attribute.
    - For the config to be activated, i.e installed in the kernel, "service networking reload" needs be be executed. See EXAMPLES section.


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
