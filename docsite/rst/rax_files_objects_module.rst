.. _rax_files_objects:


rax_files_objects - Upload, download, and delete objects in Rackspace Cloud Files
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.5


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Upload, download, and delete objects in Rackspace Cloud Files


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
    <td>clear_meta<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Optionally clear existing metadata when applying metadata to existing objects. Selecting this option is only appropriate when setting type=meta</div></td></tr>
            <tr>
    <td>container<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The container to use for file object operations.</div></td></tr>
            <tr>
    <td>credentials<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>File to find the Rackspace credentials in (ignored if <em>api_key</em> and <em>username</em> are provided)</div></br>
        <div style="font-size: small;">aliases: creds_file<div></td></tr>
            <tr>
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The destination of a "get" operation; i.e. a local directory, "/home/user/myfolder". Used to specify the destination of an operation on a remote object; i.e. a file name, "file1", or a comma-separated list of remote objects, "file1,file2,file17"</div></td></tr>
            <tr>
    <td>env<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Environment as configured in ~/.pyrax.cfg, see <a href='https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration'>https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration</a></div></td></tr>
            <tr>
    <td>expires<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Used to set an expiration on a file or folder uploaded to Cloud Files. Requires an integer, specifying expiration in seconds</div></td></tr>
            <tr>
    <td>meta<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A hash of items to set as metadata values on an uploaded file or folder</div></td></tr>
            <tr>
    <td>method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>get</td>
        <td><ul><li>get</li><li>put</li><li>delete</li></ul></td>
        <td><div>The method of operation to be performed.  For example, put to upload files to Cloud Files, get to download files from Cloud Files or delete to delete remote objects in Cloud Files</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>DFW</td>
        <td><ul></ul></td>
        <td><div>Region to create an instance in</div></td></tr>
            <tr>
    <td>src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Source from which to upload files.  Used to specify a remote object as a source for an operation, i.e. a file name, "file1", or a comma-separated list of remote objects, "file1,file2,file17".  src and dest are mutually exclusive on remote-only object operations</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource</div></td></tr>
            <tr>
    <td>structure<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>True</li><li>no</li></ul></td>
        <td><div>Used to specify whether to maintain nested directory structure when downloading objects from Cloud Files.  Setting to false downloads the contents of a container to a single, flat directory</div></td></tr>
            <tr>
    <td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>file</td>
        <td><ul><li>file</li><li>meta</li></ul></td>
        <td><div>Type of object to do work on</div><div>Metadata object or a file object</div></td></tr>
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
        </table>
    </br>



Examples
--------

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

