.. _nxos_acl:


nxos_acl - Manages access list entries for ACLs.
++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages access list entries for ACLs.




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
                <tr><td>ack<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enable</li></ul></td>
        <td><div>Match on the ACK bit.</div>        </td></tr>
                <tr><td>action<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>permit</li><li>deny</li><li>remark</li></ul></td>
        <td><div>Action of the ACE.</div>        </td></tr>
                <tr><td>dest<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Destination ip and mask using IP/MASK notation and supports the keyword 'any'.</div>        </td></tr>
                <tr><td>dest_port1<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Port/protocol and also first (lower) port when using range operand.</div>        </td></tr>
                <tr><td>dest_port2<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Second (end) port when using range operand.</div>        </td></tr>
                <tr><td>dest_port_op<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>any</li><li>eq</li><li>gt</li><li>lt</li><li>neq</li><li>range</li></ul></td>
        <td><div>Destination port operands such as eq, neq, gt, lt, range.</div>        </td></tr>
                <tr><td>dscp<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>af11</li><li>af12</li><li>af13</li><li>af21</li><li>af22</li><li>af23</li><li>af31</li><li>af32</li><li>af33</li><li>af41</li><li>af42</li><li>af43</li><li>cs1</li><li>cs2</li><li>cs3</li><li>cs4</li><li>cs5</li><li>cs6</li><li>cs7</li><li>default</li><li>ef</li></ul></td>
        <td><div>Match packets with given dscp value.</div>        </td></tr>
                <tr><td>established<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enable</li></ul></td>
        <td><div>Match established connections.</div>        </td></tr>
                <tr><td>fin<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enable</li></ul></td>
        <td><div>Match on the FIN bit.</div>        </td></tr>
                <tr><td>fragments<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enable</li></ul></td>
        <td><div>Check non-initial fragments.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div>        </td></tr>
                <tr><td>log<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enable</li></ul></td>
        <td><div>Log matches against this entry.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Case sensitive name of the access list (ACL).</div>        </td></tr>
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
                <tr><td>precedence<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>critical</li><li>flash</li><li>flash-override</li><li>immediate</li><li>internet</li><li>network</li><li>priority</li><li>routine</li></ul></td>
        <td><div>Match packets with given precedence.</div>        </td></tr>
                <tr><td>proto<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Port number or protocol (as supported by the switch).</div>        </td></tr>
                <tr><td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Convenience method that allows all <em>nxos</em> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div>        </td></tr>
                <tr><td>psh<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enable</li></ul></td>
        <td><div>Match on the PSH bit.</div>        </td></tr>
                <tr><td>remark<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If action is set to remark, this is the description.</div>        </td></tr>
                <tr><td>rst<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enable</li></ul></td>
        <td><div>Match on the RST bit.</div>        </td></tr>
                <tr><td>seq<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sequence number of the entry (ACE).</div>        </td></tr>
                <tr><td>src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Source ip and mask using IP/MASK notation and supports keyword 'any'.</div>        </td></tr>
                <tr><td>src_port1<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Port/protocol and also first (lower) port when using range operand.</div>        </td></tr>
                <tr><td>src_port2<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Second (end) port when using range operand.</div>        </td></tr>
                <tr><td>src_port_op<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>any</li><li>eq</li><li>gt</li><li>lt</li><li>neq</li><li>range</li></ul></td>
        <td><div>Source port operands such as eq, neq, gt, lt, range.</div>        </td></tr>
                <tr><td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.  This argument is only used for the <em>cli</em> transport. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>delete_acl</li></ul></td>
        <td><div>Specify desired state of the resource.</div>        </td></tr>
                <tr><td>syn<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enable</li></ul></td>
        <td><div>Match on the SYN bit.</div>        </td></tr>
                <tr><td>time-range<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of time-range to apply.</div>        </td></tr>
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
                <tr><td>urg<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enable</li></ul></td>
        <td><div>Match on the URG bit.</div>        </td></tr>
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
        </table>
    </br>



Examples
--------

 ::

    
    # configure ACL ANSIBLE
    - nxos_acl:
        name: ANSIBLE
        seq: 10
        action: permit
        proto: tcp
        src: 1.1.1.1/24
        dest: any
        state: present
        provider: "{{ nxos_provider }}"

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
        <td> end_state </td>
        <td> k/v pairs of ACL entries after module execution. </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'src': '1.1.1.1/24', 'name': 'ANSIBLE', 'seq': '10', 'proto': 'tcp', 'dest': 'any', 'action': 'permit'} </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> check to see if a change was made on the device </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> updates </td>
        <td> commands sent to the device </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['ip access-list ANSIBLE', '10 permit tcp 1.1.1.1/24 any'] </td>
    </tr>
            <tr>
        <td> proposed </td>
        <td> k/v pairs of parameters passed into module. </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'src': '1.1.1.1/24', 'name': 'ANSIBLE', 'seq': '10', 'proto': 'tcp', 'dest': 'any', 'action': 'permit'} </td>
    </tr>
            <tr>
        <td> existing </td>
        <td> k/v pairs of existing ACL entries. </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - ``state=absent`` removes the ACE if it exists.
    - ``state=delete_acl`` deleted the ACL if it exists.
    - For idempotency, use port numbers for the src/dest port params like *src_port1* and names for the well defined protocols for the *proto* param.
    - Although this module is idempotent in that if the ace as presented in the task is identical to the one on the switch, no changes will be made. If there is any difference, what is in Ansible will be pushed (configured options will be overridden).  This is to improve security, but at the same time remember an ACE is removed, then re-added, so if there is a change, the new ACE will be exactly what parameters you are sending to the module.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
