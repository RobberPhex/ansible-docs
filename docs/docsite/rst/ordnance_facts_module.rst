.. _ordnance_facts:


ordnance_facts - Collect facts from Ordnance Virtual Routers over SSH
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Collects a base set of device facts from an Ordnance Virtual router over SSH. This module prepends all of the base network fact keys with ``ansible_net_<fact>``.  The facts module will always collect a base set of facts from the device and can enable or disable collection of additional facts.




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
                <tr><td>gather_subset<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>!config</td>
        <td></td>
        <td><div>When supplied, this argument will restrict the facts collected to a given subset.  Possible values for this argument include all, hardware, config, and interfaces.  Can specify a list of values to include a larger subset.  Values can also be used with an initial <code><span class='module'>!</span></code> to specify that a specific subset should not be collected.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    ---
    # Note: examples below use the following provider dict to handle
    #       transport and authentication to the node.
    vars:
      cli:
        host: "{{ inventory_hostname }}"
        username: RouterName
        password: ordnance
        transport: cli
    
    ---
    # Collect all facts from the device
    - ordnance_facts:
        gather_subset: all
        provider: "{{ cli }}"
    
    # Collect only the config and default facts
    - ordnance_facts:
        gather_subset:
          - config
        provider: "{{ cli }}"
    
    # Do not collect hardware facts
    - ordnance_facts:
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
        <td> ansible_net_all_ipv4_addresses </td>
        <td> All IPv4 addresses configured on the virtual router </td>
        <td align=center> when interfaces is configured </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_config </td>
        <td> The current active config from the virtual router </td>
        <td align=center> when config is configured </td>
        <td align=center> str </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_all_ipv6_addresses </td>
        <td> All IPv6 addresses configured on the virtual router </td>
        <td align=center> when interfaces is configured </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_gather_subset </td>
        <td> The list of fact subsets collected from the virtual router </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ansible_net_interfaces </td>
        <td> A hash of all interfaces running on the virtual router </td>
        <td align=center> when interfaces is configured </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
