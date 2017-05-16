.. _keystone_user:


keystone_user - Manage OpenStack Identity (keystone) users, tenants and roles
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1

DEPRECATED
----------

Deprecated in 2.0. Use os_user instead

Synopsis
--------

Manage users,tenants, roles from OpenStack.


Requirements
------------

  * python >= 2.6
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
    <td>email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>An email address for the user</div></td></tr>
            <tr>
    <td>endpoint<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>http://127.0.0.1:35357/v2.0/</td>
        <td><ul></ul></td>
        <td><div>The keystone url for authentication</div></td></tr>
            <tr>
    <td>login_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul></ul></td>
        <td><div>Password of login user</div></td></tr>
            <tr>
    <td>login_tenant_name<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The tenant login_user belongs to</div></td></tr>
            <tr>
    <td>login_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>admin</td>
        <td><ul></ul></td>
        <td><div>login username to authenticate to keystone</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The password to be assigned to the user</div></td></tr>
            <tr>
    <td>role<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the role to be assigned or created</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource</div></td></tr>
            <tr>
    <td>tenant<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The tenant name that has be added/removed</div></td></tr>
            <tr>
    <td>tenant_description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A description for the tenant</div></td></tr>
            <tr>
    <td>token<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The token to be uses in case the password is not specified</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the user that has to added/removed from OpenStack</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a tenant
    - keystone_user: tenant=demo tenant_description="Default Tenant"
    
    # Create a user
    - keystone_user: user=john tenant=demo password=secrete
    
    # Apply the admin role to the john user in the demo tenant
    - keystone_user: role=admin user=john tenant=demo





For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

