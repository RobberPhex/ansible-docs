.. _lambda:


lambda - Manage AWS Lambda functions
++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Allows for the management of Lambda functions.


Requirements (on host that executes module)
-------------------------------------------

  * boto
  * boto3
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
                <tr><td>aws_access_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS access key. If not set then the value of the AWS_ACCESS_KEY_ID, AWS_ACCESS_KEY or EC2_ACCESS_KEY environment variable is used.</div></br>
    <div style="font-size: small;">aliases: ec2_access_key, access_key<div>        </td></tr>
                <tr><td>aws_secret_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS secret key. If not set then the value of the AWS_SECRET_ACCESS_KEY, AWS_SECRET_KEY, or EC2_SECRET_KEY environment variable is used.</div></br>
    <div style="font-size: small;">aliases: ec2_secret_key, secret_key<div>        </td></tr>
                <tr><td>dead_letter_arn<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The parent object that contains the target Amazon Resource Name (ARN) of an Amazon SQS queue or Amazon SNS topic.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A short, user-defined function description. Lambda does not use this value. Assign a meaningful description as you see fit.</div>        </td></tr>
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>environment_variables<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A dictionary of environment variables the Lambda function is given.</div></br>
    <div style="font-size: small;">aliases: environment<div>        </td></tr>
                <tr><td>handler<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The function within your code that Lambda calls to begin execution</div>        </td></tr>
                <tr><td>memory_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>128</td>
        <td></td>
        <td><div>The amount of memory, in MB, your Lambda function is given</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name you want to assign to the function you are uploading. Cannot be changed.</div>        </td></tr>
                <tr><td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Uses a boto profile. Only works with boto &gt;= 2.24.0.</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The AWS region to use. If not specified then the value of the AWS_REGION or EC2_REGION environment variable, if any, is used. See <a href='http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region'>http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region</a></div></br>
    <div style="font-size: small;">aliases: aws_region, ec2_region<div>        </td></tr>
                <tr><td>role<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The Amazon Resource Name (ARN) of the IAM role that Lambda assumes when it executes your function to access any other Amazon Web Services (AWS) resources. You may use the bare ARN if the role belongs to the same AWS account.</div>        </td></tr>
                <tr><td>runtime<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The runtime environment for the Lambda function you are uploading. Required when creating a function. Use parameters as described in boto3 docs. Current example runtime environments are nodejs, nodejs4.3, java8 or python2.7</div>        </td></tr>
                <tr><td>s3_bucket<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Amazon S3 bucket name where the .zip file containing your deployment package is stored</div>        </td></tr>
                <tr><td>s3_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The Amazon S3 object (the deployment package) key name you want to upload</div>        </td></tr>
                <tr><td>s3_object_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The Amazon S3 object (the deployment package) version you want to upload.</div>        </td></tr>
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Create or delete Lambda function</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3</td>
        <td></td>
        <td><div>The function execution time at which Lambda should terminate the function.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div>        </td></tr>
                <tr><td>vpc_security_group_ids<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>List of VPC security group IDs to associate with the Lambda function. Required when vpc_subnet_ids is used.</div>        </td></tr>
                <tr><td>vpc_subnet_ids<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>List of subnet IDs to run Lambda function in. Use this option if you need to access resources in your VPC. Leave empty if you don't want to run the function in a VPC.</div>        </td></tr>
                <tr><td>zip_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A .zip file containing your deployment package</div></br>
    <div style="font-size: small;">aliases: src<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create Lambda functions
    tasks:
    - name: looped creation
      lambda:
        name: '{{ item.name }}'
        state: present
        zip_file: '{{ item.zip_file }}'
        runtime: 'python2.7'
        role: 'arn:aws:iam::987654321012:role/lambda_basic_execution'
        handler: 'hello_python.my_handler'
        vpc_subnet_ids:
        - subnet-123abcde
        - subnet-edcba321
        vpc_security_group_ids:
        - sg-123abcde
        - sg-edcba321
        environment_variables: '{{ item.env_vars }}'
      with_items:
        - name: HelloWorld
          zip_file: hello-code.zip
          env_vars:
            key1: "first"
            key2: "second"
        - name: ByeBye
          zip_file: bye-code.zip
          env_vars:
            key1: "1"
            key2: "2"
    
    # Basic Lambda function deletion
    tasks:
    - name: Delete Lambda functions HelloWorld and ByeBye
      lambda:
        name: '{{ item }}'
        state: absent
      with_items:
        - HelloWorld
        - ByeBye

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> output </td>
        <td> the data returned by get_function in boto3 </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> {'code': {'repository_type': 'S3', 'location': 'an S3 URL'}, 'configuration': {'description': 'string', 'function_arn': 'string', 'handler': 'string', 'timeout': 123, 'last_modified': 'string', 'role': 'string', 'version': 'string', 'code_sha256': 'string', 'memory_size': 123, 'runtime': 'nodejs', 'code_size': 123, 'function_name': 'string'}} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
    - Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
    - ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
