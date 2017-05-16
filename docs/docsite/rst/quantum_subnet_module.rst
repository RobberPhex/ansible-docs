.. _quantum_subnet:


quantum_subnet - Add/remove subnet from a network
+++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2

DEPRECATED
----------

Deprecated in 2.0. Use :ref:`os_subnet <os_subnet>` instead.

Synopsis
--------

* Add/remove subnet from a network


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * python-neutronclient or python-quantumclient
  * python-keystoneclient


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
                <tr><td>allocation_pool_end<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>From the subnet pool the last IP that should be assigned to the virtual machines</div>        </td></tr>
                <tr><td>allocation_pool_start<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>From the subnet pool the starting address from which the IP should be allocated</div>        </td></tr>
                <tr><td>auth_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>http://127.0.0.1:35357/v2.0/</td>
        <td></td>
        <td><div>The keystone URL for authentication</div>        </td></tr>
                <tr><td>cidr<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td></td>
        <td><div>The CIDR representation of the subnet that should be assigned to the subnet</div>        </td></tr>
                <tr><td>dns_nameservers<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>DNS nameservers for this subnet, comma-separated</div>        </td></tr>
                <tr><td>enable_dhcp<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Whether DHCP should be enabled for this subnet.</div>        </td></tr>
                <tr><td>gateway_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The ip that would be assigned to the gateway for this subnet</div>        </td></tr>
                <tr><td>ip_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>4</td>
        <td></td>
        <td><div>The IP version of the subnet 4 or 6</div>        </td></tr>
                <tr><td>login_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>True</td>
        <td></td>
        <td><div>Password of login user</div>        </td></tr>
                <tr><td>login_tenant_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>True</td>
        <td></td>
        <td><div>The tenant name of the login user</div>        </td></tr>
                <tr><td>login_username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>admin</td>
        <td></td>
        <td><div>login username to authenticate to keystone</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td></td>
        <td><div>The name of the subnet that should be created</div>        </td></tr>
                <tr><td>network_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td></td>
        <td><div>Name of the network to which the subnet should be attached</div>        </td></tr>
                <tr><td>region_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Name of the region</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource</div>        </td></tr>
                <tr><td>tenant_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The name of the tenant for whom the subnet should be created</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create a subnet for a tenant with the specified subnet
      quantum_subnet:
        state: present
        login_username: admin
        login_password: admin
        login_tenant_name: admin
        tenant_name: tenant1
        network_name: network1
        name: net1subnet
        cidr: 192.168.0.0/24




For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
