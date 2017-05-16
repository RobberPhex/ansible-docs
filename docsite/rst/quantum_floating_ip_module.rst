.. _quantum_floating_ip:


quantum_floating_ip - Add/Remove floating IP from an instance
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1

DEPRECATED
----------

Deprecated in 2.0. Use os_floating_ip instead

Synopsis
--------

Add or Remove a floating IP to an instance


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * python-novaclient
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
        <td><div>The keystone url for authentication</div></td></tr>
            <tr>
    <td>instance_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the instance to which the IP address should be assigned</div></td></tr>
            <tr>
    <td>internal_network_name<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the network of the port to associate with the floating ip. Necessary when VM multiple networks.</div></td></tr>
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
    <td>network_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Name of the network from which IP has to be assigned to VM. Please make sure the network is an external network</div></td></tr>
            <tr>
    <td>region_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Name of the region</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Assign a floating ip to the instance from an external network
    - quantum_floating_ip: state=present login_username=admin login_password=admin
                           login_tenant_name=admin network_name=external_network
                           instance_name=vm1 internal_network_name=internal_network





For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

