.. _linode:


linode - create / delete / stop / restart an instance in Linode Public Cloud
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.3


.. contents::
   :local:
   :depth: 1


Synopsis
--------

creates / deletes a Linode Public Cloud instance and optionally waits for it to be 'running'.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * linode-python
  * pycurl


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
    <td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Linode API key</div></td></tr>
            <tr>
    <td>datacenter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>datacenter to create an instance in (Linode Datacenter)</div></td></tr>
            <tr>
    <td>distribution<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>distribution to use for the instance (Linode Distribution)</div></td></tr>
            <tr>
    <td>linode_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Unique ID of a linode server</div></br>
        <div style="font-size: small;">aliases: lid<div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name to give the instance (alphanumeric, dashes, underscore)</div><div>To keep sanity on the Linode Web Console, name is prepended with LinodeID_</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>root password to apply to a new server (auto generated if missing)</div></td></tr>
            <tr>
    <td>payment_term<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>1</li><li>12</li><li>24</li></ul></td>
        <td><div>payment term to use for the instance (payment term in months)</div></td></tr>
            <tr>
    <td>plan<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>plan to use for the instance (Linode plan)</div></td></tr>
            <tr>
    <td>ssh_pub_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>SSH public key applied to root user</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>active</li><li>started</li><li>absent</li><li>deleted</li><li>stopped</li><li>restarted</li></ul></td>
        <td><div>Indicate desired state of the resource</div></td></tr>
            <tr>
    <td>swap<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>512</td>
        <td><ul></ul></td>
        <td><div>swap size in MB</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>wait for the instance to be in state 'running' before returning</div></td></tr>
            <tr>
    <td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td><div>how long before wait gives up, in seconds</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a server
    - local_action:
         module: linode
         api_key: 'longStringFromLinodeApi'
         name: linode-test1
         plan: 1
         datacenter: 2
         distribution: 99
         password: 'superSecureRootPassword'
         ssh_pub_key: 'ssh-rsa qwerty'
         swap: 768
         wait: yes
         wait_timeout: 600
         state: present
    
    # Ensure a running server (create if missing)
    - local_action:
         module: linode
         api_key: 'longStringFromLinodeApi'
         name: linode-test1
         linode_id: 12345678
         plan: 1
         datacenter: 2
         distribution: 99
         password: 'superSecureRootPassword'
         ssh_pub_key: 'ssh-rsa qwerty'
         swap: 768
         wait: yes
         wait_timeout: 600
         state: present
    
    # Delete a server
    - local_action:
         module: linode
         api_key: 'longStringFromLinodeApi'
         name: linode-test1
         linode_id: 12345678
         state: absent
    
    # Stop a server
    - local_action:
         module: linode
         api_key: 'longStringFromLinodeApi'
         name: linode-test1
         linode_id: 12345678
         state: stopped
    
    # Reboot a server
    - local_action:
         module: linode
         api_key: 'longStringFromLinodeApi'
         name: linode-test1
         linode_id: 12345678
         state: restarted


Notes
-----

.. note:: LINODE_API_KEY env variable can be used instead


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

