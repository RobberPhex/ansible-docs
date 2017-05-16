.. _quantum_subnet:


quantum_subnet - Add/remove subnet from a network
+++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

Add/remove subnet from a network

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
    <td>allocation_pool_end</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>From the subnet pool the last IP that should be assigned to the virtual machines</td>
    </tr>
            <tr>
    <td>allocation_pool_start</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>From the subnet pool the starting address from which the IP should be allocated</td>
    </tr>
            <tr>
    <td>auth_url</td>
    <td>no</td>
    <td>http://127.0.0.1:35357/v2.0/</td>
        <td><ul></ul></td>
        <td>The keystone URL for authentication</td>
    </tr>
            <tr>
    <td>cidr</td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The CIDR representation of the subnet that should be assigned to the subnet</td>
    </tr>
            <tr>
    <td>dns_nameservers</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>DNS nameservers for this subnet, comma-separated (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>enable_dhcp</td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>Whether DHCP should be enabled for this subnet.</td>
    </tr>
            <tr>
    <td>gateway_ip</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The ip that would be assigned to the gateway for this subnet</td>
    </tr>
            <tr>
    <td>ip_version</td>
    <td>no</td>
    <td>4</td>
        <td><ul></ul></td>
        <td>The IP version of the subnet 4 or 6</td>
    </tr>
            <tr>
    <td>login_password</td>
    <td>yes</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>Password of login user</td>
    </tr>
            <tr>
    <td>login_tenant_name</td>
    <td>yes</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>The tenant name of the login user</td>
    </tr>
            <tr>
    <td>login_username</td>
    <td>yes</td>
    <td>admin</td>
        <td><ul></ul></td>
        <td>login username to authenticate to keystone</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The name of the subnet that should be created</td>
    </tr>
            <tr>
    <td>network_name</td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>Name of the network to which the subnet should be attached</td>
    </tr>
            <tr>
    <td>region_name</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>Name of the region</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Indicate desired state of the resource</td>
    </tr>
            <tr>
    <td>tenant_name</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The name of the tenant for whom the subnet should be created</td>
    </tr>
        </table>


.. note:: Requires quantumclient


.. note:: Requires neutronclient


.. note:: Requires keystoneclient


Examples
--------

.. raw:: html

    <br/>


::

    # Create a subnet for a tenant with the specified subnet
    - quantum_subnet: state=present login_username=admin login_password=admin
                      login_tenant_name=admin tenant_name=tenant1
                      network_name=network1 name=net1subnet cidr=192.168.0.0/24"



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

