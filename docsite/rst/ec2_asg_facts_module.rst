.. _ec2_asg_facts:


ec2_asg_facts - Gather facts about ec2 Auto Scaling Groups (ASGs) in AWS
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Gather facts about ec2 Auto Scaling Groups (ASGs) in AWS


Requirements (on host that executes module)
-------------------------------------------

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
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The prefix or name of the auto scaling group(s) you are searching for.</div><div>Note: This is a regular expression match with implicit '^' (beginning of string). Append '$' for a complete name match.</div></td></tr>
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
    <td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A dictionary/hash of tags in the format { tag1_name: 'tag1_value', tag2_name: 'tag2_value' } to match against the auto scaling group(s) you are searching for.</div></td></tr>
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
    
    # Find all groups
    - ec2_asg_facts:
      register: asgs
    
    # Find a group with matching name/prefix
    - ec2_asg_facts:
        name: public-webserver-asg
      register: asgs
    
    # Find a group with matching tags
    - ec2_asg_facts:
        tags:
          project: webapp
          env: production
      register: asgs
    
    # Find a group with matching name/prefix and tags
    - ec2_asg_facts:
        name: myproject
        tags:
          env: production
      register: asgs
    
    # Fail if no groups are found
    - ec2_asg_facts:
        name: public-webserver-asg
      register: asgs
      failed_when: "{{ asgs.results | length == 0 }}"
    
    # Fail if more than 1 group is found
    - ec2_asg_facts:
        name: public-webserver-asg
      register: asgs
      failed_when: "{{ asgs.results | length > 1 }}"

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
        <td> status </td>
        <td> The current state of the group when DeleteAutoScalingGroup is in progress. </td>
        <td align=center> success </td>
        <td align=center> str </td>
        <td align=center> None </td>
    </tr>
            <tr>
        <td> default_cooldown </td>
        <td> The default cooldown time in seconds. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 300 </td>
    </tr>
            <tr>
        <td> tags </td>
        <td> List of tags for the ASG, and whether or not each tag propagates to instances at launch. </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> [{'propagate_at_launch': 'true', 'key': 'Name', 'value': 'public-webapp-production-1', 'resource_type': 'auto-scaling-group', 'resource_id': 'public-webapp-production-1'}, {'propagate_at_launch': 'true', 'key': 'env', 'value': 'production', 'resource_type': 'auto-scaling-group', 'resource_id': 'public-webapp-production-1'}] </td>
    </tr>
            <tr>
        <td> load_balancer_names </td>
        <td> List of load balancers names attached to the ASG. </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> ['elb-webapp-prod'] </td>
    </tr>
            <tr>
        <td> min_size </td>
        <td> Minimum size of group </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 1 </td>
    </tr>
            <tr>
        <td> instances </td>
        <td> List of EC2 instances and their status as it relates to the ASG. </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> [{'instance_id': 'i-es22ad25', 'lifecycle_state': 'InService', 'health_status': 'Healthy', 'protected_from_scale_in': 'false', 'availability_zone': 'us-west-2a', 'launch_configuration_name': 'public-webapp-production-1'}] </td>
    </tr>
            <tr>
        <td> health_check_period </td>
        <td> Length of time in seconds after a new EC2 instance comes into service that Auto Scaling starts checking its health. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 30 </td>
    </tr>
            <tr>
        <td> created_time </td>
        <td> The date and time this ASG was created, in ISO 8601 format. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2015-11-25T00:05:36.309Z </td>
    </tr>
            <tr>
        <td> max_size </td>
        <td> Maximum size of group </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 3 </td>
    </tr>
            <tr>
        <td> availability_zones </td>
        <td> List of Availability Zones that are enabled for this ASG. </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> ['us-west-2a', 'us-west-2b', 'us-west-2a'] </td>
    </tr>
            <tr>
        <td> launch_configuration_name </td>
        <td> Name of launch configuration associated with the ASG. </td>
        <td align=center> success </td>
        <td align=center> str </td>
        <td align=center> public-webapp-production-1 </td>
    </tr>
            <tr>
        <td> auto_scaling_group_arn </td>
        <td> The Amazon Resource Name of the ASG </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> arn:aws:autoscaling:us-west-2:1234567890:autoScalingGroup:10787c52-0bcb-427d-82ba-c8e4b008ed2e:autoScalingGroupName/public-webapp-production-1 </td>
    </tr>
            <tr>
        <td> new_instances_protected_from_scale_in </td>
        <td> Whether or not new instances a protected from automatic scaling in. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> false </td>
    </tr>
            <tr>
        <td> termination_policies </td>
        <td> A list of termination policies for the group. </td>
        <td align=center> success </td>
        <td align=center> str </td>
        <td align=center> ['Default'] </td>
    </tr>
            <tr>
        <td> desired_capacity </td>
        <td> The number of EC2 instances that should be running in this group. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 3 </td>
    </tr>
            <tr>
        <td> health_check_type </td>
        <td> The service you want the health status from, one of "EC2" or "ELB". </td>
        <td align=center> success </td>
        <td align=center> str </td>
        <td align=center> ELB </td>
    </tr>
            <tr>
        <td> auto_scaling_group_name </td>
        <td> Name of autoscaling group </td>
        <td align=center> success </td>
        <td align=center> str </td>
        <td align=center> public-webapp-production-1 </td>
    </tr>
            <tr>
        <td> placement_group </td>
        <td> Placement group into which instances are launched, if any. </td>
        <td align=center> success </td>
        <td align=center> str </td>
        <td align=center> None </td>
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

