.. _cloudformation:


cloudformation - Create or delete an AWS CloudFormation stack
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Launches or updates an AWS CloudFormation stack and waits for it complete.


Requirements (on host that executes module)
-------------------------------------------

  * boto
  * botocore>=1.4.57
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
                <tr><td>disable_rollback<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>false</td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td><div>If a stacks fails to form, rollback will remove the stack</div>        </td></tr>
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>notification_arns<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The Simple Notification Service (SNS) topic ARNs to publish stack related events.</div>        </td></tr>
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
                <tr><td>role_arn<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The role that AWS CloudFormation assumes to create the stack. See the AWS CloudFormation Service Role docs <a href='http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-servicerole.html'>http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/using-iam-servicerole.html</a></div>        </td></tr>
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>stack_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>name of the cloudformation stack</div>        </td></tr>
                <tr><td>stack_policy<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the path of the cloudformation stack policy. A policy cannot be removed once placed, but it can be modified. (for instance, [allow all updates](http://docs.aws.amazon.com/AWSCloudFormation/latest/UserGuide/protect-stack-resources.html#d0e9051)</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>If state is "present", stack will be created.  If state is "present" and if stack exists and template has changed, it will be updated. If state is "absent", stack will be removed.</div>        </td></tr>
                <tr><td>tags<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dictionary of tags to associate with stack and its resources during stack creation. Can be updated later, updating tags removes previous entries.</div>        </td></tr>
                <tr><td>template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The local path of the cloudformation template.</div><div>This must be the full path to the file, relative to the working directory. If using roles this may look like "roles/cloudformation/files/cloudformation-example.json".</div><div>If 'state' is 'present' and the stack does not exist yet, either 'template' or 'template_url' must be specified (but not both). If 'state' is present, the stack does exist, and neither 'template' nor 'template_url' are specified, the previous template will be reused.</div>        </td></tr>
                <tr><td>template_format<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>json</td>
        <td><ul><li>json</li><li>yaml</li></ul></td>
        <td><div>(deprecated) For local templates, allows specification of json or yaml format. Templates are now passed raw to CloudFormation regardless of format. This parameter is ignored since Ansible 2.3.</div>        </td></tr>
                <tr><td>template_parameters<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a list of hashes of all the template variables for the stack</div>        </td></tr>
                <tr><td>template_url<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Location of file containing the template body. The URL must point to a template (max size 307,200 bytes) located in an S3 bucket in the same region as the stack.</div><div>If 'state' is 'present' and the stack does not exist yet, either 'template' or 'template_url' must be specified (but not both). If 'state' is present, the stack does exist, and neither 'template' nor 'template_url' are specified, the previous template will be reused.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div>        </td></tr>
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
        stack_name: "ansible-cloudformation"
        state: present
        region: us-east-1
        disable_rollback: true
        template_url: https://s3.amazonaws.com/my-bucket/cloudformation.template
      args:
        template_parameters:
          KeyName: jmartin
          DiskType: ephemeral
          InstanceType: m1.small
          ClusterSize: 3
        tags:
          Stack: ansible-cloudformation
    
    # Use a template from a URL, and assume a role to execute
    - name: launch ansible cloudformation example with role assumption
      cloudformation:
        stack_name: "ansible-cloudformation"
        state: present
        region: us-east-1
        disable_rollback: true
        template_url: https://s3.amazonaws.com/my-bucket/cloudformation.template
        role_arn: 'arn:aws:iam::123456789012:role/cloudformation-iam-role'
      args:
        template_parameters:
          KeyName: jmartin
          DiskType: ephemeral
          InstanceType: m1.small
          ClusterSize: 3
        tags:
          Stack: ansible-cloudformation

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
        <td> stack_resources </td>
        <td> AWS stack resources and their status. List of dictionaries, one dict per resource. </td>
        <td align=center>  </td>
        <td align=center> list </td>
        <td align=center> [{'status': 'UPDATE_COMPLETE', 'physical_resource_id': 'cloudformation2-CFTestSg-16UQ4CYQ57O9F', 'logical_resource_id': 'CFTestSg', 'status_reason': None, 'last_updated_time': '2016-10-11T19:40:14.979000+00:00', 'resource_type': 'AWS::EC2::SecurityGroup'}] </td>
    </tr>
            <tr>
        <td> stack_outputs </td>
        <td> A key:value dictionary of all the stack outputs currently defined. If there are no stack outputs, it is an empty dictionary. </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'MySg': 'AnsibleModuleTestYAML-CFTestSg-C8UVS567B6NS'} </td>
    </tr>
            <tr>
        <td> events </td>
        <td> Most recent events in Cloudformation's event log. This may be from a previous run in some cases. </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['StackEvent AWS::CloudFormation::Stack stackname UPDATE_COMPLETE', 'StackEvent AWS::CloudFormation::Stack stackname UPDATE_COMPLETE_CLEANUP_IN_PROGRESS'] </td>
    </tr>
            <tr>
        <td> log </td>
        <td> Debugging logs. Useful when modifying or finding an error. </td>
        <td align=center> always </td>
        <td align=center> list </td>
        <td align=center> ['updating stack'] </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - As of version 2.3, migrated to boto3 to enable new features. To match existing behavior, YAML parsing is done in the module, not given to AWS as YAML. This will change (in fact, it may change before 2.3 is out).
    - If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
    - Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
    - ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is supported mainly by the community and is curated by core committers.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
