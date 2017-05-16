.. _nxos_interface_ospf:


nxos_interface_ospf - Manages configuration of an OSPF interface instance.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages configuration of an OSPF interface instance.




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
    <td>area<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Ospf area associated with this cisco_interface_ospf instance. Valid values are a string, formatted as an IP address (i.e. "0.0.0.0") or as an integer.</div></td></tr>
            <tr>
    <td>cost<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The cost associated with this cisco_interface_ospf instance.</div></td></tr>
            <tr>
    <td>dead_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Time interval an ospf neighbor waits for a hello packet before tearing down adjacencies. Valid values are an integer or the keyword 'default'.</div></td></tr>
            <tr>
    <td>hello_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Time between sending successive hello packets. Valid values are an integer or the keyword 'default'.</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div></td></tr>
            <tr>
    <td>interface<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of this cisco_interface resource. Valid value is a string.</div></td></tr>
            <tr>
    <td>message_digest<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Enables or disables the usage of message digest authentication. Valid values are 'true' and 'false'.</div></td></tr>
            <tr>
    <td>message_digest_algorithm_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>md5</li></ul></td>
        <td><div>Algorithm used for authentication among neighboring routers within an area. Valid values is 'md5'.</div></td></tr>
            <tr>
    <td>message_digest_encryption_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>cisco_type_7</li><li>3des</li></ul></td>
        <td><div>Specifies the scheme used for encrypting message_digest_password. Valid values are '3des' or 'cisco_type_7' encryption.</div></td></tr>
            <tr>
    <td>message_digest_key_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Md5 authentication key-id associated with the ospf instance. If this is present, message_digest_encryption_type, message_digest_algorithm_type and message_digest_password are mandatory. Valid value is an integer and 'default'.</div></td></tr>
            <tr>
    <td>message_digest_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the message_digest password. Valid value is a string.</div></td></tr>
            <tr>
    <td>ospf<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the ospf instance.</div></td></tr>
            <tr>
    <td>passive_interface<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>Setting to true will prevent this interface from receiving HELLO packets. Valid values are 'true' and 'false'.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the password to use to authenticate the connection to the remote device.  This is a common argument used for either <em>cli</em> or <em>nxapi</em> transports. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_PASSWORD</code> will be used instead.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0 (use common port)</td>
        <td><ul></ul></td>
        <td><div>Specifies the port to use when building the connection to the remote device.  This value applies to either <em>cli</em> or <em>nxapi</em>.  The port value will default to the appropriate transport common port if none is provided in the task.  (cli=22, http=80, https=443).</div></td></tr>
            <tr>
    <td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Convenience method that allows all <em>nxos</em> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div></td></tr>
            <tr>
    <td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.  This argument is only used for the <em>cli</em> transport. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Determines whether the config should be present or not on the device.</div></td></tr>
            <tr>
    <td>transport<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>cli</td>
        <td><ul></ul></td>
        <td><div>Configures the transport connection to use when connecting to the remote device.  The transport argument supports connectivity to the device over cli (ssh) or nxapi.</div></td></tr>
            <tr>
    <td>use_ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Configures the <em>transport</em> to use SSL if set to true only when the <code>transport=nxapi</code>, otherwise this value is ignored.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Configures the username to use to authenticate the connection to the remote device.  The value of <em>username</em> is used to authenticate either the CLI login or the nxapi authentication depending on which transport is used. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_USERNAME</code> will be used instead.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - nxos_interface_ospf:
        interface: ethernet1/32
        ospf: 1
        area: 1
        cost=default
        username: "{{ un }}"
        password: "{{ pwd }}"
        host: "{{ inventory_hostname }}"

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
        <td> k/v pairs of OSPF configuration after module execution </td>
        <td align=center> verbose mode </td>
        <td align=center> dict </td>
        <td align=center> {'hello_interval': '', 'area': '0.0.0.1', 'message_digest_algorithm_type': '', 'message_digest_key_id': '', 'message_digest_encryption_type': '', 'dead_interval': '', 'cost': '', 'passive_interface': False, 'message_digest_password': '', 'interface': 'ethernet1/32', 'ospf': '1', 'message_digest': False} </td>
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
        <td align=center> ['interface Ethernet1/32', 'ip router ospf 1 area 0.0.0.1'] </td>
    </tr>
            <tr>
        <td> proposed </td>
        <td> k/v pairs of parameters passed into module </td>
        <td align=center> verbose mode </td>
        <td align=center> dict </td>
        <td align=center> {'interface': 'ethernet1/32', 'ospf': '1', 'area': '1'} </td>
    </tr>
            <tr>
        <td> existing </td>
        <td> k/v pairs of existing OSPF configuration </td>
        <td align=center> verbose mode </td>
        <td align=center> dict </td>
        <td align=center> {'hello_interval': '', 'area': '', 'message_digest_algorithm_type': '', 'message_digest_key_id': '', 'message_digest_encryption_type': '', 'dead_interval': '', 'cost': '', 'passive_interface': False, 'message_digest_password': '', 'interface': 'ethernet1/32', 'ospf': '', 'message_digest': False} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Default, where supported, restores params default value.
.. note:: To remove an existing authentication configuration you should use ``message_digest_key_id=default`` plus all other options matching their existing values.
.. note:: ``state=absent`` removes the whole OSPF interface configuration.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

