.. _rax_cbs:


rax_cbs - Manipulate Rackspace Cloud Block Storage Volumes
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manipulate Rackspace Cloud Block Storage Volumes


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
    <td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Rackspace API key (overrides <em>credentials</em>)</div></br>
        <div style="font-size: small;">aliases: password<div></td></tr>
            <tr>
    <td>auth_endpoint<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>https://identity.api.rackspacecloud.com/v2.0/</td>
        <td><ul></ul></td>
        <td><div>The URI of the authentication service</div></td></tr>
            <tr>
    <td>credentials<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>File to find the Rackspace credentials in (ignored if <em>api_key</em> and <em>username</em> are provided)</div></br>
        <div style="font-size: small;">aliases: creds_file<div></td></tr>
            <tr>
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Description to give the volume being created</div></td></tr>
            <tr>
    <td>env<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Environment as configured in ~/.pyrax.cfg, see <a href='https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration'>https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration</a></div></td></tr>
            <tr>
    <td>identity_type<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>rackspace</td>
        <td><ul></ul></td>
        <td><div>Authentication machanism to use, such as rackspace or keystone</div></td></tr>
            <tr>
    <td>image<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>image to use for bootable volumes. Can be an <code>id</code>, <code>human_id</code> or <code>name</code>. This option requires <code>pyrax&gt;=1.9.3</code></div></td></tr>
            <tr>
    <td>meta<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A hash of metadata to associate with the volume</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name to give the volume being created</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>DFW</td>
        <td><ul></ul></td>
        <td><div>Region to create an instance in</div></td></tr>
            <tr>
    <td>size<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>100</td>
        <td><ul></ul></td>
        <td><div>Size of the volume to create in Gigabytes</div></td></tr>
            <tr>
    <td>snapshot_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The id of the snapshot to create the volume from</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource</div></td></tr>
            <tr>
    <td>tenant_id<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The tenant ID used for authentication</div></td></tr>
            <tr>
    <td>tenant_name<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The tenant name used for authentication</div></td></tr>
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
    <td>volume_type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>SATA</td>
        <td><ul><li>SATA</li><li>SSD</li></ul></td>
        <td><div>Type of the volume being created</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>wait for the volume to be in state 'available' before returning</div></td></tr>
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

    - name: Build a Block Storage Volume
      gather_facts: False
      hosts: local
      connection: local
      tasks:
        - name: Storage volume create request
          local_action:
            module: rax_cbs
            credentials: ~/.raxpub
            name: my-volume
            description: My Volume
            volume_type: SSD
            size: 150
            region: DFW
            wait: yes
            state: present
            meta:
              app: my-cool-app
          register: my_volume


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

