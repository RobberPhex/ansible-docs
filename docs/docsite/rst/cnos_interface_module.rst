.. _cnos_interface:


cnos_interface - Manage interface configuration on devices running Lenovo CNOS
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module allows you to work with interface related configurations. The operators used are overloaded to ensure control over switch interface configurations. Apart from the regular device connection related attributes, there are seven interface arguments that will perform further configurations. They are interfaceArg1, interfaceArg2, interfaceArg3, interfaceArg4, interfaceArg5, interfaceArg6, and interfaceArg7. For more details on how to use these arguments, see [Overloaded Variables]. Interface configurations are taken care at six contexts in a regular CLI. They are 1. Interface Name - Configurations 2. Ethernet Interface - Configurations 3. Loopback Interface Configurations 4. Management Interface Configurations 5. Port Aggregation - Configurations 6. VLAN Configurations This module uses SSH to manage network device configuration. The results of the operation will be placed in a directory named 'results' that must be created by the user in their local directory to where the playbook is run. For more information about this module from Lenovo and customizing it usage for your use cases, please visit http://systemx.lenovofiles.com/help/index.jsp?topic=%2Fcom.lenovo.switchmgt.ansible.doc%2Fcnos_interface.html




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
                <tr><td>deviceType<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>g8272_cnos</li><li>g8296_cnos</li><li>g8332_cnos</li></ul></td>
        <td><div>This specifies the type of device where the method is executed.</div>        </td></tr>
                <tr><td>enablePassword<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Configures the password used to enter Global Configuration command mode on the switch. If the switch does not request this password, the parameter is ignored.While generally the value should come from the inventory file, you can also specify it as a variable. This parameter is optional. If it is not specified, no default value will be used.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>This is the variable used to search the hosts file at /etc/ansible/hosts and identify the IP address of the device on which the template is going to be applied. Usually the Ansible keyword {{ inventory_hostname }} is specified in the playbook as an abstraction of the group of network elements that need to be configured.</div>        </td></tr>
                <tr><td>interfaceArg1<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>aggregation-group</li><li>bfd</li><li>bridgeport</li><li>description</li><li>duplex</li><li>flowcontrol</li><li>ip</li><li>ipv6</li><li>lacp</li><li>lldp</li><li>load-interval</li><li>mac</li><li>mac-address</li><li>mac-learn</li><li>microburst-detection</li><li>mtu</li><li>service</li><li>service-policy</li><li>shutdown</li><li>snmp</li><li>spanning-tree</li><li>speed</li><li>storm-control</li><li>vlan</li><li>vrrp</li><li>port-aggregation</li></ul></td>
        <td><div>This is an overloaded interface first argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>interfaceArg2<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>aggregation-group number</li><li>access or mode or trunk</li><li>description</li><li>auto or full or half</li><li>recieve or send</li><li>port-priority</li><li>suspend-individual</li><li>timeout</li><li>receive or transmit or trap-notification</li><li>tlv-select</li><li>Load interval delay in seconds</li><li>counter</li><li>Name for the MAC Access List</li><li>mac-address in HHHH.HHHH.HHHH format</li><li>THRESHOLD  Value in unit of buffer cell</li><li><64-9216>  MTU in bytes-<64-9216> for L2 packet</li><li><576-9216> for L3 IPv4 packet</li><li><1280-9216> for L3 IPv6 packet</li><li>enter the instance id</li><li>input or output</li><li>copp-system-policy</li><li>type</li><li>1000  or  10000  or   40000 or   auto</li><li>broadcast or multicast or unicast</li><li>disable or enable or egress-only</li><li>Virtual router identifier</li><li>destination-ip or destination-mac or destination-port or source-dest-ip or source-dest-mac or source-dest-port or source-interface or source-ip or source-mac or source-port</li></ul></td>
        <td><div>This is an overloaded interface second argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>interfaceArg3<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>active or on or passive</li><li>on or off</li><li>LACP port priority</li><li>long or short</li><li>link-aggregation or mac-phy-status or management-address or max-frame-size or port-description or port-protocol-vlan or port-vlan or power-mdi or protocol-identity or system-capabilities or system-description or system-name or vid-management or vlan-name</li><li>counter for load interval</li><li>policy input name</li><li>all or Copp class name to attach</li><li>qos</li><li>queing</li><li>Enter the allowed traffic level</li><li>ipv6</li></ul></td>
        <td><div>This is an overloaded interface third argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>interfaceArg4<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>key-chain</li><li>key-id</li><li>keyed-md5 or keyed-sha1 or meticulous-keyed-md5 or meticulous-keyed-sha1 or simple</li><li>Interval value in milliseconds</li><li>Destination IP (Both IPV4 and IPV6)</li><li>in or out</li><li>MAC address</li><li>Time-out value in seconds</li><li>class-id</li><li>request</li><li>Specify the IPv4 address</li><li>OSPF area ID as a decimal value</li><li>OSPF area ID in IP address format</li><li>anycast or secondary</li><li>ethernet</li><li>vlan</li><li>MAC (hardware) address in HHHH.HHHH.HHHH format</li><li>Load interval delay in seconds</li><li>Specify policy input name</li><li>input or output</li><li>cost</li><li>port-priority</li><li>BFD minimum receive interval</li><li>source-interface</li></ul></td>
        <td><div>This is an overloaded interface fourth argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>interfaceArg5<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>name of key-chain</li><li>key-Id Value</li><li>key-chain</li><li>key-id</li><li>BFD minimum receive interval</li><li>Value of Hello Multiplier</li><li>admin-down or multihop or non-persistent</li><li>Vendor class-identifier name</li><li>bootfile-name or host-name or log-server or ntp-server or tftp-server-name</li><li>Slot/chassis number</li><li>Vlan interface</li><li>Specify policy input name</li><li>Port path cost or auto</li><li>Port priority increments of 32</li></ul></td>
        <td><div>This is an overloaded interface fifth argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>interfaceArg6<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>Authentication key string</li><li>name of key-chain</li><li>key-Id Value</li><li>Value of Hello Multiplier</li><li>admin-down or non-persistent</li></ul></td>
        <td><div>This is an overloaded interface sixth argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>interfaceArg7<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>Authentication key string</li><li>admin-down</li></ul></td>
        <td><div>This is an overloaded interface seventh argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>interfaceOption<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>None</li><li>ethernet</li><li>loopback</li><li>mgmt</li><li>port-aggregation</li><li>vlan</li></ul></td>
        <td><div>This specifies the attribute you specify subsequent to interface command</div>        </td></tr>
                <tr><td>interfaceRange<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>This specifies the interface range in which the port aggregation is envisaged</div>        </td></tr>
                <tr><td>outputfile<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>This specifies the file path where the output of each command execution is saved. Each command that is specified in the merged template file and each response from the device are saved here. Usually the location is the results folder, but you can choose another location based on your write permission.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Configures the password used to authenticate the connection to the remote device. The value of the password parameter is used to authenticate the SSH session. While generally the value should come from the inventory file, you can also specify it as a variable. This parameter is optional. If it is not specified, no default value will be used.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Configures the username used to authenticate the connection to the remote device. The value of the username parameter is used to authenticate the SSH session. While generally the value should come from the inventory file, you can also specify it as a variable. This parameter is optional. If it is not specified, no default value will be used.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    Tasks : The following are examples of using the module cnos_interface. These are written in the main.yml file of the tasks directory.
    ---
    - name: Test Interface Ethernet - aggregation-group
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 1
          interfaceArg1: "aggregation-group"
          interfaceArg2: 33
          interfaceArg3: "on"
    
    - name: Test Interface Ethernet - bridge-port
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "bridge-port"
          interfaceArg2: "access"
          interfaceArg3: 33
    
    - name: Test Interface Ethernet - bridgeport mode
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "bridge-port"
          interfaceArg2: "mode"
          interfaceArg3: "access"
    
    - name: Test Interface Ethernet  - Description
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "description"
          interfaceArg2: "Hentammoo "
    
    - name: Test Interface Ethernet - Duplex
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 1
          interfaceArg1: "duplex"
          interfaceArg2: "auto"
    
    - name: Test Interface Ethernet - flowcontrol
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "flowcontrol"
          interfaceArg2: "send"
          interfaceArg3: "off"
    
    - name: Test Interface Ethernet - lacp
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "lacp"
          interfaceArg2: "port-priority"
          interfaceArg3: 33
    
    - name: Test Interface Ethernet  - lldp
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "lldp"
          interfaceArg2: "tlv-select"
          interfaceArg3: "max-frame-size"
    
    - name: Test Interface Ethernet - load-interval
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "load-interval"
          interfaceArg2: "counter"
          interfaceArg3: 2
          interfaceArg4: 33
    
    - name: Test Interface Ethernet - mac
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "mac"
          interfaceArg2: "copp-system-acl-vlag-hc"
    
    - name: Test Interface Ethernet - microburst-detection
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "microburst-detection"
          interfaceArg2: 25
    
    - name: Test Interface Ethernet  - mtu
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "mtu"
          interfaceArg2: 66
    
    - name: Test Interface Ethernet - service-policy
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "service-policy"
          interfaceArg2: "input"
          interfaceArg3: "Anil"
    
    - name: Test Interface Ethernet - speed
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 1
          interfaceArg1: "speed"
          interfaceArg2: "auto"
    
    - name: Test Interface Ethernet - storm
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "storm-control"
          interfaceArg2: "broadcast"
          interfaceArg3: 12.5
    
    - name: Test Interface Ethernet - vlan
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "vlan"
          interfaceArg2: "disable"
    
    - name: Test Interface Ethernet - vrrp
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "vrrp"
          interfaceArg2: 33
    
    - name: Test Interface Ethernet - spanning tree1
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "spanning-tree"
          interfaceArg2: "bpduguard"
          interfaceArg3: "enable"
    
    - name: Test Interface Ethernet - spanning tree 2
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "spanning-tree"
          interfaceArg2: "mst"
          interfaceArg3: "33-35"
          interfaceArg4: "cost"
          interfaceArg5: 33
    
    - name: Test Interface Ethernet - ip1
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "ip"
          interfaceArg2: "access-group"
          interfaceArg3: "anil"
          interfaceArg4: "in"
    
    - name: Test Interface Ethernet - ip2
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "ip"
          interfaceArg2: "port"
          interfaceArg3: "anil"
    
    - name: Test Interface Ethernet - bfd
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "bfd"
          interfaceArg2: "interval"
          interfaceArg3: 55
          interfaceArg4: 55
          interfaceArg5: 33
    
    - name: Test Interface Ethernet - bfd
      cnos_interface:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_interface_{{ inventory_hostname }}_output.txt"
          interfaceOption: 'ethernet'
          interfaceRange: 33
          interfaceArg1: "bfd"
          interfaceArg2: "ipv4"
          interfaceArg3: "authentication"
          interfaceArg4: "meticulous-keyed-md5"
          interfaceArg5: "key-chain"
          interfaceArg6: "mychain"
    

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
        <td> Success or failure message </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> Interface configurations accomplished. </td>
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
