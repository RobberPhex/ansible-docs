.. _nxos_ping:


nxos_ping - Tests reachability using ping from Nexus switch.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Tests reachability using ping from switch to a remote destination.




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
                <tr><td>count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>2</td>
        <td></td>
        <td><div>Number of packets to send.</div>        </td></tr>
                <tr><td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>IP address or hostname (resolvable by switch) of remote node.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the password to use to authenticate the connection to the remote device.  This is a common argument used for either <em>cli</em> or <em>nxapi</em> transports. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_PASSWORD</code> will be used instead.</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0 (use common port)</td>
        <td></td>
        <td><div>Specifies the port to use when building the connection to the remote device.  This value applies to either <em>cli</em> or <em>nxapi</em>.  The port value will default to the appropriate transport common port if none is provided in the task.  (cli=22, http=80, https=443).</div>        </td></tr>
                <tr><td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Convenience method that allows all <em>nxos</em> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div>        </td></tr>
                <tr><td>source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Source IP Address.</div>        </td></tr>
                <tr><td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.  This argument is only used for the <em>cli</em> transport. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>Specifies the timeout in seconds for communicating with the network device for either connecting or sending commands.  If the timeout is exceeded before the operation is completed, the module will error. NX-API can be slow to return on long-running commands (sh mac, sh bgp, etc).</div>        </td></tr>
                <tr><td>transport<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>cli</td>
        <td></td>
        <td><div>Configures the transport connection to use when connecting to the remote device.  The transport argument supports connectivity to the device over cli (ssh) or nxapi.</div>        </td></tr>
                <tr><td>use_ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Configures the <em>transport</em> to use SSL if set to true only when the <code>transport=nxapi</code>, otherwise this value is ignored.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Configures the username to use to authenticate the connection to the remote device.  This value is used to authenticate either the CLI login or the nxapi authentication depending on which transport is used. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_USERNAME</code> will be used instead.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.  If the transport argument is not nxapi, this value is ignored.</div>        </td></tr>
                <tr><td>vrf<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Outgoing VRF.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Test reachability to 8.8.8.8 using mgmt vrf
      nxos_ping:
        dest: 8.8.8.8
        vrf: management
        host: 68.170.147.165
    
    - name: Test reachability to a few different public IPs using mgmt vrf
      nxos_ping:
        dest: nxos_ping
        vrf: management
        host: 68.170.147.165
      with_items:
        - 8.8.8.8
        - 4.4.4.4
        - 198.6.1.4

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
        <td> count </td>
        <td> Show amount of packets sent </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 2 </td>
    </tr>
            <tr>
        <td> packet_loss </td>
        <td> Percentage of packets lost </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 0.00% </td>
    </tr>
            <tr>
        <td> dest </td>
        <td> Show the ping destination </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 8.8.8.8 </td>
    </tr>
            <tr>
        <td> packets_rx </td>
        <td> Packets successfully received </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 2 </td>
    </tr>
            <tr>
        <td> rtt </td>
        <td> Show RTT stats </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'max': '6.564', 'avg': '6.264', 'min': '5.978'} </td>
    </tr>
            <tr>
        <td> updates </td>
        <td> Show the command sent </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['ping 8.8.8.8 count 2 vrf management'] </td>
    </tr>
            <tr>
        <td> packets_tx </td>
        <td> Packets successfully transmitted </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 2 </td>
    </tr>
            <tr>
        <td> action </td>
        <td> ['Show what action has been performed'] </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> PING 8.8.8.8 (8.8.8.8): 56 data bytes </td>
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
