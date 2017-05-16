.. _dellos10_facts:


dellos10_facts - Collect facts from remote devices running Dell OS10
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Collects a base set of device facts from a remote device that is running Dell OS10.  This module prepends all of the base network fact keys with ``ansible_net_<fact>``.  The facts module will always collect a base set of facts from the device and can enable or disable collection of additional facts.




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
    <td>gather_subset<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>!config</td>
        <td><ul></ul></td>
        <td><div>When supplied, this argument will restrict the facts collected to a given subset.  Possible values for this argument include all, hardware, config, and interfaces.  Can specify a list of values to include a larger subset.  Values can also be used with an initial <code><span class='module'>!</span></code> to specify that a specific subset should not be collected.</div></td></tr>
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
        <td><div>This value <em>password</em> is used to authenticate the SSH session to the remote device. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_PASSWORD will be used instead.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>22</td>
        <td><ul></ul></td>
        <td><div>Specifies the port to use when building the connection to the remote device.</div></td></tr>
            <tr>
    <td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Convenience method that allows all <span class='module'>dellos10</span> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div></td></tr>
            <tr>
    <td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>This value <em>ssh_keyfile</em> is the path to the key used to authenticate the SSH session to the remote device.  If the value is not specified in the task, the value of environment variable ANSIBLE_NET_SSH_KEYFILE will be used instead.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>Specifies idle timeout (in seconds) for the connection. Useful if the console freezes before continuing. For example when saving configurations.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>This value <em>username</em> is used to authenticate the SSH session to the remote device. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_USERNAME will be used instead.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Collect all facts from the device
    - dellos10_facts:
        gather_subset: all
    
    # Collect only the config and default facts
    - dellos10_facts:
        gather_subset:
          - config
    
    # Do not collect hardware facts
    - dellos10_facts:
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
        <td> ansible_net_model </td>
        <td> The model name returned from the device </td>
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
        <td> ansible_net_config </td>
        <td> The current active config from the device </td>
        <td align=center> when config is configured </td>
        <td align=center> str </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_hostname </td>
        <td> The configured hostname of the device </td>
        <td align=center> always </td>
        <td align=center> str </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_cpu_arch </td>
        <td> Cpu Architecture of the remote device </td>
        <td align=center> when hardware is configured </td>
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
        <td> ansible_net_version </td>
        <td> The operating system version running on the remote device </td>
        <td align=center> always </td>
        <td align=center> str </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_servicetag </td>
        <td> The service tag number of the remote device </td>
        <td align=center> always </td>
        <td align=center> str </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_name </td>
        <td> The name of the OS which is running </td>
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



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

