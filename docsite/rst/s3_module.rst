.. _s3:


s3 - S3 module putting a file into S3.
++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.1

This module allows the user to dictate the presence of a given file in an S3 bucket. If or once the key (file) exists in the bucket, it returns a time-expired download URL. This module has a dependency on python-boto.

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
    <td>aws_access_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>AWS access key. If not set then the value of the AWS_ACCESS_KEY environment variable is used.</td>
    </tr>
            <tr>
    <td>aws_secret_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>AWS secret key. If not set then the value of the AWS_SECRET_KEY environment variable is used.</td>
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
        <td>The destination file path when downloading an object/key with a GET operation. (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>expiration</td>
    <td>no</td>
    <td>600</td>
        <td><ul></ul></td>
        <td>Time limit (in seconds) for the URL generated and returned by S3/Walrus when performing a mode=put or mode=geturl operation.</td>
    </tr>
            <tr>
    <td>metadata</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Metadata for PUT operation, as a dictionary of 'key=value' and 'key=value,key=value'. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>mode</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Switches the module behaviour between put (upload), get (download), geturl (return download url (Ansible 1.3+), getstr (download object as string (1.3+)), create (bucket) and delete (bucket).</td>
    </tr>
            <tr>
    <td>object</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Keyname of the object inside the bucket. Can be used to create "virtual directories", see examples. (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>overwrite</td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>Force overwrite either locally on the filesystem or remotely with the object/key. Used with PUT and GET operations. (added in Ansible 1.2)</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>AWS region to create the bucket in. If not set then the value of the EC2_REGION and AWS_REGION environment variables are checked, followed by the aws_region and ec2_region settings in the Boto config file.  If none of those are set the region defaults to the S3 Location: US Standard.  Prior to ansible 1.8 this parameter could be specified but had no effect. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>s3_url</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>S3 URL endpoint. If not specified then the S3_URL environment variable is used, if that variable is defined. Ansible tries to guess if fakes3 (https://github.com/jubos/fake-s3) or Eucalyptus Walrus (https://github.com/eucalyptus/eucalyptus/wiki/Walrus) is used and configure connection accordingly. Current heuristic is: everything with scheme fakes3:// is fakes3, everything else not ending with amazonaws.com is Walrus.</td>
    </tr>
            <tr>
    <td>src</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The source file path when performing a PUT operation. (added in Ansible 1.3)</td>
    </tr>
        </table>


.. note:: Requires boto


Examples
--------

.. raw:: html

    <br/>


::

    # Simple PUT operation
    - s3: bucket=mybucket object=/my/desired/key.txt src=/usr/local/myfile.txt mode=put
    # Simple GET operation
    - s3: bucket=mybucket object=/my/desired/key.txt dest=/usr/local/myfile.txt mode=get
    # GET/download and overwrite local file (trust remote)
    - s3: bucket=mybucket object=/my/desired/key.txt dest=/usr/local/myfile.txt mode=get 
    # GET/download and do not overwrite local file (trust remote)
    - s3: bucket=mybucket object=/my/desired/key.txt dest=/usr/local/myfile.txt mode=get force=false
    # PUT/upload and overwrite remote file (trust local)
    - s3: bucket=mybucket object=/my/desired/key.txt src=/usr/local/myfile.txt mode=put
    # PUT/upload with metadata
    - s3: bucket=mybucket object=/my/desired/key.txt src=/usr/local/myfile.txt mode=put metadata='Content-Encoding=gzip'
    # PUT/upload with multiple metadata
    - s3: bucket=mybucket object=/my/desired/key.txt src=/usr/local/myfile.txt mode=put metadata='Content-Encoding=gzip,Cache-Control=no-cache'
    # PUT/upload and do not overwrite remote file (trust local)
    - s3: bucket=mybucket object=/my/desired/key.txt src=/usr/local/myfile.txt mode=put force=false
    # Download an object as a string to use else where in your playbook
    - s3: bucket=mybucket object=/my/desired/key.txt src=/usr/local/myfile.txt mode=getstr
    # Create an empty bucket
    - s3: bucket=mybucket mode=create
    # Create a bucket with key as directory
    - s3: bucket=mybucket object=/my/directory/path mode=create
    # Create an empty bucket in the EU region
    - s3: bucket=mybucket mode=create region=eu-west-1
    # Delete a bucket and all contents
    - s3: bucket=mybucket mode=delete



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

