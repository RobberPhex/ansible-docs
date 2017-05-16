.. _ios_facts:


ios_facts - Collect facts from remote devices running Cisco IOS
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Collects a base set of device facts from a remote device that is running IOS.  This module prepends all of the base network fact keys with ``ansible_net_<fact>``.  The facts module will always collect a base set of facts from the device and can enable or disable collection of additional facts.




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
                <tr><td>gather_subset<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>!config</td>
        <td></td>
        <td><div>When supplied, this argument will restrict the facts collected to a given subset.  Possible values for this argument include all, hardware, config, and interfaces.  Can specify a list of values to include a larger subset.  Values can also be used with an initial <code><span class='module'>!</span></code> to specify that a specific subset should not be collected.</div>        </td></tr>
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
        </table>
    </br>



Examples
--------

 ::

    # Note: examples below use the following provider dict to handle
    #       transport and authentication to the node.
    ---
    vars:
      cli:
        host: "{{ inventory_hostname }}"
        username: cisco
        password: cisco
        transport: cli
    
    ---
    # Collect all facts from the device
    - ios_facts:
        gather_subset: all
        provider: "{{ cli }}"
    
    # Collect only the config and default facts
    - ios_facts:
        gather_subset:
          - config
        provider: "{{ cli }}"
    
    # Do not collect hardware facts
    - ios_facts:
        gather_subset:
          - "!hardware"
        provider: "{{ cli }}"

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
        <td> ansible_net_model </td>
        <td> The model name returned from the device </td>
        <td align=center> always </td>
        <td align=center> str </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_hostname </td>
        <td> The configured hostname of the device </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_config </td>
        <td> The current active config from the device </td>
        <td align=center> when config is configured </td>
        <td align=center> str </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_serialnum </td>
        <td> The serial number of the remote device </td>
        <td align=center> always </td>
        <td align=center> str </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_gather_subset </td>
        <td> The list of fact subsets collected from the device </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_interfaces </td>
        <td> A hash of all interfaces running on the system </td>
        <td align=center> when interfaces is configured </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_version </td>
        <td> The operating system version running on the remote device </td>
        <td align=center> always </td>
        <td align=center> str </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_all_ipv4_addresses </td>
        <td> All IPv4 addresses configured on the device </td>
        <td align=center> when interfaces is configured </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_neighbors </td>
        <td> The list of LLDP neighbors from the remote device </td>
        <td align=center> when interfaces is configured </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_filesystems </td>
        <td> All file system names available on the device </td>
        <td align=center> when hardware is configured </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_image </td>
        <td> The image file the device is running </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_memfree_mb </td>
        <td> The available free memory on the remote device in Mb </td>
        <td align=center> when hardware is configured </td>
        <td align=center> int </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_all_ipv6_addresses </td>
        <td> All IPv6 addresses configured on the device </td>
        <td align=center> when interfaces is configured </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_memtotal_mb </td>
        <td> The total memory on the remote device in Mb </td>
        <td align=center> when hardware is configured </td>
        <td align=center> int </td>
        <td align=center>  </td>
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
