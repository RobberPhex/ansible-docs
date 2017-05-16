.. _ec2_asg:


ec2_asg - Create or delete AWS Autoscaling Groups
+++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Can create or delete AWS Autoscaling Groups
Works with the ec2_lc module to manage Launch Configurations

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
    <td>availability_zones</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>List of availability zone names in which to create the group.  Defaults to all the availability zones in the region if vpc_zone_identifier is not set.</td>
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
    <td>desired_capacity</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Desired number of instances in group</td>
    </tr>
            <tr>
    <td>ec2_url</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Must be specified if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used</td>
    </tr>
            <tr>
    <td>health_check_period</td>
    <td>no</td>
    <td>500 seconds</td>
        <td><ul></ul></td>
        <td>Length of time in seconds after a new EC2 instance comes into service that Auto Scaling starts checking its health. (added in Ansible 1.7)</td>
    </tr>
            <tr>
    <td>health_check_type</td>
    <td>no</td>
    <td>EC2</td>
        <td><ul><li>EC2</li><li>ELB</li></ul></td>
        <td>The service you want the health status from, Amazon EC2 or Elastic Load Balancer. (added in Ansible 1.7)</td>
    </tr>
            <tr>
    <td>launch_config_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of the Launch configuration to use for the group. See the ec2_lc module for managing these.</td>
    </tr>
            <tr>
    <td>lc_check</td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>Check to make sure instances that are being replaced with replace_instances do not aready have the current launch_config. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>load_balancers</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>List of ELB names to use for the group</td>
    </tr>
            <tr>
    <td>max_size</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Maximum number of instances in group</td>
    </tr>
            <tr>
    <td>min_size</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Minimum number of instances in group</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Unique name for group to be created or deleted</td>
    </tr>
            <tr>
    <td>profile</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>uses a boto profile. Only works with boto &gt;= 2.24.0 (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The AWS region to use. If not specified then the value of the EC2_REGION environment variable, if any, is used.</td>
    </tr>
            <tr>
    <td>replace_all_instances</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>In a rolling fashion, replace all instances with an old launch configuration with one from the current launch configuraiton. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>replace_batch_size</td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td>Number of instances you'd like to replace at a time.  Used with replace_all_instances. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>replace_instances</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>List of instance_ids belonging to the named ASG that you would like to terminate and be replaced with instances matching the current launch configuration. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>security_token</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>security token to authenticate against AWS (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>register or deregister the instance</td>
    </tr>
            <tr>
    <td>tags</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>A list of tags to add to the Auto Scale Group. Optional key is 'propagate_at_launch', which defaults to true. (added in Ansible 1.7)</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>vpc_zone_identifier</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>List of VPC subnets to use</td>
    </tr>
            <tr>
    <td>wait_for_instances</td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>Wait for the ASG instances to be in a ready state before exiting.  If instances are behind an ELB, it will wait until the instances are considered by the ELB. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>wait_timeout</td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td>how long before wait instances to become viable when replaced.  Used in concjunction with instance_ids option. (added in Ansible 1.8)</td>
    </tr>
        </table>


.. note:: Requires boto


Examples
--------

.. raw:: html

    <br/>


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
    
    Below is an example of how to assign a new launch config to an ASG and terminate old instances.  
    
    All instances in "myasg" that do not have the launch configuration named "my_new_lc" will be terminated in 
    a rolling fashion with instances using the current launch configuration, "my_new_lc".
    
    This could also be considered a rolling deploy of a pre-baked AMI.
    
    If this is a newly created group, the instances will not be replaced since all instances
    will have the current launch configuration.
    
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
    
    To only replace a couple of instances instead of all of them, supply a list
    to "replace_instances":
    
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

.. note:: The following environment variables can be used ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY`` or ``AWS_ACCESS_KEY_ID``, ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY`` or ``AWS_SECRET_ACCESS_KEY``, ``AWS_REGION`` or ``EC2_REGION``, ``AWS_SECURITY_TOKEN``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

