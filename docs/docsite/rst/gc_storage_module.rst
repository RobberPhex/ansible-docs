.. _gc_storage:


gc_storage - This module manages objects/buckets in Google Cloud Storage.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module allows users to manage their objects/buckets in Google Cloud Storage.  It allows upload and download operations and can set some canned permissions. It also allows retrieval of URLs for objects for use in playbooks, and retrieval of string contents of objects.  This module requires setting the default project in GCS prior to playbook usage.  See https://developers.google.com/storage/docs/reference/v1/apiversion1 for information about setting the default project.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * boto >= 2.9


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
                <tr><td>bucket<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Bucket name.</div>        </td></tr>
                <tr><td>dest<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The destination file path when downloading an object/key with a GET operation.</div>        </td></tr>
                <tr><td>expiration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Time limit (in seconds) for the URL generated and returned by GCA when performing a mode=put or mode=get_url operation. This url is only available when public-read is the acl for the object.</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Forces an overwrite either locally on the filesystem or remotely with the object/key. Used with PUT and GET operations.</div></br>
    <div style="font-size: small;">aliases: overwrite<div>        </td></tr>
                <tr><td>gs_access_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>GS access key. If not set then the value of the GS_ACCESS_KEY_ID environment variable is used.</div>        </td></tr>
                <tr><td>gs_secret_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>GS secret key. If not set then the value of the GS_SECRET_ACCESS_KEY environment variable is used.</div>        </td></tr>
                <tr><td>headers<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>{}</td>
        <td></td>
        <td><div>Headers to attach to object.</div>        </td></tr>
                <tr><td>mode<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>get</li><li>put</li><li>get_url</li><li>get_str</li><li>delete</li><li>create</li></ul></td>
        <td><div>Switches the module behaviour between upload, download, get_url (return download url) , get_str (download object as string), create (bucket) and delete (bucket).</div>        </td></tr>
                <tr><td>object<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Keyname of the object inside the bucket. Can be also be used to create "virtual directories" (see examples).</div>        </td></tr>
                <tr><td>permission<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>private</td>
        <td></td>
        <td><div>This option let's the user set the canned permissions on the object/bucket that are created. The permissions that can be set are 'private', 'public-read', 'authenticated-read'.</div>        </td></tr>
                <tr><td>src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The source file path when performing a PUT operation.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Upload some content
      gc_storage:
        bucket: mybucket
        object: key.txt
        src: /usr/local/myfile.txt
        mode: put
        permission: public-read
    
    - name: Upload some headers
      gc_storage:
        bucket: mybucket
        object: key.txt
        src: /usr/local/myfile.txt
        headers: '{"Content-Encoding": "gzip"}'
    
    - name: Download some content
      gc_storage:
        bucket: mybucket
        object: key.txt
        dest: /usr/local/myfile.txt
        mode: get
    
    - name: Download an object as a string to use else where in your playbook
      gc_storage:
        bucket: mybucket
        object: key.txt
        mode: get_str
    
    - name: Create an empty bucket
      gc_storage:
        bucket: mybucket
        mode: create
    
    - name: Create a bucket with key as directory
      gc_storage:
        bucket: mybucket
        object: /my/directory/path
        mode: create
    
    - name: Delete a bucket and all contents
      gc_storage:
        bucket: mybucket
        mode: delete





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
