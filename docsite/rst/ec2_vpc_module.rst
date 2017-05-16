.. _ec2_vpc:


ec2_vpc - configure AWS virtual private clouds
++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

Create or terminates AWS virtual private clouds.  This module has a dependency on python-boto.

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
    <td>aws_access_key</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>AWS access key. If not set then the value of the AWS_ACCESS_KEY environment variable is used.</td>
    </tr>
            <tr>
    <td>aws_secret_key</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>AWS secret key. If not set then the value of the AWS_SECRET_KEY environment variable is used.</td>
    </tr>
            <tr>
    <td>cidr_block</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The cidr block representing the VPC, e.g. 10.0.0.0/16</td>
    </tr>
            <tr>
    <td>dns_hostnames</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>toggles the "Enable DNS hostname support for instances" flag</td>
    </tr>
            <tr>
    <td>dns_support</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>toggles the "Enable DNS resolution" flag</td>
    </tr>
            <tr>
    <td>instance_tenancy</td>
    <td>no</td>
    <td>default</td>
        <td><ul><li>default</li><li>dedicated</li></ul></td>
        <td>The supported tenancy options for instances launched into the VPC.</td>
    </tr>
            <tr>
    <td>internet_gateway</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Toggle whether there should be an Internet gateway attached to the VPC</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>region in which the resource exists.</td>
    </tr>
            <tr>
    <td>resource_tags</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>A dictionary array of resource tags of the form: { tag1: value1, tag2: value2 }.  Tags in this list are used in conjunction with CIDR block to uniquely identify a VPC in lieu of vpc_id. Therefore, if CIDR/Tag combination does not exits, a new VPC will be created.  VPC tags not on this list will be ignored. Prior to 1.7, specifying a resource tag was optional. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>route_tables</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A dictionary array of route tables to add of the form: { subnets: [172.22.2.0/24, 172.22.3.0/24,], routes: [{ dest: 0.0.0.0/0, gw: igw},] }. Where the subnets list is those subnets the route table should be associated with, and the routes list is a list of routes to be in the table.  The special keyword for the gw of igw specifies that you should the route should go through the internet gateway attached to the VPC. gw also accepts instance-ids in addition igw. This module is currently unable to affect the "main" route table due to some limitations in boto, so you must explicitly define the associated subnets or they will be attached to the main table implicitly. As of 1.8, if the route_tables parameter is not specified, no existing routes will be modified.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td>present</td>
        <td><ul></ul></td>
        <td>Create or terminate the VPC</td>
    </tr>
            <tr>
    <td>subnets</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A dictionary array of subnets to add of the form: { cidr: ..., az: ... , resource_tags: ... }. Where az is the desired availability zone of the subnet, but it is not required. Tags (i.e.: resource_tags) is also optional and use dictionary form: { "Environment":"Dev", "Tier":"Web", ...}. All VPC subnets not in this list will be removed. As of 1.8, if the subnets parameter is not specified, no existing subnets will be modified.</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>vpc_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A VPC id to terminate when state=absent</td>
    </tr>
            <tr>
    <td>wait</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>wait for the VPC to be in state 'available' before returning</td>
    </tr>
            <tr>
    <td>wait_timeout</td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td>how long before wait gives up, in seconds</td>
    </tr>
        </table>


.. note:: Requires boto


Examples
--------

.. raw:: html

    <br/>


::

    # Note: None of these examples set aws_access_key, aws_secret_key, or region.
    # It is assumed that their matching environment variables are set.
    
    # Basic creation example:
          local_action:
            module: ec2_vpc
            state: present
            cidr_block: 172.23.0.0/16
            resource_tags: { "Environment":"Development" }
            region: us-west-2
    # Full creation example with subnets and optional availability zones.
    # The absence or presence of subnets deletes or creates them respectively.
          local_action:
            module: ec2_vpc
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
          local_action:
            module: ec2_vpc
            state: absent
            vpc_id: vpc-aaaaaaa
            region: us-west-2
    If you have added elements not managed by this module, e.g. instances, NATs, etc then
    the delete will fail until those dependencies are removed.



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

