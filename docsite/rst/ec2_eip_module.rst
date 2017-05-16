.. _ec2_eip:


ec2_eip - associate an EC2 elastic IP with an instance.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

This module associates AWS EC2 elastic IP addresses with instances

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
    <td>ec2_url</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Must be specified if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used</td>
    </tr>
            <tr>
    <td>in_vpc</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>allocate an EIP inside a VPC or not (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>instance_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The EC2 instance id</td>
    </tr>
            <tr>
    <td>profile</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>uses a boto profile. Only works with boto &gt;= 2.24.0 (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>public_ip</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The elastic IP address to associate with the instance.If absent, allocate a new address</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the EC2 region to use</td>
    </tr>
            <tr>
    <td>reuse_existing_ip_allowed</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Reuse an EIP that is not associated to an instance (when available), instead of allocating a new one. (added in Ansible 1.6)</td>
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
        <td>If present, associate the IP with the instance.If absent, disassociate the IP with the instance.</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>wait_timeout</td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td>how long to wait in seconds for newly provisioned EIPs to become available (added in Ansible 1.7)</td>
    </tr>
        </table>


.. note:: Requires boto


Examples
--------

.. raw:: html

    <br/>


::

    - name: associate an elastic IP with an instance
      ec2_eip: instance_id=i-1212f003 ip=93.184.216.119
    
    - name: disassociate an elastic IP from an instance
      ec2_eip: instance_id=i-1212f003 ip=93.184.216.119 state=absent
    
    - name: allocate a new elastic IP and associate it with an instance
      ec2_eip: instance_id=i-1212f003
    
    - name: allocate a new elastic IP without associating it to anything
      ec2_eip:
      register: eip
    - name: output the IP
      debug: msg="Allocated IP is {{ eip.public_ip }}"
    
    - name: provision new instances with ec2
      ec2: keypair=mykey instance_type=c1.medium image=emi-40603AD1 wait=yes group=webserver count=3
      register: ec2
    - name: associate new elastic IPs with each of the instances
      ec2_eip: "instance_id={{ item }}"
      with_items: ec2.instance_ids
    
    - name: allocate a new elastic IP inside a VPC in us-west-2
      ec2_eip: region=us-west-2 in_vpc=yes
      register: eip
    - name: output the IP
      debug: msg="Allocated IP inside a VPC is {{ eip.public_ip }}"

.. note:: This module will return ``public_ip`` on success, which will contain the public IP address associated with the instance.
.. note:: There may be a delay between the time the Elastic IP is assigned and when the cloud instance is reachable via the new address. Use wait_for and pause to delay further playbook execution until the instance is reachable, if necessary.
.. note:: The following environment variables can be used ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY`` or ``AWS_ACCESS_KEY_ID``, ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY`` or ``AWS_SECRET_ACCESS_KEY``, ``AWS_REGION`` or ``EC2_REGION``, ``AWS_SECURITY_TOKEN``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

