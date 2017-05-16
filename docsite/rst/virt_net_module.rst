.. _virt_net:


virt_net - Manage libvirt network configuration
+++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage *libvirt* networks.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * python-libvirt
  * python-lxml


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
    <td>autostart<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Specify if a given storage pool should be started automatically on system boot.</div></td></tr>
            <tr>
    <td>command<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>define</li><li>create</li><li>start</li><li>stop</li><li>destroy</li><li>undefine</li><li>get_xml</li><li>list_nets</li><li>facts</li><li>info</li><li>status</li></ul></td>
        <td><div>in addition to state management, various non-idempotent commands are available. See examples.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the network being managed. Note that network must be previously defined with xml.</div></br>
        <div style="font-size: small;">aliases: network<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>active</li><li>inactive</li><li>present</li><li>absent</li></ul></td>
        <td><div>specify which state you want a network to be in. If 'active', network will be started. If 'present', ensure that network is present but do not change its state; if it's missing, you need to specify xml argument. If 'inactive', network will be stopped. If 'undefined' or 'absent', network will be removed from <em>libvirt</em> configuration.</div></td></tr>
            <tr>
    <td>uri<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>qemu:///system</td>
        <td><ul></ul></td>
        <td><div>libvirt connection uri.</div></td></tr>
            <tr>
    <td>xml<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>XML document used with the define command.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Define a new network
    - virt_net: command=define name=br_nat xml='{{ lookup("template", "network/bridge.xml.j2") }}'
    
    # Start a network
    - virt_net: command=create name=br_nat
    
    # List available networks
    - virt_net: command=list_nets
    
    # Get XML data of a specified network
    - virt_net: command=get_xml name=br_nat
    
    # Stop a network
    - virt_net: command=destroy name=br_nat
    
    # Undefine a network
    - virt_net: command=undefine name=br_nat
    
    # Gather facts about networks
    # Facts will be available as 'ansible_libvirt_networks'
    - virt_net: command=facts
    
    # Gather information about network managed by 'libvirt' remotely using uri
    - virt_net: command=info uri='{{ item }}'
      with_items: libvirt_uris
      register: networks
    
    # Ensure that a network is active (needs to be defined and built first)
    - virt_net: state=active name=br_nat
    
    # Ensure that a network is inactive
    - virt_net: state=inactive name=br_nat
    
    # Ensure that a given network will be started at boot
    - virt_net: autostart=yes name=br_nat
    
    # Disable autostart for a given network
    - virt_net: autostart=no name=br_nat




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

