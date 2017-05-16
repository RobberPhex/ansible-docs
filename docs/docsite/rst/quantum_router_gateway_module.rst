.. _quantum_router_gateway:


quantum_router_gateway - set/unset a gateway interface for the router with the specified external network
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2

DEPRECATED
----------

Deprecated in 2.0. Use :ref:`os_router <os_router>` instead.

Synopsis
--------

* Creates/Removes a gateway interface from the router, used to associate a external network with a router to route external traffic.


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
                <tr><td>auth_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>http://127.0.0.1:35357/v2.0/</td>
        <td></td>
        <td><div>The keystone URL for authentication</div>        </td></tr>
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
                <tr><td>network_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td></td>
        <td><div>Name of the external network which should be attached to the router.</div>        </td></tr>
                <tr><td>region_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Name of the region</div>        </td></tr>
                <tr><td>router_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td></td>
        <td><div>Name of the router to which the gateway should be attached.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Attach an external network with a router to allow flow of external traffic
      quantum_router_gateway:
        state: present
        login_username: admin
        login_password: admin
        login_tenant_name: admin
        router_name: external_router
        network_name: external_network




For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
