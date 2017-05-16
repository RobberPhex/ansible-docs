.. _quantum_router:


quantum_router - Create or Remove router from openstack
+++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2

DEPRECATED
----------

Deprecated in 2.0. Use :ref:`os_router <os_router>` instead.

Synopsis
--------

* Create or Delete routers from OpenStack


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
        <td><div>desired admin state of the created router .</div>        </td></tr>
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
        <td><div>Name to be give to the router</div>        </td></tr>
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
        <td><div>Name of the tenant for which the router has to be created, if none router would be created for the login tenant.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create a router for tenant admin
      quantum_router:
        state: present
        login_username: admin
        login_password: admin
        login_tenant_name: admin
        name: router1




For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
