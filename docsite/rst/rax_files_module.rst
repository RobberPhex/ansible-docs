.. _rax_files:


rax_files - Manipulate Rackspace Cloud Files Containers
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.5


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manipulate Rackspace Cloud Files Containers


Requirements
------------

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
    <td>clear_meta<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Optionally clear existing metadata when applying metadata to existing containers. Selecting this option is only appropriate when setting type=meta</div></td></tr>
            <tr>
    <td>container<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The container to use for container or metadata operations.</div></td></tr>
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
    <td>meta<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A hash of items to set as metadata values on a container</div></td></tr>
            <tr>
    <td>private<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Used to set a container as private, removing it from the CDN.  <b>Warning!</b> Private containers, if previously made public, can have live objects available until the TTL on cached objects expires</div></td></tr>
            <tr>
    <td>public<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Used to set a container as public, available via the Cloud Files CDN</div></td></tr>
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
        <td><div>Indicate desired state of the resource</div></td></tr>
            <tr>
    <td>ttl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>In seconds, set a container-wide TTL for all objects cached on CDN edge nodes. Setting a TTL is only appropriate for containers that are public</div></td></tr>
            <tr>
    <td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>file</td>
        <td><ul><li>file</li><li>meta</li></ul></td>
        <td><div>Type of object to do work on, i.e. metadata object or a container object</div></td></tr>
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
    <td>web_error<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Sets an object to be presented as the HTTP error page when accessed by the CDN URL</div></td></tr>
            <tr>
    <td>web_index<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Sets an object to be presented as the HTTP index page when accessed by the CDN URL</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: "Test Cloud Files Containers"
      hosts: local
      gather_facts: no
      tasks:
        - name: "List all containers"
          rax_files: state=list
    
        - name: "Create container called 'mycontainer'"
          rax_files: container=mycontainer
    
        - name: "Create container 'mycontainer2' with metadata"
          rax_files:
            container: mycontainer2
            meta:
              key: value
              file_for: someuser@example.com
    
        - name: "Set a container's web index page"
          rax_files: container=mycontainer web_index=index.html
    
        - name: "Set a container's web error page"
          rax_files: container=mycontainer web_error=error.html
    
        - name: "Make container public"
          rax_files: container=mycontainer public=yes
    
        - name: "Make container public with a 24 hour TTL"
          rax_files: container=mycontainer public=yes ttl=86400
    
        - name: "Make container private"
          rax_files: container=mycontainer private=yes
    
    - name: "Test Cloud Files Containers Metadata Storage"
      hosts: local
      gather_facts: no
      tasks:
        - name: "Get mycontainer2 metadata"
          rax_files:
            container: mycontainer2
            type: meta
    
        - name: "Set mycontainer2 metadata"
          rax_files:
            container: mycontainer2
            type: meta
            meta:
              uploaded_by: someuser@example.com
    
        - name: "Remove mycontainer2 metadata"
          rax_files:
            container: "mycontainer2"
            type: meta
            state: absent
            meta:
              key: ""
              file_for: ""


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

