.. _s3:


s3 - manage objects in S3.
++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module allows the user to manage S3 buckets and the objects within them. Includes support for creating and deleting both objects and buckets, retrieving objects as files or strings and generating download links. This module has a dependency on python-boto.


Requirements
------------

  * boto
  * python >= 2.6


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
    <td>aws_access_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS access key. If not set then the value of the AWS_ACCESS_KEY_ID, AWS_ACCESS_KEY or EC2_ACCESS_KEY environment variable is used.</div></br>
        <div style="font-size: small;">aliases: ec2_access_key, access_key<div></td></tr>
            <tr>
    <td>aws_secret_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS secret key. If not set then the value of the AWS_SECRET_ACCESS_KEY, AWS_SECRET_KEY, or EC2_SECRET_KEY environment variable is used.</div></br>
        <div style="font-size: small;">aliases: ec2_secret_key, secret_key<div></td></tr>
            <tr>
    <td>bucket<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Bucket name.</div></td></tr>
            <tr>
    <td>dest<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The destination file path when downloading an object/key with a GET operation.</div></td></tr>
            <tr>
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>encrypt<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>When set for PUT mode, asks for server-side encryption</div></td></tr>
            <tr>
    <td>expiration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>600</td>
        <td><ul></ul></td>
        <td><div>Time limit (in seconds) for the URL generated and returned by S3/Walrus when performing a mode=put or mode=geturl operation.</div></td></tr>
            <tr>
    <td>headers<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Custom headers for PUT operation, as a dictionary of 'key=value' and 'key=value,key=value'.</div></td></tr>
            <tr>
    <td>marker<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the key to start with when using list mode. Object keys are returned in alphabetical order, starting with key after the marker in order.</div></td></tr>
            <tr>
    <td>max_keys<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>1000</td>
        <td><ul></ul></td>
        <td><div>Max number of results to return in list mode, set this if you want to retrieve fewer than the default 1000 keys.</div></td></tr>
            <tr>
    <td>metadata<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Metadata for PUT operation, as a dictionary of 'key=value' and 'key=value,key=value'.</div></td></tr>
            <tr>
    <td>mode<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>get</li><li>put</li><li>delete</li><li>create</li><li>geturl</li><li>getstr</li><li>delobj</li><li>list</li></ul></td>
        <td><div>Switches the module behaviour between put (upload), get (download), geturl (return download url, Ansible 1.3+), getstr (download object as string (1.3+)), list (list keys, Ansible 2.0+), create (bucket), delete (bucket), and delobj (delete object, Ansible 2.0+).</div></td></tr>
            <tr>
    <td>object<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Keyname of the object inside the bucket. Can be used to create "virtual directories", see examples.</div></td></tr>
            <tr>
    <td>overwrite<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Force overwrite either locally on the filesystem or remotely with the object/key. Used with PUT and GET operations. Boolean or one of [Always, Never, Different], new in 2.0</div></td></tr>
            <tr>
    <td>permission<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>private</td>
        <td><ul></ul></td>
        <td><div>This option let's the user set the canned permissions on the object/bucket that are created. The permissions that can be set are 'private', 'public-read', 'public-read-write', 'authenticated-read'. Multiple permissions can be specified as a list.</div></td></tr>
            <tr>
    <td>prefix<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Limits the response to keys that begin with the specified prefix for list mode</div></td></tr>
            <tr>
    <td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>uses a boto profile. Only works with boto &gt;= 2.24.0</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS region to create the bucket in. If not set then the value of the AWS_REGION and EC2_REGION environment variables are checked, followed by the aws_region and ec2_region settings in the Boto config file.  If none of those are set the region defaults to the S3 Location: US Standard.  Prior to ansible 1.8 this parameter could be specified but had no effect.</div></td></tr>
            <tr>
    <td>retries<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>On recoverable failure, how many times to retry before actually failing.</div></td></tr>
            <tr>
    <td>s3_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>S3 URL endpoint for usage with Eucalypus, fakes3, etc.  Otherwise assumes AWS</div></br>
        <div style="font-size: small;">aliases: S3_URL<div></td></tr>
            <tr>
    <td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
        <div style="font-size: small;">aliases: access_token<div></td></tr>
            <tr>
    <td>src<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The source file path when performing a PUT operation.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div></td></tr>
            <tr>
    <td>version<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Version ID of the object inside the bucket. Can be used to get a specific version of a file if versioning is enabled in the target bucket.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Simple PUT operation
    - s3: bucket=mybucket object=/my/desired/key.txt src=/usr/local/myfile.txt mode=put
    
    # Simple GET operation
    - s3: bucket=mybucket object=/my/desired/key.txt dest=/usr/local/myfile.txt mode=get
    
    # Get a specific version of an object.
    - s3: bucket=mybucket object=/my/desired/key.txt version=48c9ee5131af7a716edc22df9772aa6f dest=/usr/local/myfile.txt mode=get
    
    # PUT/upload with metadata
    - s3: bucket=mybucket object=/my/desired/key.txt src=/usr/local/myfile.txt mode=put metadata='Content-Encoding=gzip,Cache-Control=no-cache'
    
    # PUT/upload with custom headers
    - s3: bucket=mybucket object=/my/desired/key.txt src=/usr/local/myfile.txt mode=put headers=x-amz-grant-full-control=emailAddress=owner@example.com
    
    # List keys simple
    - s3: bucket=mybucket mode=list
    
    # List keys all options
    - s3: bucket=mybucket mode=list prefix=/my/desired/ marker=/my/desired/0023.txt max_keys=472
    
    # Create an empty bucket
    - s3: bucket=mybucket mode=create permission=public-read
    
    # Create a bucket with key as directory, in the EU region
    - s3: bucket=mybucket object=/my/directory/path mode=create region=eu-west-1
    
    # Delete a bucket and all contents
    - s3: bucket=mybucket mode=delete
    
    # GET an object but dont download if the file checksums match. New in 2.0
    - s3: bucket=mybucket object=/my/desired/key.txt dest=/usr/local/myfile.txt mode=get overwrite=different
    
    # Delete an object from a bucket
    - s3: bucket=mybucket object=/my/desired/key.txt mode=delobj


Notes
-----

.. note:: If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

