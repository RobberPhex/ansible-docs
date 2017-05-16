.. _ec2_group:


ec2_group - maintain an ec2 VPC security group.
+++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3

maintains ec2 security groups. This module has a dependency on python-boto >= 2.5

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
    <td>description</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Description of the security group.</td>
    </tr>
            <tr>
    <td>ec2_url</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Must be specified if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of the security group.</td>
    </tr>
            <tr>
    <td>profile</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>uses a boto profile. Only works with boto &gt;= 2.24.0 (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>purge_rules</td>
    <td>no</td>
    <td>true</td>
        <td><ul></ul></td>
        <td>Purge existing rules on security group that are not found in rules (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>purge_rules_egress</td>
    <td>no</td>
    <td>true</td>
        <td><ul></ul></td>
        <td>Purge existing rules_egress on security group that are not found in rules_egress (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the EC2 region to use</td>
    </tr>
            <tr>
    <td>rules</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>List of firewall inbound rules to enforce in this group (see example).</td>
    </tr>
            <tr>
    <td>rules_egress</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>List of firewall outbound rules to enforce in this group (see example). (added in Ansible 1.6)</td>
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
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Create or delete a security group (added in Ansible 1.4)</td>
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
        <td>ID of the VPC to create the group in.</td>
    </tr>
        </table>


.. note:: Requires boto


Examples
--------

.. raw:: html

    <br/>


::

    - name: example ec2 group
      ec2_group:
        name: example
        description: an example EC2 group
        vpc_id: 12345
        region: eu-west-1a
        aws_secret_key: SECRET
        aws_access_key: ACCESS
        rules:
          - proto: tcp
            from_port: 80
            to_port: 80
            cidr_ip: 0.0.0.0/0
          - proto: tcp
            from_port: 22
            to_port: 22
            cidr_ip: 10.0.0.0/8
          - proto: udp
            from_port: 10050
            to_port: 10050
            cidr_ip: 10.0.0.0/8
          - proto: udp
            from_port: 10051
            to_port: 10051
            group_id: sg-12345678
          - proto: all
            # the containing group name may be specified here
            group_name: example
        rules_egress:
          - proto: tcp
            from_port: 80
            to_port: 80
            cidr_ip: 0.0.0.0/0
            group_name: example-other
            # description to use if example-other needs to be created
            group_desc: other example EC2 group

.. note:: If a rule declares a group_name and that group doesn't exist, it will be automatically created. In that case, group_desc should be provided as well. The module will refuse to create a depended-on group without a description.
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

