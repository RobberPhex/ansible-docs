.. _nova_keypair:


nova_keypair - Add/Delete key pair from nova
++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1

DEPRECATED
----------

Deprecated in 2.0. Use os_keypair instead

Synopsis
--------

Add or Remove key pair from nova .


Requirements
------------

  * python >= 2.6
  * python-novaclient


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
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Name that has to be given to the key pair</div></td></tr>
            <tr>
    <td>public_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The public key that would be uploaded to nova and injected to vm's upon creation</div></td></tr>
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

    # Creates a key pair with the running users public key
    - nova_keypair: state=present login_username=admin
                    login_password=admin login_tenant_name=admin name=ansible_key
                    public_key={{ lookup('file','~/.ssh/id_rsa.pub') }}
    
    # Creates a new key pair and the private key returned after the run.
    - nova_keypair: state=present login_username=admin login_password=admin
                    login_tenant_name=admin name=ansible_key





For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

