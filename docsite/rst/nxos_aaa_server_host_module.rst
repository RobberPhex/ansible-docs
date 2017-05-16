.. _nxos_aaa_server_host:


nxos_aaa_server_host - Manages AAA server host-specific configuration.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages AAA server host-specific configuration.




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
    <td>acct_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Alternate UDP port for RADIUS accounting.</div></td></tr>
            <tr>
    <td>address<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Address or name of the radius or tacacs host.</div></td></tr>
            <tr>
    <td>auth_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Alternate UDP port for RADIUS authentication.</div></td></tr>
            <tr>
    <td>encrypt_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>0</li><li>7</li></ul></td>
        <td><div>The state of encryption applied to the entered key. O for clear text, 7 for encrypted. Type-6 encryption is not supported.</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div></td></tr>
            <tr>
    <td>host_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Timeout period for specified host, in seconds. Range is 1-60.</div></td></tr>
            <tr>
    <td>key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Shared secret for the specified host.</div></td></tr>
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
    <td>server_type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>radius</li><li>tacacs</li></ul></td>
        <td><div>The server type is either radius or tacacs.</div></td></tr>
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
        <td><div>Manage the state of the resource.</div></td></tr>
            <tr>
    <td>tacacs_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Alternate TCP port TACACS Server.</div></td></tr>
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

    # Radius Server Host Basic settings
      - name: "Radius Server Host Basic settings"
        nxos_aaa_server_host:
            state: present
            server_type: radius
            address: 1.2.3.4
            acct_port: 2084
            host_timeout: 10
            host: {{ inventory_hostname }}
            username: {{ un }}
            password: {{ pwd }}
    
    # Radius Server Host Key Configuration
      - name: "Radius Server Host Key Configuration"
        nxos_aaa_server_host:
            state: present
            server_type: radius
            address: 1.2.3.4
            key: hello
            encrypt_type: 7
            host:  inventory_hostname }}
            username: {{ un }}
            password: {{ pwd }}
    
    # TACACS Server Host Configuration
      - name: "Tacacs Server Host Configuration"
        nxos_aaa_server_host:
            state: present
            server_type: tacacs 
            tacacs_port: 89
            host_timeout: 10
            address: 5.6.7.8
            host:  inventory_hostname }}
            username:  un }}
            password:  pwd }}

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
        <td> k/v pairs of configuration after module execution </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'host_timeout': '10', 'address': '1.2.3.4', 'auth_port': '2084', 'server_type': 'radius'} </td>
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
        <td> command sent to the device </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['radius-server host 1.2.3.4 auth-port 2084 timeout 10'] </td>
    </tr>
            <tr>
        <td> proposed </td>
        <td> k/v pairs of parameters passed into module </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'host_timeout': '10', 'address': '1.2.3.4', 'auth_port': '2084', 'server_type': 'radius'} </td>
    </tr>
            <tr>
        <td> existing </td>
        <td> ['k/v pairs of existing configuration'] </td>
        <td align=center>  </td>
        <td align=center> dict </td>
        <td align=center> {} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Changes to the AAA server host key (shared secret) are not idempotent.
.. note:: If ``state=absent`` removes the whole host configuration.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

