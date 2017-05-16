.. _rax_clb_nodes:


rax_clb_nodes - add, modify and remove nodes from a Rackspace Cloud Load Balancer
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

Adds, modifies and removes nodes from a Rackspace Cloud Load Balancer

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
    <td>address</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>IP address or domain name of the node</td>
    </tr>
            <tr>
    <td>api_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Rackspace API key (overrides <em>credentials</em>)</td>
    </tr>
            <tr>
    <td>condition</td>
    <td>no</td>
    <td></td>
        <td><ul><li>enabled</li><li>disabled</li><li>draining</li></ul></td>
        <td>Condition for the node, which determines its role within the load balancer</td>
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
    <td>load_balancer_id</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Load balancer id</td>
    </tr>
            <tr>
    <td>node_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Node id</td>
    </tr>
            <tr>
    <td>port</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Port number of the load balanced service on the node</td>
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
        <td>Indicate desired state of the node</td>
    </tr>
            <tr>
    <td>type</td>
    <td>no</td>
    <td></td>
        <td><ul><li>primary</li><li>secondary</li></ul></td>
        <td>Type of node</td>
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
    <td>wait</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Wait for the load balancer to become active before returning</td>
    </tr>
            <tr>
    <td>wait_timeout</td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td>How long to wait before giving up and returning an error</td>
    </tr>
            <tr>
    <td>weight</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Weight of node</td>
    </tr>
        </table>


.. note:: Requires pyrax


Examples
--------

.. raw:: html

    <br/>


::

    # Add a new node to the load balancer
    - local_action:
        module: rax_clb_nodes
        load_balancer_id: 71
        address: 10.2.2.3
        port: 80
        condition: enabled
        type: primary
        wait: yes
        credentials: /path/to/credentials
    
    # Drain connections from a node
    - local_action:
        module: rax_clb_nodes
        load_balancer_id: 71
        node_id: 410
        condition: draining
        wait: yes
        credentials: /path/to/credentials
    
    # Remove a node from the load balancer
    - local_action:
        module: rax_clb_nodes
        load_balancer_id: 71
        node_id: 410
        state: absent
        wait: yes
        credentials: /path/to/credentials

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

