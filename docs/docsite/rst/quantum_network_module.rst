.. _quantum_network:


quantum_network - Creates/Removes networks from OpenStack
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 2

DEPRECATED
----------

Deprecated in 2.0. Use :ref:`os_network <os_network>` instead.

Synopsis
--------

* Add or Remove network from OpenStack.


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
                <tr><td>admin_state_up<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Whether the state should be marked as up or down</div>        </td></tr>
                <tr><td>auth_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>http://127.0.0.1:35357/v2.0/</td>
        <td></td>
        <td><div>The keystone url for authentication</div>        </td></tr>
                <tr><td>login_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>yes</td>
        <td></td>
        <td><div>Password of login user</div>        </td></tr>
                <tr><td>login_tenant_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>yes</td>
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
        <td><div>Name to be assigned to the network</div>        </td></tr>
                <tr><td>provider_network_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The type of the network to be created, gre, vlan, local. Available types depend on the plugin. The Quantum service decides if not specified.</div>        </td></tr>
                <tr><td>provider_physical_network<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The physical network which would realize the virtual network for flat and vlan networks.</div>        </td></tr>
                <tr><td>provider_segmentation_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The id that has to be assigned to the network, in case of vlan networks that would be vlan id and for gre the tunnel id</div>        </td></tr>
                <tr><td>region_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Name of the region</div>        </td></tr>
                <tr><td>router_external<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If 'yes', specifies that the virtual network is a external network (public).</div>        </td></tr>
                <tr><td>shared<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether this network is shared or not</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource</div>        </td></tr>
                <tr><td>tenant_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The name of the tenant for whom the network is created</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create a GRE backed Quantum network with tunnel id 1 for tenant1
      quantum_network:
        name: t1network
        tenant_name: tenant1
        state: present
        provider_network_type: gre
        provider_segmentation_id: 1
        login_username: admin
        login_password: admin
        login_tenant_name: admin
    
    - name: Create an external network
      quantum_network:
        name: external_network
        state: present
        provider_network_type: local
        router_external: yes
        login_username: admin
        login_password: admin
        login_tenant_name: admin




For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
