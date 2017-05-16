.. _ec2_vpc:


ec2_vpc - configure AWS virtual private clouds
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create or terminates AWS virtual private clouds.  This module has a dependency on python-boto.


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
    <td>cidr_block<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The cidr block representing the VPC, e.g. 10.0.0.0/16</div></td></tr>
            <tr>
    <td>dns_hostnames<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>toggles the "Enable DNS hostname support for instances" flag</div></td></tr>
            <tr>
    <td>dns_support<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>toggles the "Enable DNS resolution" flag</div></td></tr>
            <tr>
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>instance_tenancy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>default</td>
        <td><ul><li>default</li><li>dedicated</li></ul></td>
        <td><div>The supported tenancy options for instances launched into the VPC.</div></td></tr>
            <tr>
    <td>internet_gateway<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Toggle whether there should be an Internet gateway attached to the VPC</div></td></tr>
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
    <td>resource_tags<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A dictionary array of resource tags of the form: { tag1: value1, tag2: value2 }.  Tags in this list are used in conjunction with CIDR block to uniquely identify a VPC in lieu of vpc_id. Therefore, if CIDR/Tag combination does not exist, a new VPC will be created.  VPC tags not on this list will be ignored. Prior to 1.7, specifying a resource tag was optional.</div></td></tr>
            <tr>
    <td>route_tables<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A dictionary array of route tables to add of the form: { subnets: [172.22.2.0/24, 172.22.3.0/24,], routes: [{ dest: 0.0.0.0/0, gw: igw},], resource_tags: ... }. Where the subnets list is those subnets the route table should be associated with, and the routes list is a list of routes to be in the table.  The special keyword for the gw of igw specifies that you should the route should go through the internet gateway attached to the VPC. gw also accepts instance-ids in addition igw. resource_tags is optional and uses dictionary form: { "Name": "public", ... }. This module is currently unable to affect the "main" route table due to some limitations in boto, so you must explicitly define the associated subnets or they will be attached to the main table implicitly. As of 1.8, if the route_tables parameter is not specified, no existing routes will be modified.</div></td></tr>
            <tr>
    <td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
        <div style="font-size: small;">aliases: access_token<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Create or terminate the VPC</div></td></tr>
            <tr>
    <td>subnets<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A dictionary array of subnets to add of the form: { cidr: ..., az: ... , resource_tags: ... }. Where az is the desired availability zone of the subnet, but it is not required. Tags (i.e.: resource_tags) is also optional and use dictionary form: { "Environment":"Dev", "Tier":"Web", ...}. All VPC subnets not in this list will be removed as well. As of 1.8, if the subnets parameter is not specified, no existing subnets will be modified.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div></td></tr>
            <tr>
    <td>vpc_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A VPC id to terminate when state=absent</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>wait for the VPC to be in state 'available' before returning</div></td></tr>
            <tr>
    <td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td><div>how long before wait gives up, in seconds</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note: None of these examples set aws_access_key, aws_secret_key, or region.
    # It is assumed that their matching environment variables are set.
    
    # Basic creation example:
          ec2_vpc:
            state: present
            cidr_block: 172.23.0.0/16
            resource_tags: { "Environment":"Development" }
            region: us-west-2
    # Full creation example with subnets and optional availability zones.
    # The absence or presence of subnets deletes or creates them respectively.
          ec2_vpc:
            state: present
            cidr_block: 172.22.0.0/16
            resource_tags: { "Environment":"Development" }
            subnets:
              - cidr: 172.22.1.0/24
                az: us-west-2c
                resource_tags: { "Environment":"Dev", "Tier" : "Web" }
              - cidr: 172.22.2.0/24
                az: us-west-2b
                resource_tags: { "Environment":"Dev", "Tier" : "App" }
              - cidr: 172.22.3.0/24
                az: us-west-2a
                resource_tags: { "Environment":"Dev", "Tier" : "DB" }
            internet_gateway: True
            route_tables:
              - subnets:
                  - 172.22.2.0/24
                  - 172.22.3.0/24
                routes:
                  - dest: 0.0.0.0/0
                    gw: igw
              - subnets:
                  - 172.22.1.0/24
                routes:
                  - dest: 0.0.0.0/0
                    gw: igw
            region: us-west-2
          register: vpc
    
    # Removal of a VPC by id
          ec2_vpc:
            state: absent
            vpc_id: vpc-aaaaaaa
            region: us-west-2
    If you have added elements not managed by this module, e.g. instances, NATs, etc then
    the delete will fail until those dependencies are removed.


Notes
-----

.. note:: If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

