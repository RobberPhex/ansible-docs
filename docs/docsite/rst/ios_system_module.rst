.. _ios_system:


ios_system - Manage the system attributes on Cisco IOS devices
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module provides declarative management of node system attributes on Cisco IOS devices.  It provides an option to configure host system parameters or remove those parameters from the device active configuration.




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
                <tr><td>domain_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Configure the IP domain name on the remote device to the provided value. Value should be in the dotted name form and will be appended to the <code>hostname</code> to create a fully-qualified domain name.</div>        </td></tr>
                <tr><td>domain_search<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Provides the list of domain suffixes to append to the hostname for the purpose of doing name resolution. This argument accepts a list of names and will be reconciled with the current active configuration on the running node.</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Configure the device hostname parameter. This option takes an ASCII string value.</div>        </td></tr>
                <tr><td>lookup_enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Administrative control for enabling or disabling DNS lookups.  When this argument is set to True, lookups are performed and when it is set to False, lookups are not performed.</div>        </td></tr>
                <tr><td>lookup_source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Provides one or more source interfaces to use for performing DNS lookups.  The interface provided in <code>lookup_source</code> must be a valid interface configured on the device.</div>        </td></tr>
                <tr><td>name_servers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of DNS name servers by IP address to use to perform name resolution lookups.  This argument accepts either a list of DNS servers See examples.</div>        </td></tr>
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
                <td><div>Configures the username to use to authenticate the connection to the remote device.  This value is used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_USERNAME</code> will be used instead.</div>        </td></tr>
                    <tr><td>authorize<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td><ul><li>yes</li><li>no</li></ul></td>
                <td><div>Instructs the module to enter privileged mode on the remote device before sending any commands.  If not specified, the device will attempt to execute all commands in non-privileged mode. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_AUTHORIZE</code> will be used instead.</div>        </td></tr>
                    <tr><td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.   This value is the path to the key used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div>        </td></tr>
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
                    <tr><td>password<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td></td>
                <td></td>
                <td><div>Specifies the password to use to authenticate the connection to the remote device.   This value is used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_PASSWORD</code> will be used instead.</div>        </td></tr>
                    <tr><td>port<br/><div style="font-size: small;"></div></td>
        <td>no</td>
        <td>22</td>
                <td></td>
                <td><div>Specifies the port to use when building the connection to the remote device.</div>        </td></tr>
        </table>
    </td>
    </tr>
        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the configuration values in the device's current active configuration.  When set to <em>present</em>, the values should be configured in the device active configuration and when set to <em>absent</em> the values should not be in the device active configuration</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: configure hostname and domain name
      ios_system:
        hostname: ios01
        domain_name: test.example.com
        domain-search:
          - ansible.com
          - redhat.com
          - cisco.com
    
    - name: remove configuration
      ios_system:
        state: absent
    
    - name: configure DNS lookup sources
      ios_system:
        lookup_source: MgmtEth0/0/CPU0/0
        lookup_enabled: yes
    
    - name: configure name servers
      ios_system:
        name_servers:
          - 8.8.8.8
          - 8.8.4.4

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
        <td align=center> ['hostname ios01', 'ip domain name test.example.com'] </td>
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
