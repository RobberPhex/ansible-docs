.. _nxos_aaa_server:


nxos_aaa_server - Manages AAA server global configuration.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages AAA server global configuration




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
                <tr><td>deadtime<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Duration for which a non-reachable AAA server is skipped, in minutes. Range is 1-1440. Device default is 0.</div>        </td></tr>
                <tr><td>directed_request<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enabled</li><li>disabled</li></ul></td>
        <td><div>Enables direct authentication requests to AAA server. Device default is disabled.</div>        </td></tr>
                <tr><td>encrypt_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>0</li><li>7</li></ul></td>
        <td><div>The state of encryption applied to the entered global key. O clear text, 7 encrypted. Type-6 encryption is not supported.</div>        </td></tr>
                <tr><td>global_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Global AAA shared secret.</div>        </td></tr>
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
                <tr><td>server_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Global AAA server timeout period, in seconds. Range is 1-60. Device default is 5.</div>        </td></tr>
                <tr><td>server_type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>radius</li><li>tacacs</li></ul></td>
        <td><div>The server type is either radius or tacacs.</div>        </td></tr>
                <tr><td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.  This argument is only used for the <em>cli</em> transport. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>present</td>
        <td><ul><li>present</li><li>default</li></ul></td>
        <td><div>Manage the state of the resource.</div>        </td></tr>
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
        </table>
    </br>



Examples
--------

 ::

    # Radius Server Basic settings
      - name: "Radius Server Basic settings"
        nxos_aaa_server:
            server_type: radius
            server_timeout: 9
            deadtime: 20
            directed_request: enabled
            host:  inventory_hostname }}
            username:  un }}
            password:  pwd }}
    
    # Tacacs Server Basic settings
      - name: "Tacacs Server Basic settings"
        nxos_aaa_server:
            server_type: tacacs
            server_timeout: 8
            deadtime: 19
            directed_request: disabled
            host:  inventory_hostname }}
            username:  un }}
            password:  pwd }}
    
    # Setting Global Key
      - name: "AAA Server Global Key"
        nxos_aaa_server:
            server_type: radius
            global_key: test_key
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
        <td> state </td>
        <td> state as sent in from the playbook </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> present </td>
    </tr>
            <tr>
        <td> updates </td>
        <td> command sent to the device </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['radius-server deadtime 22', 'radius-server timeout 11', 'radius-server directed-request'] </td>
    </tr>
            <tr>
        <td> proposed </td>
        <td> k/v pairs of parameters passed into module </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'server_timeout': '11', 'deadtime': '22', 'directed_request': 'enabled', 'server_type': 'radius'} </td>
    </tr>
            <tr>
        <td> end_state </td>
        <td> k/v pairs of aaa params after module execution </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'server_timeout': '11', 'deadtime': '22', 'directed_request': 'enabled', 'global_key': 'unknown'} </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> check to see if a change was made on the device </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> existing </td>
        <td> ['k/v pairs of existing aaa server'] </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'server_timeout': '5', 'deadtime': '0', 'directed_request': 'disabled', 'global_key': 'unknown'} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - The server_type parameter is always required.
    - If encrypt_type is not supplied, the global AAA server key will be stored as encrypted (type 7).
    - Changes to the global AAA server key with encrypt_type=0 are not idempotent.
    - If global AAA server key is not found, it's shown as "unknown"
    - state=default will set the supplied parameters to their default values. The parameters that you want to default must also be set to default. If global_key=default, the global key will be removed.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
