.. _pn_vrouterbgp:


pn_vrouterbgp - CLI command to add/remove/modify vrouter-bgp.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Execute vrouter-bgp-add, vrouter-bgp-remove, vrouter-bgp-modify command.
* Each fabric, cluster, standalone switch, or virtual network (VNET) can provide its tenants with a vRouter service that forwards traffic between networks and implements Layer 4 protocols.




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
                <tr><td>pn_bfd<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify if you want BFD protocol support for fault detection.</div>        </td></tr>
                <tr><td>pn_clipassword<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Provide login password if user is not root.</div>        </td></tr>
                <tr><td>pn_cliswitch<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Target switch(es) to run the cli on.</div>        </td></tr>
                <tr><td>pn_cliusername<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Provide login username if user is not root.</div>        </td></tr>
                <tr><td>pn_default_originate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify if you want announce default routes to the neighbor or not.</div>        </td></tr>
                <tr><td>pn_ebgp<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a value for external BGP to accept or attempt BGP connections to external peers, not directly connected, on the network. This is a value between 1 and 255.</div>        </td></tr>
                <tr><td>pn_holdtime<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify BGP neighbor holdtime in seconds.</div>        </td></tr>
                <tr><td>pn_keepalive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify BGP neighbor keepalive interval in seconds.</div>        </td></tr>
                <tr><td>pn_max_prefix<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify the maximum number of prefixes.</div>        </td></tr>
                <tr><td>pn_max_prefix_warn<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify if you want a warning message when the maximum number of prefixes is exceeded.</div>        </td></tr>
                <tr><td>pn_multiprotocol<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>ipv4-unicast</li><li>ipv6-unicast</li></ul></td>
        <td><div>Specify a multi-protocol for BGP.</div>        </td></tr>
                <tr><td>pn_neighbor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a neighbor IP address to use for BGP.</div><div>Required for vrouter-bgp-add.</div>        </td></tr>
                <tr><td>pn_next_hop_self<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify if the next-hop is the same router or not.</div>        </td></tr>
                <tr><td>pn_override_capability<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify if you want to override capability.</div>        </td></tr>
                <tr><td>pn_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a password, if desired.</div>        </td></tr>
                <tr><td>pn_prefix_listin<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify the prefix list to filter traffic inbound.</div>        </td></tr>
                <tr><td>pn_prefix_listout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify the prefix list to filter traffic outbound.</div>        </td></tr>
                <tr><td>pn_remote_as<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify the remote Autonomous System(AS) number. This value is between 1 and 4294967295.</div><div>Required for vrouter-bgp-add.</div>        </td></tr>
                <tr><td>pn_route_mapin<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify inbound route map for neighbor.</div>        </td></tr>
                <tr><td>pn_route_mapout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify outbound route map for neighbor.</div>        </td></tr>
                <tr><td>pn_route_reflector<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify if a route reflector client is used.</div>        </td></tr>
                <tr><td>pn_soft_reconfig<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify if you want a soft reconfiguration of inbound traffic.</div>        </td></tr>
                <tr><td>pn_vrouter_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specify a name for the vRouter service.</div>        </td></tr>
                <tr><td>pn_weight<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a default weight value between 0 and 65535 for the neighbor routes.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>update</li></ul></td>
        <td><div>State the action to perform. Use 'present' to add bgp, 'absent' to remove bgp and 'update' to modify bgp.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: add vrouter-bgp
      pn_vrouterbgp:
        state: 'present'
        pn_vrouter_name: 'ansible-vrouter'
        pn_neighbor: 104.104.104.1
        pn_remote_as: 1800
    
    - name: remove vrouter-bgp
      pn_vrouterbgp:
        state: 'absent'
        pn_name: 'ansible-vrouter'

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
        <td align=center> always </td>
        <td align=center> str </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stderr </td>
        <td> The set of error responses from the vrouterbgp command. </td>
        <td align=center> on error </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> The set of responses from the vrouterbpg command. </td>
        <td align=center> always </td>
        <td align=center> list </td>
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
