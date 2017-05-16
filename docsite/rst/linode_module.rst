.. _linode:


linode - create / delete / stop / restart an instance in Linode Public Cloud
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3

creates / deletes a Linode Public Cloud instance and optionally waits for it to be 'running'.

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
    <td>api_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Linode API key</td>
    </tr>
            <tr>
    <td>datacenter</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>datacenter to create an instance in (Linode Datacenter)</td>
    </tr>
            <tr>
    <td>distribution</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>distribution to use for the instance (Linode Distribution)</td>
    </tr>
            <tr>
    <td>linode_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Unique ID of a linode server</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name to give the instance (alphanumeric, dashes, underscore)To keep sanity on the Linode Web Console, name is prepended with LinodeID_</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>root password to apply to a new server (auto generated if missing)</td>
    </tr>
            <tr>
    <td>payment_term</td>
    <td>no</td>
    <td>1</td>
        <td><ul><li>1</li><li>12</li><li>24</li></ul></td>
        <td>payment term to use for the instance (payment term in months)</td>
    </tr>
            <tr>
    <td>plan</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>plan to use for the instance (Linode plan)</td>
    </tr>
            <tr>
    <td>ssh_pub_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>SSH public key applied to root user</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>active</li><li>started</li><li>absent</li><li>deleted</li><li>stopped</li><li>restarted</li></ul></td>
        <td>Indicate desired state of the resource</td>
    </tr>
            <tr>
    <td>swap</td>
    <td>no</td>
    <td>512</td>
        <td><ul></ul></td>
        <td>swap size in MB</td>
    </tr>
            <tr>
    <td>wait</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>wait for the instance to be in state 'running' before returning</td>
    </tr>
            <tr>
    <td>wait_timeout</td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td>how long before wait gives up, in seconds</td>
    </tr>
        </table>


.. note:: Requires linode-python


.. note:: Requires pycurl


Examples
--------

.. raw:: html

    <br/>


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

.. note:: LINODE_API_KEY env variable can be used instead


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

