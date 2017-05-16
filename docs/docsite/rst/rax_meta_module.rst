.. _rax_meta:


rax_meta - Manipulate metadata for Rackspace Cloud Servers
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.7


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manipulate metadata for Rackspace Cloud Servers


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
                <tr><td>address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Server IP address to modify metadata for, will match any IP assigned to the server</div>        </td></tr>
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Rackspace API key, overrides <em>credentials</em>.</div></br>
    <div style="font-size: small;">aliases: password<div>        </td></tr>
                <tr><td>auth_endpoint<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>https://identity.api.rackspacecloud.com/v2.0/</td>
        <td></td>
        <td><div>The URI of the authentication service.</div>        </td></tr>
                <tr><td>credentials<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>File to find the Rackspace credentials in. Ignored if <em>api_key</em> and <em>username</em> are provided.</div></br>
    <div style="font-size: small;">aliases: creds_file<div>        </td></tr>
                <tr><td>env<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Environment as configured in <em>~/.pyrax.cfg</em>, see <a href='https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration'>https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration</a>.</div>        </td></tr>
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Server ID to modify metadata for</div>        </td></tr>
                <tr><td>identity_type<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>rackspace</td>
        <td></td>
        <td><div>Authentication mechanism to use, such as rackspace or keystone.</div>        </td></tr>
                <tr><td>meta<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A hash of metadata to associate with the instance</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Server name to modify metadata for</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>DFW</td>
        <td></td>
        <td><div>Region to create an instance in.</div>        </td></tr>
                <tr><td>tenant_id<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The tenant ID used for authentication.</div>        </td></tr>
                <tr><td>tenant_name<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The tenant name used for authentication.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Rackspace username, overrides <em>credentials</em>.</div>        </td></tr>
                <tr><td>verify_ssl<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether or not to require SSL validation of API endpoints.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Set metadata for a server
      hosts: all
      gather_facts: False
      tasks:
        - name: Set metadata
          local_action:
            module: rax_meta
            credentials: ~/.raxpub
            name: "{{ inventory_hostname }}"
            region: DFW
            meta:
              group: primary_group
              groups:
                - group_two
                - group_three
              app: my_app
    
        - name: Clear metadata
          local_action:
            module: rax_meta
            credentials: ~/.raxpub
            name: "{{ inventory_hostname }}"
            region: DFW


Notes
-----

.. note::
    - The following environment variables can be used, ``RAX_USERNAME``, ``RAX_API_KEY``, ``RAX_CREDS_FILE``, ``RAX_CREDENTIALS``, ``RAX_REGION``.
    - ``RAX_CREDENTIALS`` and ``RAX_CREDS_FILE`` points to a credentials file appropriate for pyrax. See https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#authenticating
    - ``RAX_USERNAME`` and ``RAX_API_KEY`` obviate the use of a credentials file
    - ``RAX_REGION`` defines a Rackspace Public Cloud region (DFW, ORD, LON, ...)



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
