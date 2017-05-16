.. _ios_vrf:


ios_vrf - Manage the collection of VRF definitions on Cisco IOS devices
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module provides declarative management of VRF definitions on Cisco IOS devices.  It allows playbooks to manage individual or the entire VRF collection.  It also supports purging VRF definitions from the configuration that are not explicitly defined.




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
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Provides a short description of the VRF definition in the current active configuration.  The VRF definition value accepts alphanumeric characters used to provide additional information about the VRF.</div>        </td></tr>
                <tr><td>interfaces<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Identifies the set of interfaces that should be configured in the VRF.  Interfaces must be routed interfaces in order to be placed into a VRF.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of the VRF definition to be managed on the remote IOS device.  The VRF definition name is an ASCII string name used to uniquely identify the VRF.  This argument is mutually exclusive with the <code>vrfs</code> argument</div>        </td></tr>
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
                <tr><td>purge<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Instructs the module to consider the VRF definition absolute.  It will remove any previously configured VRFs on the device.</div>        </td></tr>
                <tr><td>rd<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The router-distinguisher value uniquely identifies the VRF to routing processes on the remote IOS system.  The RD value takes the form of <code>A:B</code> where <code>A</code> and <code>B</code> are both numeric values.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Configures the state of the VRF definition as it relates to the device operational configuration.  When set to <em>present</em>, the VRF should be configured in the device active configuration and when set to <em>absent</em> the VRF should not be in the device active configuration</div>        </td></tr>
                <tr><td>vrfs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The set of VRF definition objects to be configured on the remote IOS device.  Ths list entries can either be the VRF name or a hash of VRF definitions and attributes.  This argument is mutually exclusive with the <code>name</code> argument.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: configure a vrf named management
      ios_vrf:
        name: management
        description: oob mgmt vrf
        interfaces:
          - Management1
    
    - name: remove a vrf named test
      ios_vrf:
        name: test
        state: absent
    
    - name: configure set of VRFs and purge any others
      ios_vrf:
        vrfs:
          - red
          - blue
          - green
        purge: yes

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
        <td> start </td>
        <td> The time the job started </td>
        <td align=center> always </td>
        <td align=center> str </td>
        <td align=center> 2016-11-16 10:38:15.126146 </td>
    </tr>
            <tr>
        <td> commands </td>
        <td> The list of configuration mode commands to send to the device </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['vrf definition ansible', 'description management vrf', {'rd': '1:100'}] </td>
    </tr>
            <tr>
        <td> end </td>
        <td> The time the job ended </td>
        <td align=center> always </td>
        <td align=center> str </td>
        <td align=center> 2016-11-16 10:38:25.595612 </td>
    </tr>
            <tr>
        <td> delta </td>
        <td> The time elapsed to perform all operations </td>
        <td align=center> always </td>
        <td align=center> str </td>
        <td align=center> 0:00:10.469466 </td>
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
