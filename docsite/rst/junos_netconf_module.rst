.. _junos_netconf:


junos_netconf - Configures the Junos Netconf system service
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module provides an abstraction that enables and configures the netconf system service running on Junos devices.  This module can be used to easily enable the Netconf API. Netconf provides a programmatic interface for working with configuration and state resources as defined in RFC 6242.




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
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the DNS host name or address for connecting to the remote device over the specified transport.  The value of host is used as the destination address for the transport.</div></td></tr>
            <tr>
    <td>netconf_port<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>830</td>
        <td><ul></ul></td>
        <td><div>This argument specifies the port the netconf service should listen on for SSH connections.  The default port as defined in RFC 6242 is 830.</div></br>
        <div style="font-size: small;">aliases: listens_on<div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the password to use to authenticate the connection to the remote device.   The value of <em>password</em> is used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_PASSWORD will be used instead.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>22</td>
        <td><ul></ul></td>
        <td><div>Specifies the port to use when building the connection to the remote device.  The port value will default to the well known SSH port of 22 (for <code>transport=cli</code>) or port 830 (for <code>transport=netconf</code>) device.</div></td></tr>
            <tr>
    <td>provider<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Convenience method that allows all <em>ios</em> arguments to be passed as a dict object.  All constraints (required, choices, etc) must be met either by individual arguments or values in this dict.</div></td></tr>
            <tr>
    <td>ssh_keyfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the SSH key to use to authenticate the connection to the remote device.   The value of <em>ssh_keyfile</em> is the path to the key used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_SSH_KEYFILE will be used instead.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Specifies the state of the <span class='module'>junos_netconf</span> resource on the remote device.  If the <em>state</em> argument is set to <em>present</em> the netconf service will be configured.  If the <em>state</em> argument is set to <em>absent</em> the netconf service will be removed from the configuration.</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Configures the username to use to authenticate the connection to the remote device.  The value of <em>username</em> is used to authenticate the SSH session. If the value is not specified in the task, the value of environment variable ANSIBLE_NET_USERNAME will be used instead.</div></td></tr>
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
        username: ansible
        password: Ansible
        transport: cli
    
    - name: enable netconf service on port 830
      junos_netconf:
        listens_on: 830
        state: present
        provider: "{{ cli }}"
    
    - name: disable netconf service
      junos_netconf:
        state: absent
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
        <td> commands </td>
        <td> Returns the command sent to the remote device </td>
        <td align=center> when changed is True </td>
        <td align=center> str </td>
        <td align=center> set system services netconf ssh port 830 </td>
    </tr>
        
    </table>
    </br></br>



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

