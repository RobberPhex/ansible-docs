.. _quantum_floating_ip_associate:


quantum_floating_ip_associate - Associate or disassociate a particular floating IP with an instance
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1

DEPRECATED
----------

Deprecated in 2.0. Use os_floating_ip instead

Synopsis
--------

Associates or disassociates a specific floating IP with a particular instance


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
        <td><div>the keystone url for authentication</div></td></tr>
            <tr>
    <td>instance_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>name of the instance to which the public IP should be assigned</div></td></tr>
            <tr>
    <td>ip_address<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>floating ip that should be assigned to the instance</div></td></tr>
            <tr>
    <td>login_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>yes</td>
        <td><ul></ul></td>
        <td><div>password of login user</div></td></tr>
            <tr>
    <td>login_tenant_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>the tenant name of the login user</div></td></tr>
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
        <td><div>name of the region</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>indicates the desired state of the resource</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Associate a specific floating IP with an Instance
    - quantum_floating_ip_associate:
               state=present
               login_username=admin
               login_password=admin
               login_tenant_name=admin
               ip_address=1.1.1.1
               instance_name=vm1





For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

