.. _rax_clb_nodes:


rax_clb_nodes - add, modify and remove nodes from a Rackspace Cloud Load Balancer
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Adds, modifies and removes nodes from a Rackspace Cloud Load Balancer


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * pyrax


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
    <td>address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>IP address or domain name of the node</div></td></tr>
            <tr>
    <td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Rackspace API key (overrides <em>credentials</em>)</div></br>
        <div style="font-size: small;">aliases: password<div></td></tr>
            <tr>
    <td>condition<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>enabled</li><li>disabled</li><li>draining</li></ul></td>
        <td><div>Condition for the node, which determines its role within the load balancer</div></td></tr>
            <tr>
    <td>credentials<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>File to find the Rackspace credentials in (ignored if <em>api_key</em> and <em>username</em> are provided)</div></br>
        <div style="font-size: small;">aliases: creds_file<div></td></tr>
            <tr>
    <td>env<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Environment as configured in ~/.pyrax.cfg, see <a href='https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration'>https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration</a></div></td></tr>
            <tr>
    <td>load_balancer_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Load balancer id</div></td></tr>
            <tr>
    <td>node_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Node id</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Port number of the load balanced service on the node</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>DFW</td>
        <td><ul></ul></td>
        <td><div>Region to create an instance in</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the node</div></td></tr>
            <tr>
    <td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>primary</li><li>secondary</li></ul></td>
        <td><div>Type of node</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Rackspace username (overrides <em>credentials</em>)</div></td></tr>
            <tr>
    <td>verify_ssl<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether or not to require SSL validation of API endpoints</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Wait for the load balancer to become active before returning</div></td></tr>
            <tr>
    <td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td><div>How long to wait before giving up and returning an error</div></td></tr>
            <tr>
    <td>weight<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Weight of node</div></td></tr>
        </table>
    </br>



Examples
--------

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


Notes
-----

.. note:: The following environment variables can be used, ``RAX_USERNAME``, ``RAX_API_KEY``, ``RAX_CREDS_FILE``, ``RAX_CREDENTIALS``, ``RAX_REGION``.
.. note:: ``RAX_CREDENTIALS`` and ``RAX_CREDS_FILE`` points to a credentials file appropriate for pyrax. See https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#authenticating
.. note:: ``RAX_USERNAME`` and ``RAX_API_KEY`` obviate the use of a credentials file
.. note:: ``RAX_REGION`` defines a Rackspace Public Cloud region (DFW, ORD, LON, ...)


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

