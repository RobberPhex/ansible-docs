.. _eos_eapi:


eos_eapi - Manage and configure Arista EOS eAPI.
++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Use to enable or disable eAPI access, and set the port and state of http, https, local_http and unix-socket servers.
* When enabling eAPI access the default is to enable HTTP on port 80, enable HTTPS on port 443, disable local HTTP, and disable Unix socket server. Use the options listed below to override the default configuration.
* Requires EOS v4.12 or greater.


Requirements (on host that executes module)
-------------------------------------------

  * EOS v4.12 or greater


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
                <tr><td>auth_pass<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td></td>
        <td><div>Specifies the password to use if required to enter privileged mode on the remote device.  If <em>authorize</em> is false, then this argument does nothing. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_AUTH_PASS</code> will be used instead.</div>        </td></tr>
                <tr><td>authorize<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Instructs the module to enter privileged mode on the remote device before sending any commands.  If not specified, the device will attempt to execute all commands in non-privileged mode. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_AUTHORIZE</code> will be used instead.</div>        </td></tr>
                <tr><td>config<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>nul</td>
        <td></td>
        <td><div>The module, by default, will connect to the remote device and retrieve the current running-config to use as a base for comparing against the contents of source.  There are times when it is not desirable to have the task get the current running-config for every task in a playbook.  The <em>config</em> argument allows the implementer to pass in the configuration to use as the base config for comparison.</div>        </td></tr>
                <tr><td>http<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>The <code>http</code> argument controls the operating state of the HTTP transport protocol when eAPI is present in the running-config. When the value is set to True, the HTTP protocol is enabled and when the value is set to False, the HTTP protocol is disabled. By default, when eAPI is first configured, the HTTP protocol is disabled.</div></br>
    <div style="font-size: small;">aliases: enable_http<div>        </td></tr>
                <tr><td>http_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>80</td>
        <td></td>
        <td><div>Configures the HTTP port that will listen for connections when the HTTP transport protocol is enabled.  This argument accepts integer values in the valid range of 1 to 65535.</div>        </td></tr>
                <tr><td>https<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>The <code>https</code> argument controls the operating state of the HTTPS transport protocol when eAPI is present in the running-config. When the value is set to True, the HTTPS protocol is enabled and when the value is set to False, the HTTPS protocol is disabled. By default, when eAPI is first configured, the HTTPS protocol is enabled.</div></br>
    <div style="font-size: small;">aliases: enable_http<div>        </td></tr>
                <tr><td>https_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>443</td>
        <td></td>
        <td><div>Configures the HTTP port that will listen for connections when the HTTP transport protocol is enabled.  This argument accepts integer values in the valid range of 1 to 65535.</div>        </td></tr>
                <tr><td>local_http<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>The <code>local_http</code> argument controls the operating state of the local HTTP transport protocol when eAPI is present in the running-config.  When the value is set to True, the HTTP protocol is enabled and restricted to connections from localhost only.  When the value is set to False, the HTTP local protocol is disabled.</div><div>Note is value is independent of the <code>http</code> argument</div></br>
    <div style="font-size: small;">aliases: enable_local_http<div>        </td></tr>
                <tr><td>local_http_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>8080</td>
        <td></td>
        <td><div>Configures the HTTP port that will listen for connections when the HTTP transport protocol is enabled.  This argument accepts integer values in the valid range of 1 to 65535.</div>        </td></tr>
                <tr><td rowspan="2">provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td><td></td>
    <td> <div>A dict object containing connection details.</div>    </tr>
    <tr>
    <td colspan="5">
    <table border=1 cellpadding=4>
    <caption><b>Dictionary object provider</b></caption>
    <tr>
    <th class="head">parameter</th>
    <th class="head">required</th>
    <th class="head">default</th>
    <th class="head">choices</th>
    <th class="head">comments</th>
    </tr>
                    <tr><td>username<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Configures the username to use to authenticate the connection to the remote device.  This value is used to authenticate either the CLI login or the eAPI authentication depending on which transport is used. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_USERNAME</code> will be used instead.</div>        </td></tr>
                    <tr><td>authorize<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td><ul><li>yes</li><li>no</li></ul></td>
                <td><div>Instructs the module to enter privileged mode on the remote device before sending any commands.  If not specified, the device will attempt to execute all commands in non-privileged mode. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_AUTHORIZE</code> will be used instead.</div>        </td></tr>
                    <tr><td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Specifies the SSH keyfile to use to authenticate the connection to the remote device.  This argument is only used for <em>cli</em> transports. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div>        </td></tr>
                    <tr><td>auth_pass<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>none</td>
                <td></td>
                <td><div>Specifies the password to use if required to enter privileged mode on the remote device.  If <em>authorize</em> is false, then this argument does nothing. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_AUTH_PASS</code> will be used instead.</div>        </td></tr>
                    <tr><td>host<br/><div style="font-size: small;"></div></td>
        <td>yes</td>
        <td></td>
                <td></td>
                <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div>        </td></tr>
                    <tr><td>timeout<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>10</td>
                <td></td>
                <td><div>Specifies the timeout in seconds for communicating with the network device for either connecting or sending commands.  If the timeout is exceeded before the operation is completed, the module will error.</div>        </td></tr>
                    <tr><td>use_ssl<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>True</td>
                <td><ul><li>yes</li><li>no</li></ul></td>
                <td><div>Configures the <em>transport</em> to use SSL if set to true only when the <code>transport=eapi</code>.  If the transport argument is not eapi, this value is ignored.</div>        </td></tr>
                    <tr><td>password<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Specifies the password to use to authenticate the connection to the remote device.  This is a common argument used for either <em>cli</em> or <em>eapi</em> transports. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_PASSWORD</code> will be used instead.</div>        </td></tr>
                    <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td><ul><li>yes</li><li>no</li></ul></td>
                <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.  If the transport argument is not eapi, this value is ignored.</div>        </td></tr>
                    <tr><td>port<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>0 (use common port)</td>
                <td></td>
                <td><div>Specifies the port to use when building the connection to the remote device.  This value applies to either <em>cli</em> or <em>eapi</em>.  The port value will default to the appropriate transport common port if none is provided in the task.  (cli=22, http=80, https=443).</div>        </td></tr>
                    <tr><td>transport<br/><div style="font-size: small;"></div></td>
        <td>yes</td>
        <td>cli</td>
                <td><ul><li>eapi</li><li>cli</li></ul></td>
                <td><div>Configures the transport connection to use when connecting to the remote device.</div>        </td></tr>
        </table>
    </td>
    </tr>
        </td></tr>
                <tr><td>socket<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>The <code>socket</code> argument controls the operating state of the UNIX Domain Socket used to receive eAPI requests.  When the value of this argument is set to True, the UDS will listen for eAPI requests.  When the value is set to False, the UDS will not be available to handle requests.  By default when eAPI is first configured, the UDS is disabled.</div></br>
    <div style="font-size: small;">aliases: enable_socket<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>started</td>
        <td><ul><li>started</li><li>stopped</li></ul></td>
        <td><div>The <code>state</code> argument controls the operational state of eAPI on the remote device.  When this argument is set to <code>started</code>, eAPI is enabled to receive requests and when this argument is <code>stopped</code>, eAPI is disabled and will not receive requests.</div>        </td></tr>
                <tr><td>vrf<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>default</td>
        <td></td>
        <td><div>The <code>vrf</code> argument will configure eAPI to listen for connections in the specified VRF.  By default, eAPI transports will listen for connections in the global table.  This value requires the VRF to already be created otherwise the task will fail.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Enable eAPI access with default configuration
      eos_eapi:
        state: started
    
    - name: Enable eAPI with no HTTP, HTTPS at port 9443, local HTTP at port 80, and socket enabled
      eos_eapi:
        state: started
        http: false
        https_port: 9443
        local_http: yes
        local_http_port: 80
        socket: yes
    
    - name: Shutdown eAPI access
      eos_eapi:
        state: stopped

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
        <td> commands </td>
        <td> The list of configuration mode commands to send to the device </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['management api http-commands', 'protocol http port 81', 'no protocol https'] </td>
    </tr>
            <tr>
        <td> session_name </td>
        <td> The EOS config session name used to load the configuration </td>
        <td align=center> when changed is True </td>
        <td align=center> str </td>
        <td align=center> ansible_1479315771 </td>
    </tr>
            <tr>
        <td> urls </td>
        <td> Hash of URL endpoints eAPI is listening on per interface </td>
        <td align=center> when eAPI is started </td>
        <td align=center> dict </td>
        <td align=center> {'Management1': ['http://172.26.10.1:80']} </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
