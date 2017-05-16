.. _rax_keypair:


rax_keypair - Create a keypair for use with Rackspace Cloud Servers
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.5

Create a keypair for use with Rackspace Cloud Servers

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
        <td>Rackspace API key (overrides <em>credentials</em>)</td>
    </tr>
            <tr>
    <td>auth_endpoint</td>
    <td>no</td>
    <td>https://identity.api.rackspacecloud.com/v2.0/</td>
        <td><ul></ul></td>
        <td>The URI of the authentication service (added in Ansible 1.5)</td>
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
    <td>identity_type</td>
    <td>no</td>
    <td>rackspace</td>
        <td><ul></ul></td>
        <td>Authentication machanism to use, such as rackspace or keystone (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of keypair</td>
    </tr>
            <tr>
    <td>public_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Public Key string to upload. Can be a file path or string</td>
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
    <td>tenant_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The tenant ID used for authentication (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>tenant_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The tenant name used for authentication (added in Ansible 1.5)</td>
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
        </table>


.. note:: Requires pyrax


Examples
--------

.. raw:: html

    <br/>


::

    - name: Create a keypair
      hosts: localhost
      gather_facts: False
      tasks:
        - name: keypair request
          local_action:
            module: rax_keypair
            credentials: ~/.raxpub
            name: my_keypair
            region: DFW
          register: keypair
        - name: Create local public key
          local_action:
            module: copy
            content: "{{ keypair.keypair.public_key }}"
            dest: "{{ inventory_dir }}/{{ keypair.keypair.name }}.pub"
        - name: Create local private key
          local_action:
            module: copy
            content: "{{ keypair.keypair.private_key }}"
            dest: "{{ inventory_dir }}/{{ keypair.keypair.name }}"
    
    - name: Create a keypair
      hosts: localhost
      gather_facts: False
      tasks:
        - name: keypair request
          local_action:
            module: rax_keypair
            credentials: ~/.raxpub
            name: my_keypair
            public_key: "{{ lookup('file', 'authorized_keys/id_rsa.pub') }}"
            region: DFW
          register: keypair

.. note:: Keypairs cannot be manipulated, only created and deleted. To "update" a keypair you must first delete and then recreate.
.. note:: The ability to specify a file path for the public key was added in 1.7
.. note:: The following environment variables can be used, ``RAX_USERNAME``, ``RAX_API_KEY``, ``RAX_CREDS_FILE``, ``RAX_CREDENTIALS``, ``RAX_REGION``.
.. note:: ``RAX_CREDENTIALS`` and ``RAX_CREDS_FILE`` points to a credentials file appropriate for pyrax. See https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#authenticating
.. note:: ``RAX_USERNAME`` and ``RAX_API_KEY`` obviate the use of a credentials file
.. note:: ``RAX_REGION`` defines a Rackspace Public Cloud region (DFW, ORD, LON, ...)


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

