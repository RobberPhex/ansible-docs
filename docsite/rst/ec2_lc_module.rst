.. _ec2_lc:


ec2_lc - Create or delete AWS Autoscaling Launch Configurations
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Can create or delete AwS Autoscaling Configurations
Works with the ec2_asg module to manage Autoscaling Groups

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
    <td>assign_public_ip</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Used for Auto Scaling groups that launch instances into an Amazon Virtual Private Cloud. Specifies whether to assign a public IP address to each instance launched in a Amazon VPC. (added in Ansible 1.8)</td>
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
    <td>ebs_optimized</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Specifies whether the instance is optimized for EBS I/O (true) or not (false). (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>ec2_url</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Must be specified if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used</td>
    </tr>
            <tr>
    <td>image_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The AMI unique identifier to be used for the group</td>
    </tr>
            <tr>
    <td>instance_monitoring</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>whether instances in group are launched with detailed monitoring.</td>
    </tr>
            <tr>
    <td>instance_profile_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The name or the Amazon Resource Name (ARN) of the instance profile associated with the IAM role for the instances. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>instance_type</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>instance type to use for the instance</td>
    </tr>
            <tr>
    <td>kernel_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Kernel id for the EC2 instance</td>
    </tr>
            <tr>
    <td>key_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The SSH key name to be used for access to managed instances</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Unique name for configuration</td>
    </tr>
            <tr>
    <td>profile</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>uses a boto profile. Only works with boto &gt;= 2.24.0 (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>ramdisk_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A RAM disk id for the instances. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The AWS region to use. If not specified then the value of the EC2_REGION environment variable, if any, is used.</td>
    </tr>
            <tr>
    <td>security_groups</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A list of security groups into which instances should be found</td>
    </tr>
            <tr>
    <td>security_token</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>security token to authenticate against AWS (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>spot_price</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The spot price you are bidding. Only applies for an autoscaling group with spot instances.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>register or deregister the instance</td>
    </tr>
            <tr>
    <td>user_data</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>opaque blob of data which is made available to the ec2 instance</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>volumes</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>a list of volume dicts, each containing device name and optionally ephemeral id or snapshot id. Size and type (and number of iops for io device type) must be specified for a new volume or a root volume, and may be passed for a snapshot volume. For any volume, a volume size less than 1 will be interpreted as a request not to create the volume.</td>
    </tr>
        </table>


.. note:: Requires boto


Examples
--------

.. raw:: html

    <br/>


::

    - ec2_lc:
        name: special
        image_id: ami-XXX
        key_name: default
        security_groups: ['group', 'group2' ]
        instance_type: t1.micro
    

.. note:: Amazon ASG Autoscaling Launch Configurations are immutable once created, so modifying the configuration after it is changed will not modify the launch configuration on AWS. You must create a new config and assign it to the ASG instead.
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

