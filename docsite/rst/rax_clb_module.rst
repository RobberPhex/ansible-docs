.. _rax_clb:


rax_clb - create / delete a load balancer in Rackspace Public Cloud
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

creates / deletes a Rackspace Public Cloud load balancer.

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
    <td>algorithm</td>
    <td>no</td>
    <td>LEAST_CONNECTIONS</td>
        <td><ul><li>RANDOM</li><li>LEAST_CONNECTIONS</li><li>ROUND_ROBIN</li><li>WEIGHTED_LEAST_CONNECTIONS</li><li>WEIGHTED_ROUND_ROBIN</li></ul></td>
        <td>algorithm for the balancer being created</td>
    </tr>
            <tr>
    <td>api_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Rackspace API key (overrides <em>credentials</em>)</td>
    </tr>
            <tr>
    <td>credentials</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>File to find the Rackspace credentials in (ignored if <em>api_key</em> and <em>username</em> are provided)</td>
    </tr>
            <tr>
    <td>env</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Environment as configured in ~/.pyrax.cfg, see <a href='https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration'>https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration</a> (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>meta</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A hash of metadata to associate with the instance</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name to give the load balancer</td>
    </tr>
            <tr>
    <td>port</td>
    <td>no</td>
    <td>80</td>
        <td><ul></ul></td>
        <td>Port for the balancer being created</td>
    </tr>
            <tr>
    <td>protocol</td>
    <td>no</td>
    <td>HTTP</td>
        <td><ul><li>DNS_TCP</li><li>DNS_UDP</li><li>FTP</li><li>HTTP</li><li>HTTPS</li><li>IMAPS</li><li>IMAPv4</li><li>LDAP</li><li>LDAPS</li><li>MYSQL</li><li>POP3</li><li>POP3S</li><li>SMTP</li><li>TCP</li><li>TCP_CLIENT_FIRST</li><li>UDP</li><li>UDP_STREAM</li><li>SFTP</li></ul></td>
        <td>Protocol for the balancer being created</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td>DFW</td>
        <td><ul></ul></td>
        <td>Region to create an instance in</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Indicate desired state of the resource</td>
    </tr>
            <tr>
    <td>timeout</td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td>timeout for communication between the balancer and the node</td>
    </tr>
            <tr>
    <td>type</td>
    <td>no</td>
    <td>PUBLIC</td>
        <td><ul><li>PUBLIC</li><li>SERVICENET</li></ul></td>
        <td>type of interface for the balancer being created</td>
    </tr>
            <tr>
    <td>username</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Rackspace username (overrides <em>credentials</em>)</td>
    </tr>
            <tr>
    <td>verify_ssl</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Whether or not to require SSL validation of API endpoints (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>vip_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Virtual IP ID to use when creating the load balancer for purposes of sharing an IP with another load balancer of another protocol (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>wait</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>wait for the balancer to be in state 'running' before returning</td>
    </tr>
            <tr>
    <td>wait_timeout</td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td>how long before wait gives up, in seconds</td>
    </tr>
        </table>


.. note:: Requires pyrax


Examples
--------

.. raw:: html

    <br/>


::

    - name: Build a Load Balancer
      gather_facts: False
      hosts: local
      connection: local
      tasks:
        - name: Load Balancer create request
          local_action:
            module: rax_clb
            credentials: ~/.raxpub
            name: my-lb
            port: 8080
            protocol: HTTP
            type: SERVICENET
            timeout: 30
            region: DFW
            wait: yes
            state: present
            meta:
              app: my-cool-app
          register: my_lb

.. note:: The following environment variables can be used, ``RAX_USERNAME``, ``RAX_API_KEY``, ``RAX_CREDS_FILE``, ``RAX_CREDENTIALS``, ``RAX_REGION``.
.. note:: ``RAX_CREDENTIALS`` and ``RAX_CREDS_FILE`` points to a credentials file appropriate for pyrax. See https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#authenticating
.. note:: ``RAX_USERNAME`` and ``RAX_API_KEY`` obviate the use of a credentials file
.. note:: ``RAX_REGION`` defines a Rackspace Public Cloud region (DFW, ORD, LON, ...)


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

