.. _pn_trunk:


pn_trunk - CLI command to create/delete/modify a trunk.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Execute trunk-create or trunk-delete command.
Trunks can be used to aggregate network links at Layer 2 on the local switch. Use this command to create a new trunk.




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
    <td>pn_broadcast_level<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify a broadcast level in percent. The default value is 100%.</div></td></tr>
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
        <td><div>Target switch(es) to run the cli on.</div></td></tr>
            <tr>
    <td>pn_cliusername<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Provide login username if user is not root.</div></td></tr>
            <tr>
    <td>pn_description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify a description for the trunk configuration.</div></td></tr>
            <tr>
    <td>pn_edge_switch<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify if the switch is an edge switch.</div></td></tr>
            <tr>
    <td>pn_egress_rate_limit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify an egress port data rate limit for the configuration.</div></td></tr>
            <tr>
    <td>pn_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Host facing port control setting.</div></td></tr>
            <tr>
    <td>pn_jumbo<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify if the port can receive jumbo frames.</div></td></tr>
            <tr>
    <td>pn_lacp_fallback<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>bundle</li><li>individual</li></ul></td>
        <td><div>Specify the LACP fallback mode as bundles or individual.</div></td></tr>
            <tr>
    <td>pn_lacp_fallback_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the LACP fallback timeout in seconds. The range is between 30 and 60 seconds with a default value of 50 seconds.</div></td></tr>
            <tr>
    <td>pn_lacp_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>off</li><li>passive</li><li>active</li></ul></td>
        <td><div>Specify the LACP mode for the configuration.</div></td></tr>
            <tr>
    <td>pn_lacp_priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the LACP priority. This is a number between 1 and 65535 with a default value of 32768.</div></td></tr>
            <tr>
    <td>pn_lacp_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>slow</li><li>fast</li></ul></td>
        <td><div>Specify the LACP time out as slow (30 seconds) or fast (4seconds). The default value is slow.</div></td></tr>
            <tr>
    <td>pn_loopback<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify loopback if you want to use loopback.</div></td></tr>
            <tr>
    <td>pn_loopvlans<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify a list of looping vlans.</div></td></tr>
            <tr>
    <td>pn_mirror_receive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify if the configuration receives mirrored traffic.</div></td></tr>
            <tr>
    <td>pn_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the name for the trunk configuration.</div></td></tr>
            <tr>
    <td>pn_pause<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify if pause frames are sent.</div></td></tr>
            <tr>
    <td>pn_port_macaddr<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the MAC address of the port.</div></td></tr>
            <tr>
    <td>pn_ports<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the port number(s) for the link(s) to aggregate into the trunk.</div><div>Required for trunk-create.</div></td></tr>
            <tr>
    <td>pn_routing<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify if the port participates in routing on the network.</div></td></tr>
            <tr>
    <td>pn_speed<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>disable</li><li>10m</li><li>100m</li><li>1g</li><li>2.5g</li><li>10g</li><li>40g</li></ul></td>
        <td><div>Specify the port speed or disable the port.</div></td></tr>
            <tr>
    <td>pn_unkown_mcast_level<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify an unkown multicast level in percent. The default value is 100%.</div></td></tr>
            <tr>
    <td>pn_unkown_ucast_level<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify an unkown unicast level in percent. The default value is 100%.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>update</li></ul></td>
        <td><div>State the action to perform. Use 'present' to create trunk, 'absent' to delete trunk and 'update' to modify trunk.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: create trunk
      pn_trunk:
        state: 'present'
        pn_name: 'spine-to-leaf'
        pn_ports: '11,12,13,14'
    
    - name: delete trunk
      pn_trunk:
        state: 'absent'
        pn_name: 'spine-to-leaf'

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
        <td> changed </td>
        <td> Indicates whether the CLI caused changes on the target. </td>
        <td align=center> always </td>
        <td align=center> bool </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> command </td>
        <td> The CLI command run on the target node(s). </td>
        <td align=center>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stderr </td>
        <td> The set of error responses from the trunk command. </td>
        <td align=center> on error </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> The set of responses from the trunk command. </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

