.. _rax_files_objects:


rax_files_objects - Upload, download, and delete objects in Rackspace Cloud Files
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.5

Upload, download, and delete objects in Rackspace Cloud Files

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
        <td>Optionally clear existing metadata when applying metadata to existing objects. Selecting this option is only appropriate when setting type=meta</td>
    </tr>
            <tr>
    <td>container</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The container to use for file object operations.</td>
    </tr>
            <tr>
    <td>credentials</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>File to find the Rackspace credentials in (ignored if <em>api_key</em> and <em>username</em> are provided)</td>
    </tr>
            <tr>
    <td>dest</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The destination of a "get" operation; i.e. a local directory, "/home/user/myfolder". Used to specify the destination of an operation on a remote object; i.e. a file name, "file1", or a comma-separated list of remote objects, "file1,file2,file17"</td>
    </tr>
            <tr>
    <td>env</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Environment as configured in ~/.pyrax.cfg, see <a href='https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration'>https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration</a> (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>expires</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Used to set an expiration on a file or folder uploaded to Cloud Files. Requires an integer, specifying expiration in seconds</td>
    </tr>
            <tr>
    <td>meta</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A hash of items to set as metadata values on an uploaded file or folder</td>
    </tr>
            <tr>
    <td>method</td>
    <td>no</td>
    <td>get</td>
        <td><ul><li>get</li><li>put</li><li>delete</li></ul></td>
        <td>The method of operation to be performed.  For example, put to upload files to Cloud Files, get to download files from Cloud Files or delete to delete remote objects in Cloud Files</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td>DFW</td>
        <td><ul></ul></td>
        <td>Region to create an instance in</td>
    </tr>
            <tr>
    <td>src</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Source from which to upload files.  Used to specify a remote object as a source for an operation, i.e. a file name, "file1", or a comma-separated list of remote objects, "file1,file2,file17".  src and dest are mutually exclusive on remote-only object operations</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Indicate desired state of the resource</td>
    </tr>
            <tr>
    <td>structure</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>True</li><li>no</li></ul></td>
        <td>Used to specify whether to maintain nested directory structure when downloading objects from Cloud Files.  Setting to false downloads the contents of a container to a single, flat directory</td>
    </tr>
            <tr>
    <td>type</td>
    <td>no</td>
    <td>file</td>
        <td><ul><li>file</li><li>meta</li></ul></td>
        <td>Type of object to do work onMetadata object or a file object</td>
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

    - name: "Test Cloud Files Objects"
      hosts: local
      gather_facts: False
      tasks:
        - name: "Get objects from test container"
          rax_files_objects: container=testcont dest=~/Downloads/testcont
    
        - name: "Get single object from test container"
          rax_files_objects: container=testcont src=file1 dest=~/Downloads/testcont
    
        - name: "Get several objects from test container"
          rax_files_objects: container=testcont src=file1,file2,file3 dest=~/Downloads/testcont
    
        - name: "Delete one object in test container"
          rax_files_objects: container=testcont method=delete dest=file1
    
        - name: "Delete several objects in test container"
          rax_files_objects: container=testcont method=delete dest=file2,file3,file4
    
        - name: "Delete all objects in test container"
          rax_files_objects: container=testcont method=delete
    
        - name: "Upload all files to test container"
          rax_files_objects: container=testcont method=put src=~/Downloads/onehundred
    
        - name: "Upload one file to test container"
          rax_files_objects: container=testcont method=put src=~/Downloads/testcont/file1
    
        - name: "Upload one file to test container with metadata"
          rax_files_objects:
            container: testcont
            src: ~/Downloads/testcont/file2
            method: put
            meta:
              testkey: testdata
              who_uploaded_this: someuser@example.com
    
        - name: "Upload one file to test container with TTL of 60 seconds"
          rax_files_objects: container=testcont method=put src=~/Downloads/testcont/file3 expires=60
    
        - name: "Attempt to get remote object that does not exist"
          rax_files_objects: container=testcont method=get src=FileThatDoesNotExist.jpg dest=~/Downloads/testcont
          ignore_errors: yes
    
        - name: "Attempt to delete remote object that does not exist"
          rax_files_objects: container=testcont method=delete dest=FileThatDoesNotExist.jpg
          ignore_errors: yes
    
    - name: "Test Cloud Files Objects Metadata"
      hosts: local
      gather_facts: false
      tasks:
        - name: "Get metadata on one object"
          rax_files_objects:  container=testcont type=meta dest=file2
    
        - name: "Get metadata on several objects"
          rax_files_objects:  container=testcont type=meta src=file2,file1
    
        - name: "Set metadata on an object"
          rax_files_objects:
            container: testcont
            type: meta
            dest: file17
            method: put
            meta:
              key1: value1
              key2: value2
            clear_meta: true
    
        - name: "Verify metadata is set"
          rax_files_objects:  container=testcont type=meta src=file17
    
        - name: "Delete metadata"
          rax_files_objects:
            container: testcont
            type: meta
            dest: file17
            method: delete
            meta:
              key1: ''
              key2: ''
    
        - name: "Get metadata on all objects"
          rax_files_objects:  container=testcont type=meta

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

