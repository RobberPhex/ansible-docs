.. _ops_facts:


ops_facts - Collect device specific facts from OpenSwitch
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Collects facts from devices running the OpenSwitch operating system.  Fact collection is supported over both Cli and Rest transports.  This module prepends all of the base network fact keys with ``ansible_net_<fact>``.  The facts module will always collect a base set of facts from the device and can enable or disable collection of additional facts.
The facts collected from pre Ansible 2.2 are still available and are collected for backwards compatibility; however, these facts should be considered deprecated and will be removed in a future release.




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
    <td>config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>When enabled, this argument will collect the current running configuration from the remote device.  If the <code>transport=rest</code> then the collected configuration will be the full system configuration.</div></td></tr>
            <tr>
    <td>endpoints<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Accepts a list of endpoints to retrieve from the remote device using the REST API.  The endpoints should be valid endpoints available on the device.  This argument is only valid when the <code>transport=rest</code>.</div></td></tr>
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
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.  Note this argument does not affect the SSH argument.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the password to use to authenticate the connection to the remote device.  This is a common argument used for either <em>cli</em> or <em>rest</em> transports.  Note this argument does not affect the SSH transport. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_PASSWORD</code> will be used instead.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>0 (use common port)</td>
        <td><ul></ul></td>
        <td><div>Specifies the port to use when building the connection to the remote device.  This value applies to either <em>cli</em> or <em>rest</em>.  The port value will default to the appropriate transport common port if none is provided in the task.  (cli=22, http=80, https=443).  Note this argument does not affect the SSH transport.</div></td></tr>
            <tr>
    <td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Convenience method that allows all <em>openswitch</em> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div></td></tr>
            <tr>
    <td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.  This argument is only used for the <em>cli</em> transports. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_SSH_KEYFILE</code> will be used instead.</div></td></tr>
            <tr>
    <td>transport<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>ssh</td>
        <td><ul><li>ssh</li><li>cli</li><li>rest</li></ul></td>
        <td><div>Configures the transport connection to use when connecting to the remote device.  The transport argument supports connectivity to the device over ssh, cli or REST.</div></td></tr>
            <tr>
    <td>use_ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Configures the <em>transport</em> to use SSL if set to true only when the <em>transport</em> argument is configured as rest.  If the transport argument is not <em>rest</em>, this value is ignored.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Configures the username to use to authenticate the connection to the remote device.  The value of <em>username</em> is used to authenticate either the CLI login or the eAPI authentication depending on which transport is used. Note this argument does not affect the SSH transport. If the value is not specified in the task, the value of environment variable <code>ANSIBLE_NET_USERNAME</code> will be used instead.</div></td></tr>
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
        username: netop
        password: netop
        transport: cli
      rest:
        host: "{{ inventory_hostname }}"
        username: netop
        password: netop
        transport: rest
    
    - ops_facts:
        gather_subset: all
        provider: "{{ rest }}"
    
    # Collect only the config and default facts
    - ops_facts:
        gather_subset: config
        provider: "{{ cli }}"
    
    # Do not collect config facts
    - ops_facts:
        gather_subset:
          - "!config"
        provider: "{{ cli }}"
    
    - name: collect device facts
      ops_facts:
        provider: "{{ cli }}"
    
    - name: include the config
      ops_facts:
        config: yes
        provider: "{{ rest }}"
    
    - name: include a set of rest endpoints
      ops_facts:
        endpoints:
          - /system/interfaces/1
          - /system/interfaces/2
        provider: "{{ rest }}"

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
        <td align=center> when transport is cli </td>
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
        <td align=center> when config is enabled </td>
        <td align=center> str </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_serialnum </td>
        <td> The serial number of the remote device </td>
        <td align=center> when transport is cli </td>
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
        <td> ansible_net_version </td>
        <td> The operating system version running on the remote device </td>
        <td align=center> always </td>
        <td align=center> str </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> version </td>
        <td> The current version of OpenSwitch </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 0.3.0 </td>
    </tr>
            <tr>
        <td> endpoints </td>
        <td> The JSON response from the URL endpoint </td>
        <td align=center> when endpoints argument is defined and transport is rest </td>
        <td align=center> list </td>
        <td align=center> [{'....': None}, {'....': None}] </td>
    </tr>
            <tr>
        <td> config </td>
        <td> The current system configuration </td>
        <td align=center> when enabled </td>
        <td align=center> string </td>
        <td align=center> .... </td>
    </tr>
            <tr>
        <td> hostname </td>
        <td> returns the configured hostname </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> ops01 </td>
    </tr>
            <tr>
        <td> ansible_net_image </td>
        <td> The image file the device is running </td>
        <td align=center> when transport is cli </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

