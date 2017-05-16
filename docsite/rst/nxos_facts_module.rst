.. _nxos_facts:


nxos_facts - Gets facts about NX-OS switches
++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Collects facts from Cisco Nexus devices running the NX-OS operating system.  Fact collection is supported over both Cli and Nxapi transports.  This module prepends all of the base network fact keys with ``ansible_net_<fact>``.  The facts module will always collect a base set of facts from the device and can enable or disable collection of additional facts.




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
    <td>gather_subset<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>!config</td>
        <td><ul></ul></td>
        <td><div>When supplied, this argument will restrict the facts collected to a given subset.  Possible values for this argument include all, hardware, config, legacy, and interfaces.  Can specify a list of values to include a larger subset.  Values can also be used with an initial <code><span class='module'>!</span></code> to specify that a specific subset should not be collected.</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div></td></tr>
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

    # Note: examples below use the following provider dict to handle
    #       transport and authentication to the node.
    vars:
      cli:
        host: "{{ inventory_hostname }}"
        username: admin
        password: admin
        transport: cli
    
    - nxos_facts:
        gather_subset: all
    
    # Collect only the config and default facts
    - nxos_facts:
        gather_subset:
          - config
    
    # Do not collect hardware facts
    - nxos_facts:
        gather_subset:
          - "!hardware"

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
        <td> fan_info </td>
        <td> A hash of facts about fans in the remote device </td>
        <td align=center> when legacy is configured </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> kickstart </td>
        <td> The software version used to boot the system </td>
        <td align=center> when legacy is configured </td>
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
        <td> ansible_net_hostname </td>
        <td> The configured hostname of the device </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_model </td>
        <td> The model name returned from the device </td>
        <td align=center> always </td>
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
        <td> module </td>
        <td> A hash of facts about the modules in a remote device </td>
        <td align=center> when legacy is configured </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> vlan_list </td>
        <td> The list of VLAN IDs configured on the remote device </td>
        <td align=center> when legacy is configured </td>
        <td align=center> list </td>
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
        <td> ansible_net_memtotal_mb </td>
        <td> The total memory on the remote device in Mb </td>
        <td align=center> when hardware is configured </td>
        <td align=center> int </td>
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
        <td> platform </td>
        <td> The hardware platform reported by the remote device </td>
        <td align=center> when legacy is configured </td>
        <td align=center> str </td>
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
        <td> interfaces_list </td>
        <td> The list of interface names on the remote device </td>
        <td align=center> when legacy is configured </td>
        <td align=center> dict </td>
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
        <td> power_supply_info </td>
        <td> A hash of facts about the power supplies in the remote device </td>
        <td align=center> when legacy is configured </td>
        <td align=center> str </td>
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
        <td> ansible_net_all_ipv6_addresses </td>
        <td> All IPv6 addresses configured on the device </td>
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
        <td> ansible_net_memfree_mb </td>
        <td> The available free memory on the remote device in Mb </td>
        <td align=center> when hardware is configured </td>
        <td align=center> int </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> hostname </td>
        <td> The configured hostname of the remote device </td>
        <td align=center> when legacy is configured </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

