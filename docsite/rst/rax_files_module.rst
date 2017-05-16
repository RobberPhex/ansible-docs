.. _rax_files:


rax_files - Manipulate Rackspace Cloud Files Containers
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.5

Manipulate Rackspace Cloud Files Containers

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
    <td>clear_meta</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Optionally clear existing metadata when applying metadata to existing containers. Selecting this option is only appropriate when setting type=meta</td>
    </tr>
            <tr>
    <td>container</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The container to use for container or metadata operations.</td>
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
        <td>A hash of items to set as metadata values on a container</td>
    </tr>
            <tr>
    <td>private</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Used to set a container as private, removing it from the CDN.  <b>Warning!</b> Private containers, if previously made public, can have live objects available until the TTL on cached objects expires</td>
    </tr>
            <tr>
    <td>public</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Used to set a container as public, available via the Cloud Files CDN</td>
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
    <td>ttl</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>In seconds, set a container-wide TTL for all objects cached on CDN edge nodes. Setting a TTL is only appropriate for containers that are public</td>
    </tr>
            <tr>
    <td>type</td>
    <td>no</td>
    <td>file</td>
        <td><ul><li>file</li><li>meta</li></ul></td>
        <td>Type of object to do work on, i.e. metadata object or a container object</td>
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
    <td>web_error</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Sets an object to be presented as the HTTP error page when accessed by the CDN URL</td>
    </tr>
            <tr>
    <td>web_index</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Sets an object to be presented as the HTTP index page when accessed by the CDN URL</td>
    </tr>
        </table>


.. note:: Requires pyrax


Examples
--------

.. raw:: html

    <br/>


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

