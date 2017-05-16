.. _nmcli:


nmcli - Manage Networking
+++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage the network devices. Create, modify, and manage, ethernet, teams, bonds, vlans etc.


Requirements (on host that executes module)
-------------------------------------------

  * nmcli
  * dbus


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
    <td>ageingtime<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td><div>This is only used with bridge - [ageing-time &lt;0-1000000&gt;] the Ethernet MAC address aging time, in seconds</div></td></tr>
            <tr>
    <td>arp_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>This is only used with bond - ARP interval</div></td></tr>
            <tr>
    <td>arp_ip_target<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>This is only used with bond - ARP IP target</div></td></tr>
            <tr>
    <td>autoconnect<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether the connection should start on boot.</div><div>Whether the connection profile can be automatically activated</div></td></tr>
            <tr>
    <td>conn_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Where conn_name will be the name used to call the connection. when not provided a default name is generated: &lt;type&gt;[-&lt;ifname&gt;][-&lt;num&gt;]</div></td></tr>
            <tr>
    <td>dns4<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A list of upto 3 dns servers, ipv4 format e.g. To add two IPv4 DNS server addresses: ["8.8.8.8 8.8.4.4"]</div></td></tr>
            <tr>
    <td>dns6<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of upto 3 dns servers, ipv6 format e.g. To add two IPv6 DNS server addresses: ["2001:4860:4860::8888 2001:4860:4860::8844"]</div></td></tr>
            <tr>
    <td>downdelay<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>This is only used with bond - downdelay</div></td></tr>
            <tr>
    <td>egress<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>This is only used with VLAN - VLAN egress priority mapping</div></td></tr>
            <tr>
    <td>flags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>This is only used with VLAN - flags</div></td></tr>
            <tr>
    <td>forwarddelay<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>15</td>
        <td><ul></ul></td>
        <td><div>This is only used with bridge - [forward-delay &lt;2-30&gt;] STP forwarding delay, in seconds</div></td></tr>
            <tr>
    <td>gw4<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The IPv4 gateway for this interface using this format ie: "192.168.100.1"</div></td></tr>
            <tr>
    <td>gw6<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The IPv6 gateway for this interface using this format ie: "2001:db8::1"</div></td></tr>
            <tr>
    <td>hairpin<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>This is only used with 'bridge-slave' - 'hairpin mode' for the slave, which allows frames to be sent back out through the slave the frame was received on.</div></td></tr>
            <tr>
    <td>hellotime<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>2</td>
        <td><ul></ul></td>
        <td><div>This is only used with bridge - [hello-time &lt;1-10&gt;] STP hello time, in seconds</div></td></tr>
            <tr>
    <td>ifname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>conn_name</td>
        <td><ul></ul></td>
        <td><div>Where IFNAME will be the what we call the interface name.</div><div>interface to bind the connection to. The connection will only be applicable to this interface name.</div><div>A special value of "*" can be used for interface-independent connections.</div><div>The ifname argument is mandatory for all connection types except bond, team, bridge and vlan.</div></td></tr>
            <tr>
    <td>ingress<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>This is only used with VLAN - VLAN ingress priority mapping</div></td></tr>
            <tr>
    <td>ip4<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The IPv4 address to this interface using this format ie: "192.168.1.24/24"</div></td></tr>
            <tr>
    <td>ip6<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The IPv6 address to this interface using this format ie: "abbe::cafe"</div></td></tr>
            <tr>
    <td>mac<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>This is only used with bridge - MAC address of the bridge (note: this requires a recent kernel feature, originally introduced in 3.15 upstream kernel)</div></td></tr>
            <tr>
    <td>master<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>master &lt;master (ifname, or connection UUID or conn_name) of bridge, team, bond master connection profile.</div></td></tr>
            <tr>
    <td>maxage<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>20</td>
        <td><ul></ul></td>
        <td><div>This is only used with bridge - [max-age &lt;6-42&gt;] STP maximum message age, in seconds</div></td></tr>
            <tr>
    <td>miimon<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>100</td>
        <td><ul></ul></td>
        <td><div>This is only used with bond - miimon</div></td></tr>
            <tr>
    <td>mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>balence-rr</td>
        <td><ul><li>balance-rr</li><li>active-backup</li><li>balance-xor</li><li>broadcast</li><li>802.3ad</li><li>balance-tlb</li><li>balance-alb</li></ul></td>
        <td><div>This is the type of device or network connection that you wish to create for a bond, team or bridge.</div></td></tr>
            <tr>
    <td>mtu<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1500</td>
        <td><ul></ul></td>
        <td><div>The connection MTU, e.g. 9000. This can't be applied when creating the interface and is done once the interface has been created.</div><div>Can be used when modifying Team, VLAN, Ethernet (Future plans to implement wifi, pppoe, infiniband)</div></td></tr>
            <tr>
    <td>path_cost<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>100</td>
        <td><ul></ul></td>
        <td><div>This is only used with 'bridge-slave' - [&lt;1-65535&gt;] - STP port cost for destinations via this slave</div></td></tr>
            <tr>
    <td>primary<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>This is only used with bond and is the primary interface name (for "active-backup" mode), this is the usually the 'ifname'</div></td></tr>
            <tr>
    <td>priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>128</td>
        <td><ul></ul></td>
        <td><div>This is only used with 'bridge' - sets STP priority</div></td></tr>
            <tr>
    <td>slavepriority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>32</td>
        <td><ul></ul></td>
        <td><div>This is only used with 'bridge-slave' - [&lt;0-63&gt;] - STP priority of this slave</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the device should exist or not, taking action if the state is different from what is stated.</div></td></tr>
            <tr>
    <td>stp<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>This is only used with bridge and controls whether Spanning Tree Protocol (STP) is enabled for this bridge</div></td></tr>
            <tr>
    <td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>ethernet</li><li>team</li><li>team-slave</li><li>bond</li><li>bond-slave</li><li>bridge</li><li>vlan</li></ul></td>
        <td><div>This is the type of device or network connection that you wish to create.</div></td></tr>
            <tr>
    <td>updelay<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>This is only used with bond - updelay</div></td></tr>
            <tr>
    <td>vlandev<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>This is only used with VLAN - parent device this VLAN is on, can use ifname</div></td></tr>
            <tr>
    <td>vlanid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>This is only used with VLAN - VLAN ID in range &lt;0-4095&gt;</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    The following examples are working examples that I have run in the field. I followed follow the structure:
    ```
    |_/inventory/cloud-hosts
    |           /group_vars/openstack-stage.yml
    |           /host_vars/controller-01.openstack.host.com
    |           /host_vars/controller-02.openstack.host.com
    |_/playbook/library/nmcli.py
    |          /playbook-add.yml
    |          /playbook-del.yml
    ```
    
    ## inventory examples
    ### groups_vars
    ```yml
    ---
    #devops_os_define_network
    storage_gw: "192.168.0.254"
    external_gw: "10.10.0.254"
    tenant_gw: "172.100.0.254"
    
    #Team vars
    nmcli_team:
        - {conn_name: 'tenant', ip4: "{{tenant_ip}}", gw4: "{{tenant_gw}}"}
        - {conn_name: 'external', ip4: "{{external_ip}}", gw4: "{{external_gw}}"}
        - {conn_name: 'storage', ip4: "{{storage_ip}}", gw4: "{{storage_gw}}"}
    nmcli_team_slave:
        - {conn_name: 'em1', ifname: 'em1', master: 'tenant'}
        - {conn_name: 'em2', ifname: 'em2', master: 'tenant'}
        - {conn_name: 'p2p1', ifname: 'p2p1', master: 'storage'}
        - {conn_name: 'p2p2', ifname: 'p2p2', master: 'external'}
    
    #bond vars
    nmcli_bond:
        - {conn_name: 'tenant', ip4: "{{tenant_ip}}", gw4: '', mode: 'balance-rr'}
        - {conn_name: 'external', ip4: "{{external_ip}}", gw4: '', mode: 'balance-rr'}
        - {conn_name: 'storage', ip4: "{{storage_ip}}", gw4: "{{storage_gw}}", mode: 'balance-rr'}
    nmcli_bond_slave:
        - {conn_name: 'em1', ifname: 'em1', master: 'tenant'}
        - {conn_name: 'em2', ifname: 'em2', master: 'tenant'}
        - {conn_name: 'p2p1', ifname: 'p2p1', master: 'storage'}
        - {conn_name: 'p2p2', ifname: 'p2p2', master: 'external'}
    
    #ethernet vars
    nmcli_ethernet:
        - {conn_name: 'em1', ifname: 'em1', ip4: "{{tenant_ip}}", gw4: "{{tenant_gw}}"}
        - {conn_name: 'em2', ifname: 'em2', ip4: "{{tenant_ip1}}", gw4: "{{tenant_gw}}"}
        - {conn_name: 'p2p1', ifname: 'p2p1', ip4: "{{storage_ip}}", gw4: "{{storage_gw}}"}
        - {conn_name: 'p2p2', ifname: 'p2p2', ip4: "{{external_ip}}", gw4: "{{external_gw}}"}
    ```
    
    ### host_vars
    ```yml
    ---
    storage_ip: "192.168.160.21/23"
    external_ip: "10.10.152.21/21"
    tenant_ip: "192.168.200.21/23"
    ```
    
    
    
    ## playbook-add.yml example
    
    ```yml
    ---
    - hosts: openstack-stage
      remote_user: root
      tasks:
    
    - name: install needed network manager libs
      yum: name={{ item }} state=installed
      with_items:
        - NetworkManager-glib
        - libnm-qt-devel.x86_64
        - nm-connection-editor.x86_64
        - libsemanage-python
        - policycoreutils-python
    
    ##### Working with all cloud nodes - Teaming
      - name: try nmcli add team - conn_name only & ip4 gw4
        nmcli: type=team conn_name={{item.conn_name}} ip4={{item.ip4}} gw4={{item.gw4}} state=present
        with_items:
          - "{{nmcli_team}}"
    
      - name: try nmcli add teams-slave
        nmcli: type=team-slave conn_name={{item.conn_name}} ifname={{item.ifname}} master={{item.master}} state=present
        with_items:
          - "{{nmcli_team_slave}}"
    
    ###### Working with all cloud nodes - Bonding
    #  - name: try nmcli add bond - conn_name only & ip4 gw4 mode
    #    nmcli: type=bond conn_name={{item.conn_name}} ip4={{item.ip4}} gw4={{item.gw4}} mode={{item.mode}} state=present
    #    with_items:
    #      - "{{nmcli_bond}}"
    #
    #  - name: try nmcli add bond-slave
    #    nmcli: type=bond-slave conn_name={{item.conn_name}} ifname={{item.ifname}} master={{item.master}} state=present
    #    with_items:
    #      - "{{nmcli_bond_slave}}"
    
    ##### Working with all cloud nodes - Ethernet
    #  - name: nmcli add Ethernet - conn_name only & ip4 gw4
    #    nmcli: type=ethernet conn_name={{item.conn_name}} ip4={{item.ip4}} gw4={{item.gw4}} state=present
    #    with_items:
    #      - "{{nmcli_ethernet}}"
    ```
    
    ## playbook-del.yml example
    
    ```yml
    ---
    - hosts: openstack-stage
      remote_user: root
      tasks:
    
      - name: try nmcli del team - multiple
        nmcli: conn_name={{item.conn_name}} state=absent
        with_items:
          - { conn_name: 'em1'}
          - { conn_name: 'em2'}
          - { conn_name: 'p1p1'}
          - { conn_name: 'p1p2'}
          - { conn_name: 'p2p1'}
          - { conn_name: 'p2p2'}
          - { conn_name: 'tenant'}
          - { conn_name: 'storage'}
          - { conn_name: 'external'}
          - { conn_name: 'team-em1'}
          - { conn_name: 'team-em2'}
          - { conn_name: 'team-p1p1'}
          - { conn_name: 'team-p1p2'}
          - { conn_name: 'team-p2p1'}
          - { conn_name: 'team-p2p2'}
    ```
    # To add an Ethernet connection with static IP configuration, issue a command as follows
    - nmcli: conn_name=my-eth1 ifname=eth1 type=ethernet ip4=192.168.100.100/24 gw4=192.168.100.1 state=present
    
    # To add an Team connection with static IP configuration, issue a command as follows
    - nmcli: conn_name=my-team1 ifname=my-team1 type=team ip4=192.168.100.100/24 gw4=192.168.100.1 state=present autoconnect=yes
    
    # Optionally, at the same time specify IPv6 addresses for the device as follows:
    - nmcli: conn_name=my-eth1 ifname=eth1 type=ethernet ip4=192.168.100.100/24 gw4=192.168.100.1 ip6=abbe::cafe gw6=2001:db8::1 state=present
    
    # To add two IPv4 DNS server addresses:
    -nmcli: conn_name=my-eth1 dns4=["8.8.8.8", "8.8.4.4"] state=present
    
    # To make a profile usable for all compatible Ethernet interfaces, issue a command as follows
    - nmcli: ctype=ethernet name=my-eth1 ifname="*" state=present
    
    # To change the property of a setting e.g. MTU, issue a command as follows:
    - nmcli: conn_name=my-eth1 mtu=9000 type=ethernet state=present
    
        Exit Status's:
            - nmcli exits with status 0 if it succeeds, a value greater than 0 is
            returned if an error occurs.
            - 0 Success - indicates the operation succeeded
            - 1 Unknown or unspecified error
            - 2 Invalid user input, wrong nmcli invocation
            - 3 Timeout expired (see --wait option)
            - 4 Connection activation failed
            - 5 Connection deactivation failed
            - 6 Disconnecting device failed
            - 7 Connection deletion failed
            - 8 NetworkManager is not running
            - 9 nmcli and NetworkManager versions mismatch
            - 10 Connection, device, or access point does not exist.




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

