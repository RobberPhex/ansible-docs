.. _keystone_user:


keystone_user - Manage OpenStack Identity (keystone) users, tenants and roles
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

Manage users,tenants, roles from OpenStack.

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
    <td>email</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>An email address for the user</td>
    </tr>
            <tr>
    <td>endpoint</td>
    <td>no</td>
    <td>http://127.0.0.1:35357/v2.0/</td>
        <td><ul></ul></td>
        <td>The keystone url for authentication</td>
    </tr>
            <tr>
    <td>login_password</td>
    <td>no</td>
    <td>yes</td>
        <td><ul></ul></td>
        <td>Password of login user</td>
    </tr>
            <tr>
    <td>login_tenant_name</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The tenant login_user belongs to (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>login_user</td>
    <td>no</td>
    <td>admin</td>
        <td><ul></ul></td>
        <td>login username to authenticate to keystone</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The password to be assigned to the user</td>
    </tr>
            <tr>
    <td>role</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The name of the role to be assigned or created</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Indicate desired state of the resource</td>
    </tr>
            <tr>
    <td>tenant</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The tenant name that has be added/removed</td>
    </tr>
            <tr>
    <td>tenant_description</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>A description for the tenant</td>
    </tr>
            <tr>
    <td>token</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The token to be uses in case the password is not specified</td>
    </tr>
            <tr>
    <td>user</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The name of the user that has to added/removed from OpenStack</td>
    </tr>
        </table>


.. note:: Requires python-keystoneclient


Examples
--------

.. raw:: html

    <br/>


::

    # Create a tenant
    - keystone_user: tenant=demo tenant_description="Default Tenant"
    
    # Create a user
    - keystone_user: user=john tenant=demo password=secrete
    
    # Apply the admin role to the john user in the demo tenant
    - keystone_user: role=admin user=john tenant=demo



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

