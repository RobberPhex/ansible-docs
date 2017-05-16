.. _flowadm:


flowadm - Manage bandwidth resource control and priority for protocols, services and zones.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create/modify/remove networking bandwidth and associated resources for a type of traffic on a particular link.




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
    <td>dsfield<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>- Identifies the 8-bit differentiated services field (as defined in RFC 2474). The optional dsfield_mask is used to state the bits of interest in the differentiated services field when comparing with the dsfield value. Both values must be in hexadecimal.
</div></td></tr>
            <tr>
    <td>link<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifiies a link to configure flow on.</div></td></tr>
            <tr>
    <td>local_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Identifies a network flow by the local IP address.</div></td></tr>
            <tr>
    <td>local_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Identifies a service specified by the local port.</div></td></tr>
            <tr>
    <td>maxbw<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>- Sets the full duplex bandwidth for the flow. The bandwidth is specified as an integer with one of the scale suffixes(K, M, or G for Kbps, Mbps, and Gbps). If no units are specified, the input value will be read as Mbps.
</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>- A flow is defined as a set of attributes based on Layer 3 and Layer 4 headers, which can be used to identify a protocol, service, or a zone.
</div></br>
        <div style="font-size: small;">aliases: flow<div></td></tr>
            <tr>
    <td>priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>medium</td>
        <td><ul><li>low</li><li>medium</li><li>high</li></ul></td>
        <td><div>Sets the relative priority for the flow.</div></td></tr>
            <tr>
    <td>remove_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Identifies a network flow by the remote IP address.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li><li>resetted</li></ul></td>
        <td><div>Create/delete/enable/disable an IP address on the network interface.</div></td></tr>
            <tr>
    <td>temporary<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Specifies that the configured flow is temporary. Temporary flows do not persist across reboots.</div></td></tr>
            <tr>
    <td>transport<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>- Specifies a Layer 4 protocol to be used. It is typically used in combination with <em>local_port</em> to identify the service that needs special attention.
</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Limit SSH traffic to 100M via vnic0 interface
    flowadm: link=vnic0 flow=ssh_out transport=tcp local_port=22 maxbw=100M state=present
    
    # Reset flow properties
    flowadm: name=dns state=resetted
    
    # Configure policy for EF PHB (DSCP value of 101110 from RFC 2598) with a bandwidth of 500 Mbps and a high priority.
    flowadm: link=bge0 dsfield=0x2e:0xfc maxbw=500M priority=high flow=efphb-flow state=present

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
        <td> dsfield </td>
        <td> flow's differentiated services value </td>
        <td align=center> if dsfield is defined </td>
        <td align=center> string </td>
        <td align=center> 0x2e:0xfc </td>
    </tr>
            <tr>
        <td> temporary </td>
        <td> flow's persistence </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> name </td>
        <td> flow name </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> http_drop </td>
    </tr>
            <tr>
        <td> maxbw </td>
        <td> flow's maximum bandwidth </td>
        <td align=center> if maxbw is defined </td>
        <td align=center> string </td>
        <td align=center> 100M </td>
    </tr>
            <tr>
        <td> local_Ip </td>
        <td> flow's local IP address </td>
        <td align=center> if local_ip is defined </td>
        <td align=center> string </td>
        <td align=center> 10.0.0.42 </td>
    </tr>
            <tr>
        <td> local_port </td>
        <td> flow's local port </td>
        <td align=center> if local_port is defined </td>
        <td align=center> int </td>
        <td align=center> 1337 </td>
    </tr>
            <tr>
        <td> priority </td>
        <td> flow's priority </td>
        <td align=center> if priority is defined </td>
        <td align=center> string </td>
        <td align=center> low </td>
    </tr>
            <tr>
        <td> state </td>
        <td> state of the target </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> present </td>
    </tr>
            <tr>
        <td> link </td>
        <td> flow's link </td>
        <td align=center> if link is defined </td>
        <td align=center> string </td>
        <td align=center> vnic0 </td>
    </tr>
            <tr>
        <td> transport </td>
        <td> flow's transport </td>
        <td align=center> if transport is defined </td>
        <td align=center> string </td>
        <td align=center> tcp </td>
    </tr>
            <tr>
        <td> remote_Ip </td>
        <td> flow's remote IP address </td>
        <td align=center> if remote_ip is defined </td>
        <td align=center> string </td>
        <td align=center> 10.0.0.42 </td>
    </tr>
        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

