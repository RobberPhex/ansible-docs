.. _pn_vrouterif:


pn_vrouterif - CLI command to add/remove/modify vrouter-interface.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Execute vrouter-interface-add, vrouter-interface-remove, vrouter-interface-modify command.
You configure interfaces to vRouter services on a fabric, cluster, standalone switch or virtual network(VNET).




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
    <td>pn_alias<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify an alias for the interface.</div></td></tr>
            <tr>
    <td>pn_assignment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>none</li><li>dhcp</li><li>dhcpv6</li><li>autov6</li></ul></td>
        <td><div>Specify the DHCP method for IP address assignment.</div></td></tr>
            <tr>
    <td>pn_clipassword<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Provide login password if user is not root.</div></td></tr>
            <tr>
    <td>pn_cliswitch<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Target switch to run the cli on.</div></td></tr>
            <tr>
    <td>pn_cliusername<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Provide login username if user is not root.</div></td></tr>
            <tr>
    <td>pn_exclusive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify if the interface is exclusive to the configuration. Exclusive means that other configurations cannot use the interface. Exclusive is specified when you configure the interface as span interface and allows higher throughput through the interface.</div></td></tr>
            <tr>
    <td>pn_interface<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>mgmt</li><li>data</li><li>span</li></ul></td>
        <td><div>Specify if the interface is management, data or span interface.</div></td></tr>
            <tr>
    <td>pn_interface_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the IP address of the interface in x.x.x.x/n format.</div></td></tr>
            <tr>
    <td>pn_l3port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify a Layer 3 port for the interface.</div></td></tr>
            <tr>
    <td>pn_nic_enable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify if the NIC is enabled or not</div></td></tr>
            <tr>
    <td>pn_nic_str<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the type of NIC. Used for vrouter-interface remove/modify.</div></td></tr>
            <tr>
    <td>pn_secondary_macs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify a secondary MAC address for the interface.</div></td></tr>
            <tr>
    <td>pn_vlan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the VLAN identifier. This is a value between 1 and 4092.</div></td></tr>
            <tr>
    <td>pn_vrouter_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the name of the vRouter interface.</div></td></tr>
            <tr>
    <td>pn_vrrp_adv_int<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify a VRRP advertisement interval in milliseconds. The range is from 30 to 40950 with a default value of 1000.</div></td></tr>
            <tr>
    <td>pn_vrrp_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the ID for the VRRP interface. The IDs on both vRouters must be the same IS number.</div></td></tr>
            <tr>
    <td>pn_vrrp_priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the priority for the VRRP interface. This is a value between 1 (lowest) and 255 (highest).</div></td></tr>
            <tr>
    <td>pn_vxlan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the VXLAN identifier. This is a value between 1 and 16777215.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>update</li></ul></td>
        <td><div>State the action to perform. Use 'present' to add vrouter interface, 'absent' to remove vrouter interface and 'update' to modify vrouter interface.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Add vrouter-interface
      pn_vrouterif:
        pn_cliusername: admin
        pn_clipassword: admin
        state: 'present'
        pn_vrouter_name: 'ansible-vrouter'
        pn_interface_ip: 101.101.101.2/24
        pn_vlan: 101
    
    - name: Add VRRP..
      pn_vrouterif:
        pn_cliusername: admin
        pn_clipassword: admin
        state: 'present'
        pn_vrouter_name: 'ansible-vrouter'
        pn_interface_ip: 101.101.101.2/24
        pn_vrrp_ip: 101.101.101.1/24
        pn_vrrp_priority: 100
        pn_vlan: 101
    
    - name: Remove vrouter-interface
      pn_vrouterif:
        pn_cliusername: admin
        pn_clipassword: admin
        state: 'absent'
        pn_vrouter_name: 'ansible-vrouter'
        pn_interface_ip: 101.101.101.2/24

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
        <td> vrouterifcmd </td>
        <td> The CLI command run on the target node(s). </td>
        <td align=center>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> Indicates whether the CLI caused changes on the target. </td>
        <td align=center> always </td>
        <td align=center> bool </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stderr/msg </td>
        <td> The set of error responses from the vrouterif command. </td>
        <td align=center> on error </td>
        <td align=center> str </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stdout/msg </td>
        <td> The set of responses from the vrouterif command. </td>
        <td align=center> on success </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

