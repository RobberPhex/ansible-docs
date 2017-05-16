.. _cnos_bgp:


cnos_bgp - Manage BGP resources and attributes on devices running Lenovo CNOS
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module allows you to work with Border Gateway Protocol (BGP) related configurations. The operators used are overloaded to ensure control over switch BGP configurations. This module is invoked using method with asNumber as one of its arguments. The first level of the BGP configuration allows to set up an AS number, with the following attributes going into various configuration operations under the context of BGP. After passing this level, there are eight BGP arguments that will perform further configurations. They are bgpArg1, bgpArg2, bgpArg3, bgpArg4, bgpArg5, bgpArg6, bgpArg7, and bgpArg8. For more details on how to use these arguments, see [Overloaded Variables]. This module uses SSH to manage network device configuration. The results of the operation will be placed in a directory named 'results' that must be created by the user in their local directory to where the playbook is run. For more information about this module from Lenovo and customizing it usage for your use cases, please visit http://systemx.lenovofiles.com/help/index.jsp?topic=%2Fcom.lenovo.switchmgt.ansible.doc%2Fcnos_bgp.html




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
                <tr><td>asNum<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>AS number</div>        </td></tr>
                <tr><td>bgpArg1<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>address-family</li><li>bestpath</li><li>bgp</li><li>cluster-id</li><li>confederation</li><li>enforce-first-as</li><li>fast-external-failover</li><li>graceful-restart</li><li>graceful-restart-helper</li><li>log-neighbor-changes</li><li>maxas-limit</li><li>neighbor</li><li>router-id</li><li>shutdown</li><li>synchronization</li><li>timers</li><li>vrf</li></ul></td>
        <td><div>This is an overloaded bgp first argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>bgpArg2<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>ipv4 or ipv6</li><li>always-compare-med</li><li>compare-confed-aspath</li><li>compare-routerid</li><li>dont-compare-originator-id</li><li>tie-break-on-age</li><li>as-path</li><li>med</li><li>identifier</li><li>peers</li></ul></td>
        <td><div>This is an overloaded bgp second argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>bgpArg3<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>aggregate-address</li><li>client-to-client</li><li>dampening</li><li>distance</li><li>maximum-paths</li><li>network</li><li>nexthop</li><li>redistribute</li><li>save</li><li>synchronization</li><li>ignore or multipath-relax</li><li>confed or missing-as-worst or non-deterministic or remove-recv-med or remove-send-med</li></ul></td>
        <td><div>This is an overloaded bgp third argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>bgpArg4<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>Aggregate prefix</li><li>Reachability Half-life time</li><li>route-map</li><li>Distance for routes external</li><li>ebgp or ibgp</li><li>IP prefix <network></li><li>IP prefix <network>/<length></li><li>synchronization</li><li>Delay value</li><li>direct</li><li>ospf</li><li>static</li><li>memory</li></ul></td>
        <td><div>This is an overloaded bgp fourth argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>bgpArg5<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>as-set</li><li>summary-only</li><li>Value to start reusing a route</li><li>Distance for routes internal</li><li>Supported multipath numbers</li><li>backdoor</li><li>map</li><li>route-map</li></ul></td>
        <td><div>This is an overloaded bgp fifth argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>bgpArg6<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>summary-only</li><li>as-set</li><li>route-map name</li><li>Value to start suppressing a route</li><li>Distance for local routes</li><li>Network mask</li><li>Pointer to route-map entries</li></ul></td>
        <td><div>This is an overloaded bgp sixth argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>bgpArg7<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>Maximum duration to suppress a stable route(minutes)</li><li>backdoor</li><li>route-map</li><li>Name of the route map</li></ul></td>
        <td><div>This is an overloaded bgp seventh argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
                <tr><td>bgpArg8<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>Un-reachability Half-life time for the penalty(minutes)</li><li>backdoor</li></ul></td>
        <td><div>This is an overloaded bgp eigth argument. Usage of this argument can be found is the User Guide referenced above.</div>        </td></tr>
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

    Tasks: The following are examples of using the module cnos_bgp. These are written in the main.yml file of the tasks directory.
    ---
    - name: Test BGP  - neighbor
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "neighbor"
          bgpArg2: "10.241.107.40"
          bgpArg3: 13
          bgpArg4: "address-family"
          bgpArg5: "ipv4"
          bgpArg6: "next-hop-self"
    
    - name: Test BGP  - BFD
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "neighbor"
          bgpArg2: "10.241.107.40"
          bgpArg3: 13
          bgpArg4: "bfd"
    
    - name: Test BGP  - address-family - dampening
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "address-family"
          bgpArg2: "ipv4"
          bgpArg3: "dampening"
          bgpArg4: 13
          bgpArg5: 233
          bgpArg6: 333
          bgpArg7: 15
          bgpArg8: 33
    
    - name: Test BGP  - address-family - network
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "address-family"
          bgpArg2: "ipv4"
          bgpArg3: "network"
          bgpArg4: "1.2.3.4/5"
          bgpArg5: "backdoor"
    
    - name: Test BGP - bestpath - always-compare-med
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "bestpath"
          bgpArg2: "always-compare-med"
    
    - name: Test BGP - bestpath-compare-confed-aspat
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "bestpath"
          bgpArg2: "compare-confed-aspath"
    
    - name: Test BGP - bgp
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "bgp"
          bgpArg2: 33
    
    - name: Test BGP  - cluster-id
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "cluster-id"
          bgpArg2: "1.2.3.4"
    
    - name: Test BGP - confederation-identifier
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "confederation"
          bgpArg2: "identifier"
          bgpArg3: 333
    
    - name: Test BGP - enforce-first-as
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "enforce-first-as"
    
    - name: Test BGP - fast-external-failover
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "fast-external-failover"
    
    - name: Test BGP  - graceful-restart
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "graceful-restart"
          bgpArg2: 333
    
    - name: Test BGP - graceful-restart-helper
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "graceful-restart-helper"
    
    - name: Test BGP - maxas-limit
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "maxas-limit"
          bgpArg2: 333
    
    - name: Test BGP  - neighbor
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "neighbor"
          bgpArg2: "10.241.107.40"
          bgpArg3: 13
          bgpArg4: "address-family"
          bgpArg5: "ipv4"
          bgpArg6: "next-hop-self"
    
    - name: Test BGP - router-id
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "router-id"
          bgpArg2: "1.2.3.4"
    
    - name: Test BGP - synchronization
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "synchronization"
    
    - name: Test BGP - timers
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "timers"
          bgpArg2: 333
          bgpArg3: 3333
    
    - name: Test BGP - vrf
      cnos_bgp:
          host: "{{ inventory_hostname }}"
          username: "{{ hostvars[inventory_hostname]['username'] }}"
          password: "{{ hostvars[inventory_hostname]['password'] }}"
          deviceType: "{{ hostvars[inventory_hostname]['deviceType'] }}"
          enablePassword: "{{ hostvars[inventory_hostname]['enablePassword'] }}"
          outputfile: "./results/test_bgp_{{ inventory_hostname }}_output.txt"
          asNum: 33
          bgpArg1: "vrf"
    

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
        <td> Success or failure message. Upon any failure, the method returns an error display string. </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center>  </td>
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
