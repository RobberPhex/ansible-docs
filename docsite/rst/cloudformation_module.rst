.. _cloudformation:


cloudformation - Create or delete an AWS CloudFormation stack
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Launches an AWS CloudFormation stack and waits for it complete.


Requirements
------------

  * python >= 2.6
  * boto


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
    <td>disable_rollback<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>false</td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>If a stacks fails to form, rollback will remove the stack</div></td></tr>
            <tr>
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>notification_arns<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The Simple Notification Service (SNS) topic ARNs to publish stack related events.</div></td></tr>
            <tr>
    <td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>uses a boto profile. Only works with boto &gt;= 2.24.0</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The AWS region to use. If not specified then the value of the AWS_REGION or EC2_REGION environment variable, if any, is used.</div></br>
        <div style="font-size: small;">aliases: aws_region, ec2_region<div></td></tr>
            <tr>
    <td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
        <div style="font-size: small;">aliases: access_token<div></td></tr>
            <tr>
    <td>stack_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>name of the cloudformation stack</div></td></tr>
            <tr>
    <td>stack_policy<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the path of the cloudformation stack policy</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If state is "present", stack will be created.  If state is "present" and if stack exists and template has changed, it will be updated. If state is "absent", stack will be removed.</div></td></tr>
            <tr>
    <td>tags<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Dictionary of tags to associate with stack and it's resources during stack creation. Cannot be updated later. Requires at least Boto version 2.6.0.</div></td></tr>
            <tr>
    <td>template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The local path of the cloudformation template. This parameter is mutually exclusive with 'template_url'. Either one of them is required if "state" parameter is "present" Must give full path to the file, relative to the working directory. If using roles this may look like "roles/cloudformation/files/cloudformation-example.json"</div></td></tr>
            <tr>
    <td>template_format<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>json</td>
        <td><ul><li>json</li><li>yaml</li></ul></td>
        <td><div>For local templates, allows specification of json or yaml format</div></td></tr>
            <tr>
    <td>template_parameters<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a list of hashes of all the template variables for the stack</div></td></tr>
            <tr>
    <td>template_url<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Location of file containing the template body. The URL must point to a template (max size 307,200 bytes) located in an S3 bucket in the same region as the stack. This parameter is mutually exclusive with 'template'. Either one of them is required if "state" parameter is "present"</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Basic task example
    - name: launch ansible cloudformation example
      cloudformation:
        stack_name: "ansible-cloudformation" 
        state: "present"
        region: "us-east-1" 
        disable_rollback: true
        template: "files/cloudformation-example.json"
        template_parameters:
          KeyName: "jmartin"
          DiskType: "ephemeral"
          InstanceType: "m1.small"
          ClusterSize: 3
        tags:
          Stack: "ansible-cloudformation"
    
    # Basic role example
    - name: launch ansible cloudformation example
      cloudformation:
        stack_name: "ansible-cloudformation" 
        state: "present"
        region: "us-east-1" 
        disable_rollback: true
        template: "roles/cloudformation/files/cloudformation-example.json"
        template_parameters:
          KeyName: "jmartin"
          DiskType: "ephemeral"
          InstanceType: "m1.small"
          ClusterSize: 3
        tags:
          Stack: "ansible-cloudformation"
    
    # Removal example
    - name: tear down old deployment
      cloudformation:
        stack_name: "ansible-cloudformation-old"
        state: "absent"
    
    # Use a template from a URL
    - name: launch ansible cloudformation example
      cloudformation:
        stack_name="ansible-cloudformation" state=present
        region=us-east-1 disable_rollback=true
        template_url=https://s3.amazonaws.com/my-bucket/cloudformation.template
      args:
        template_parameters:
          KeyName: jmartin
          DiskType: ephemeral
          InstanceType: m1.small
          ClusterSize: 3
        tags:
          Stack: ansible-cloudformation


Notes
-----

.. note:: If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

