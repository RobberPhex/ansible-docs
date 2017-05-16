.. _gc_storage:


gc_storage - This module manages objects/buckets in Google Cloud Storage.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

This module allows users to manage their objects/buckets in Google Cloud Storage.  It allows upload and download operations and can set some canned permissions. It also allows retrieval of URLs for objects for use in playbooks, and retrieval of string contents of objects.  This module requires setting the default project in GCS prior to playbook usage.  See https://developers.google.com/storage/docs/reference/v1/apiversion1 for information about setting the default project.

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
    <td>bucket</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Bucket name.</td>
    </tr>
            <tr>
    <td>dest</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The destination file path when downloading an object/key with a GET operation.</td>
    </tr>
            <tr>
    <td>expiration</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Time limit (in seconds) for the URL generated and returned by GCA when performing a mode=put or mode=get_url operation. This url is only avaialbe when public-read is the acl for the object.</td>
    </tr>
            <tr>
    <td>force</td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>Forces an overwrite either locally on the filesystem or remotely with the object/key. Used with PUT and GET operations.</td>
    </tr>
            <tr>
    <td>gcs_access_key</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>GCS access key. If not set then the value of the GCS_ACCESS_KEY environment variable is used.</td>
    </tr>
            <tr>
    <td>gcs_secret_key</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>GCS secret key. If not set then the value of the GCS_SECRET_KEY environment variable is used.</td>
    </tr>
            <tr>
    <td>mode</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>get</li><li>put</li><li>get_url</li><li>get_str</li><li>delete</li><li>create</li></ul></td>
        <td>Switches the module behaviour between upload, download, get_url (return download url) , get_str (download object as string), create (bucket) and delete (bucket).</td>
    </tr>
            <tr>
    <td>object</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Keyname of the object inside the bucket. Can be also be used to create "virtual directories" (see examples).</td>
    </tr>
            <tr>
    <td>permission</td>
    <td>no</td>
    <td>private</td>
        <td><ul></ul></td>
        <td>This option let's the user set the canned permissions on the object/bucket that are created. The permissions that can be set are 'private', 'public-read', 'authenticated-read'.</td>
    </tr>
            <tr>
    <td>src</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The source file path when performing a PUT operation.</td>
    </tr>
        </table>


.. note:: Requires boto 2.9+


Examples
--------

.. raw:: html

    <br/>


::

    # upload some content
    - gc_storage: bucket=mybucket object=key.txt src=/usr/local/myfile.txt mode=put permission=public-read
    
    # download some content
    - gc_storage: bucket=mybucket object=key.txt dest=/usr/local/myfile.txt mode=get
    
    # Download an object as a string to use else where in your playbook
    - gc_storage: bucket=mybucket object=key.txt mode=get_str
    
    # Create an empty bucket
    - gc_storage: bucket=mybucket mode=create
    
    # Create a bucket with key as directory
    - gc_storage: bucket=mybucket object=/my/directory/path mode=create
    
    # Delete a bucket and all contents
    - gc_storage: bucket=mybucket mode=delete



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

