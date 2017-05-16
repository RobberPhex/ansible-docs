.. _cloudformation_facts:


cloudformation_facts - Obtain facts about an AWS CloudFormation stack
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Gets information about an AWS CloudFormation stack


Requirements (on host that executes module)
-------------------------------------------

  * boto
  * boto3 >= 1.0.0
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
    <td>all_facts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Get all stack information for the stack</div></td></tr>
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
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>uses a boto profile. Only works with boto &gt;= 2.24.0</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The AWS region to use. If not specified then the value of the AWS_REGION or EC2_REGION environment variable, if any, is used. See <a href='http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region'>http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region</a></div></br>
        <div style="font-size: small;">aliases: aws_region, ec2_region<div></td></tr>
            <tr>
    <td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
        <div style="font-size: small;">aliases: access_token<div></td></tr>
            <tr>
    <td>stack_events<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Get stack events for the stack</div></td></tr>
            <tr>
    <td>stack_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name or id of the CloudFormation stack</div></td></tr>
            <tr>
    <td>stack_policy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Get stack policy for the stack</div></td></tr>
            <tr>
    <td>stack_resources<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Get stack resources for the stack</div></td></tr>
            <tr>
    <td>stack_template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Get stack template body for the stack</div></td></tr>
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

    # Note: These examples do not set authentication details, see the AWS Guide for details.
    
    # Get summary information about a stack
    - cloudformation_facts:
        stack_name: my-cloudformation-stack
    
    # Facts are published in ansible_facts['cloudformation'][<stack_name>]
    - debug: msg={{ ansible_facts['cloudformation']['my-cloudformation-stack'] }}
    
    # Get all stack information about a stack
    - cloudformation_facts:
        stack_name: my-cloudformation-stack
        all_facts: true
    
    # Get stack resource and stack policy information about a stack
    - cloudformation_facts:
        stack_name: my-cloudformation-stack
        stack_resources: true
        stack_policy: true
    
    # Example dictionary outputs for stack_outputs, stack_parameters and stack_resources:
    "stack_outputs": {
        "ApplicationDatabaseName": "dazvlpr01xj55a.ap-southeast-2.rds.amazonaws.com",
        ...
    },
    "stack_parameters": {
        "DatabaseEngine": "mysql",
        "DatabasePassword": "****",
        ...
    },
    "stack_resources": {
        "AutoscalingGroup": "dev-someapp-AutoscalingGroup-1SKEXXBCAN0S7",
        "AutoscalingSecurityGroup": "sg-abcd1234",
        "ApplicationDatabase": "dazvlpr01xj55a",
        "EcsTaskDefinition": "arn:aws:ecs:ap-southeast-2:123456789:task-definition/dev-someapp-EcsTaskDefinition-1F2VM9QB0I7K9:1"
        ...
    }

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
        <td> stack_description </td>
        <td> Summary facts about the stack </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stack_template </td>
        <td> Describes the stack template for the stack </td>
        <td align=center> only if all_facts or stack_template is true </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stack_policy </td>
        <td> Describes the stack policy for the stack </td>
        <td align=center> only if all_facts or stack_policy is true </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stack_outputs </td>
        <td> Dictionary of stack outputs keyed by the value of each output 'OutputKey' parameter and corresponding value of each output 'OutputValue' parameter </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stack_events </td>
        <td> All stack events for the stack </td>
        <td align=center> only if all_facts or stack_events is true </td>
        <td align=center> list of events </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stack_parameters </td>
        <td> Dictionary of stack parameters keyed by the value of each parameter 'ParameterKey' parameter and corresponding value of each parameter 'ParameterValue' parameter </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stack_resources </td>
        <td> Dictionary of stack resources keyed by the value of each resource 'LogicalResourceId' parameter and corresponding value of each resource 'PhysicalResourceId' parameter </td>
        <td align=center> only if all_facts or stack_resourses is true </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> stack_resource_list </td>
        <td> Describes stack resources for the stack </td>
        <td align=center> only if all_facts or stack_resourses is true </td>
        <td align=center> list of resources </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

