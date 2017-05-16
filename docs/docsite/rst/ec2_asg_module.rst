.. _ec2_asg:


ec2_asg - Create or delete AWS Autoscaling Groups
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Can create or delete AWS Autoscaling Groups
* Works with the ec2_lc module to manage Launch Configurations


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
                <tr><td>availability_zones<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of availability zone names in which to create the group.  Defaults to all the availability zones in the region if vpc_zone_identifier is not set.</div>        </td></tr>
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
                <tr><td>default_cooldown<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>300 seconds</td>
        <td></td>
        <td><div>The number of seconds after a scaling activity completes before another can begin.</div>        </td></tr>
                <tr><td>desired_capacity<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Desired number of instances in group, if unspecified then the current group value will be used.</div>        </td></tr>
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>health_check_period<br/><div style="font-size: small;"> (added in 1.7)</div></td>
    <td>no</td>
    <td>500 seconds</td>
        <td></td>
        <td><div>Length of time in seconds after a new EC2 instance comes into service that Auto Scaling starts checking its health.</div>        </td></tr>
                <tr><td>health_check_type<br/><div style="font-size: small;"> (added in 1.7)</div></td>
    <td>no</td>
    <td>EC2</td>
        <td><ul><li>EC2</li><li>ELB</li></ul></td>
        <td><div>The service you want the health status from, Amazon EC2 or Elastic Load Balancer.</div>        </td></tr>
                <tr><td>launch_config_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the Launch configuration to use for the group. See the ec2_lc module for managing these.</div>        </td></tr>
                <tr><td>lc_check<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Check to make sure instances that are being replaced with replace_instances do not already have the current launch_config.</div>        </td></tr>
                <tr><td>load_balancers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of ELB names to use for the group</div>        </td></tr>
                <tr><td>max_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Maximum number of instances in group, if unspecified then the current group value will be used.</div>        </td></tr>
                <tr><td>min_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Minimum number of instances in group, if unspecified then the current group value will be used.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Unique name for group to be created or deleted</div>        </td></tr>
                <tr><td>notification_topic<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A SNS topic ARN to send auto scaling notifications to.</div>        </td></tr>
                <tr><td>notification_types<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>[u'autoscaling:EC2_INSTANCE_LAUNCH', u'autoscaling:EC2_INSTANCE_LAUNCH_ERROR', u'autoscaling:EC2_INSTANCE_TERMINATE', u'autoscaling:EC2_INSTANCE_TERMINATE_ERROR']</td>
        <td></td>
        <td><div>A list of auto scaling events to trigger notifications on.</div>        </td></tr>
                <tr><td>placement_group<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Physical location of your cluster placement group created in Amazon EC2.</div>        </td></tr>
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
                <tr><td>replace_all_instances<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>In a rolling fashion, replace all instances with an old launch configuration with one from the current launch configuration.</div>        </td></tr>
                <tr><td>replace_batch_size<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>1</td>
        <td></td>
        <td><div>Number of instances you'd like to replace at a time.  Used with replace_all_instances.</div>        </td></tr>
                <tr><td>replace_instances<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>List of instance_ids belonging to the named ASG that you would like to terminate and be replaced with instances matching the current launch configuration.</div>        </td></tr>
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
        <td><div>register or deregister the instance</div>        </td></tr>
                <tr><td>suspend_processes<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>Launch</li><li>Terminate</li><li>HealthCheck</li><li>ReplaceUnhealthy</li><li>AZRebalance</li><li>AlarmNotification</li><li>ScheduledActions</li><li>AddToLoadBalancer</li></ul></td>
        <td><div>A list of scaling processes to suspend.</div>        </td></tr>
                <tr><td>tags<br/><div style="font-size: small;"> (added in 1.7)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A list of tags to add to the Auto Scale Group. Optional key is 'propagate_at_launch', which defaults to true.</div>        </td></tr>
                <tr><td>termination_policies<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>Default</td>
        <td><ul><li>OldestInstance</li><li>NewestInstance</li><li>OldestLaunchConfiguration</li><li>ClosestToNextInstanceHour</li><li>Default</li></ul></td>
        <td><div>An ordered list of criteria used for selecting instances to be removed from the Auto Scaling group when reducing capacity.</div><div>For 'Default', when used to create a new autoscaling group, the "Default"i value is used. When used to change an existent autoscaling group, the current termination policies are maintained.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div>        </td></tr>
                <tr><td>vpc_zone_identifier<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>List of VPC subnets to use</div>        </td></tr>
                <tr><td>wait_for_instances<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Wait for the ASG instances to be in a ready state before exiting.  If instances are behind an ELB, it will wait until the ELB determines all instances have a lifecycle_state of  "InService" and  a health_status of "Healthy".</div>        </td></tr>
                <tr><td>wait_timeout<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>300</td>
        <td></td>
        <td><div>how long before wait instances to become viable when replaced.  Used in conjunction with instance_ids option.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Basic configuration
    
    - ec2_asg:
        name: special
        load_balancers: [ 'lb1', 'lb2' ]
        availability_zones: [ 'eu-west-1a', 'eu-west-1b' ]
        launch_config_name: 'lc-1'
        min_size: 1
        max_size: 10
        desired_capacity: 5
        vpc_zone_identifier: [ 'subnet-abcd1234', 'subnet-1a2b3c4d' ]
        tags:
          - environment: production
            propagate_at_launch: no
    
    # Rolling ASG Updates
    
    # Below is an example of how to assign a new launch config to an ASG and terminate old instances.
    #
    # All instances in "myasg" that do not have the launch configuration named "my_new_lc" will be terminated in
    # a rolling fashion with instances using the current launch configuration, "my_new_lc".
    #
    # This could also be considered a rolling deploy of a pre-baked AMI.
    #
    # If this is a newly created group, the instances will not be replaced since all instances
    # will have the current launch configuration.
    
    - name: create launch config
      ec2_lc:
        name: my_new_lc
        image_id: ami-lkajsf
        key_name: mykey
        region: us-east-1
        security_groups: sg-23423
        instance_type: m1.small
        assign_public_ip: yes
    
    - ec2_asg:
        name: myasg
        launch_config_name: my_new_lc
        health_check_period: 60
        health_check_type: ELB
        replace_all_instances: yes
        min_size: 5
        max_size: 5
        desired_capacity: 5
        region: us-east-1
    
    # To only replace a couple of instances instead of all of them, supply a list
    # to "replace_instances":
    
    - ec2_asg:
        name: myasg
        launch_config_name: my_new_lc
        health_check_period: 60
        health_check_type: ELB
        replace_instances:
        - i-b345231
        - i-24c2931
        min_size: 5
        max_size: 5
        desired_capacity: 5
        region: us-east-1


Notes
-----

.. note::
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
