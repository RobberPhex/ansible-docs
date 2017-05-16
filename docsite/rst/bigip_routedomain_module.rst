.. _bigip_routedomain:


bigip_routedomain - Manage route domains on a BIG-IP
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage route domains on a BIG-IP


Requirements (on host that executes module)
-------------------------------------------

  * f5-sdk


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
    <td>bwc_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The bandwidth controller for the route domain.</div></td></tr>
            <tr>
    <td>connection_limit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The maximum number of concurrent connections allowed for the route domain. Setting this to <code>0</code> turns off connection limits.</div></td></tr>
            <tr>
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies descriptive text that identifies the route domain.</div></td></tr>
            <tr>
    <td>flow_eviction_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The eviction policy to use with this route domain. Apply an eviction policy to provide customized responses to flow overflows and slow flows on the route domain.</div></td></tr>
            <tr>
    <td>id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The unique identifying integer representing the route domain.</div></td></tr>
            <tr>
    <td>parent<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the route domain the system searches when it cannot
find a route in the configured domain.
</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password for the user account used to connect to the BIG-IP.</div></td></tr>
            <tr>
    <td>routing_protocol<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>BFD</li><li>BGP</li><li>IS-IS</li><li>OSPFv2</li><li>OSPFv3</li><li>PIM</li><li>RIP</li><li>RIPng</li></ul></td>
        <td><div>Dynamic routing protocols for the system to use in the route domain.</div></td></tr>
            <tr>
    <td>server<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The BIG-IP host.</div></td></tr>
            <tr>
    <td>server_port<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>443</td>
        <td><ul></ul></td>
        <td><div>The BIG-IP server port.</div></td></tr>
            <tr>
    <td>service_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Service policy to associate with the route domain.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the route domain should exist or not.</div></td></tr>
            <tr>
    <td>strict<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enabled</li><li>disabled</li></ul></td>
        <td><div>Specifies whether the system enforces cross-routing restrictions or not.</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The username to connect to the BIG-IP with. This user must have administrative privileges on the device.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div></td></tr>
            <tr>
    <td>vlans<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>VLANs for the system to use in the route domain</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create a route domain
      bigip_routedomain:
          id: "1234"
          password: "secret"
          server: "lb.mydomain.com"
          state: "present"
          user: "admin"
      delegate_to: localhost
    
    - name: Set VLANs on the route domain
      bigip_routedomain:
          id: "1234"
          password: "secret"
          server: "lb.mydomain.com"
          state: "present"
          user: "admin"
          vlans:
              - net1
              - foo
      delegate_to: localhost

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
        <td> flow_eviction_policy </td>
        <td> The new eviction policy to use with this route domain </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> /Common/default-eviction-policy </td>
    </tr>
            <tr>
        <td> service_policy </td>
        <td> The new service policy to use with this route domain </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> /Common-my-service-policy </td>
    </tr>
            <tr>
        <td> description </td>
        <td> The description of the route domain </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> route domain foo </td>
    </tr>
            <tr>
        <td> parent </td>
        <td> The new parent route domain </td>
        <td align=center> changed </td>
        <td align=center> int </td>
        <td align=center> 0 </td>
    </tr>
            <tr>
        <td> connection_limit </td>
        <td> The new connection limit for the route domain </td>
        <td align=center> changed </td>
        <td align=center> integer </td>
        <td align=center> 100 </td>
    </tr>
            <tr>
        <td> strict </td>
        <td> The new strict isolation setting </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> enabled </td>
    </tr>
            <tr>
        <td> routing_protocol </td>
        <td> List of routing protocols applied to the route domain </td>
        <td align=center> changed </td>
        <td align=center> list </td>
        <td align=center> ['bfd', 'bgp'] </td>
    </tr>
            <tr>
        <td> bwc_policy </td>
        <td> The new bandwidth controller </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> /Common/foo </td>
    </tr>
            <tr>
        <td> vlans </td>
        <td> List of new VLANs the route domain is applied to </td>
        <td align=center> changed </td>
        <td align=center> list </td>
        <td align=center> ['/Common/http-tunnel', '/Common/socks-tunnel'] </td>
    </tr>
            <tr>
        <td> id </td>
        <td> The ID of the route domain that was changed </td>
        <td align=center> changed </td>
        <td align=center> int </td>
        <td align=center> 2 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Requires the f5-sdk Python package on the host. This is as easy as pip install f5-sdk.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

