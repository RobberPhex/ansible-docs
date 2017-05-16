.. _quantum_router_interface:


quantum_router_interface - Attach/Dettach a subnet's interface to a router
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1

DEPRECATED
----------

Deprecated in 2.0. Use os_router instead

Synopsis
--------

Attach/Dettach a subnet interface to a router, to provide a gateway for the subnet.


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
            <tr>
    <td>auth_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>http://127.0.0.1:35357/v2.0/</td>
        <td><ul></ul></td>
        <td><div>The keystone URL for authentication</div></td></tr>
            <tr>
    <td>login_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>yes</td>
        <td><ul></ul></td>
        <td><div>Password of login user</div></td></tr>
            <tr>
    <td>login_tenant_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>yes</td>
        <td><ul></ul></td>
        <td><div>The tenant name of the login user</div></td></tr>
            <tr>
    <td>login_username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>admin</td>
        <td><ul></ul></td>
        <td><div>login username to authenticate to keystone</div></td></tr>
            <tr>
    <td>region_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Name of the region</div></td></tr>
            <tr>
    <td>router_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Name of the router to which the subnet's interface should be attached.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource</div></td></tr>
            <tr>
    <td>subnet_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Name of the subnet to whose interface should be attached to the router.</div></td></tr>
            <tr>
    <td>tenant_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Name of the tenant whose subnet has to be attached.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Attach tenant1's subnet to the external router
    - quantum_router_interface: state=present login_username=admin
                                login_password=admin
                                login_tenant_name=admin
                                tenant_name=tenant1
                                router_name=external_route
                                subnet_name=t1subnet





For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

