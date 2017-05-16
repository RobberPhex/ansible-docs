.. _openvswitch_bridge:


openvswitch_bridge - Manage Open vSwitch bridges
++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage Open vSwitch bridges


Requirements (on host that executes module)
-------------------------------------------

  * ovs-vsctl


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
                <tr><td>bridge<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of bridge or fake bridge to manage</div>        </td></tr>
                <tr><td>external_ids<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A dictionary of external-ids. Omitting this parameter is a No-op. To  clear all external-ids pass an empty value.</div>        </td></tr>
                <tr><td>fail_mode<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>secure</li><li>standalone</li></ul></td>
        <td><div>Set bridge fail-mode. The default value (None) is a No-op.</div>        </td></tr>
                <tr><td>parent<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Bridge parent of the fake bridge to manage</div>        </td></tr>
                <tr><td>set<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Set a single property on a bridge.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the bridge should exist</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5</td>
        <td></td>
        <td><div>How long to wait for ovs-vswitchd to respond</div>        </td></tr>
                <tr><td>vlan<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The VLAN id of the fake bridge to manage (must be between 0 and 4095)</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a bridge named br-int
    - openvswitch_bridge:
        bridge: br-int
        state: present
    
    # Create a fake bridge named br-int within br-parent on the VLAN 405
    - openvswitch_bridge:
        bridge: br-int
        parent: br-parent
        vlan: 405
        state: present
    
    # Create an integration bridge
    - openvswitch_bridge:
        bridge: br-int
        state: present
        fail_mode: secure
      args:
        external_ids:
          bridge-id: br-int





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
