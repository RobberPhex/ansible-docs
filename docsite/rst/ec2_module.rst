.. _ec2:


ec2 - create, terminate, start or stop an instance in ec2
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Creates or terminates ec2 instances.

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
        <td>when provisioning within vpc, assign a public IP address. Boto library must be 2.13.0+ (added in Ansible 1.5)</td>
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
    <td>count</td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td>number of instances to launch</td>
    </tr>
            <tr>
    <td>count_tag</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Used with 'exact_count' to determine how many nodes based on a specific tag criteria should be running.  This can be expressed in multiple ways and is shown in the EXAMPLES section.  For instance, one can request 25 servers that are tagged with "class=webserver". (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>ebs_optimized</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>whether instance is using optimized EBS volumes, see <a href='http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSOptimized.html'>http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSOptimized.html</a> (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>ec2_url</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Must be specified if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used</td>
    </tr>
            <tr>
    <td>exact_count</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>An integer value which indicates how many instances that match the 'count_tag' parameter should be running. Instances are either created or terminated based on this value. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>group</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>security group (or list of groups) to use with the instance</td>
    </tr>
            <tr>
    <td>group_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>security group id (or list of ids) to use with the instance (added in Ansible 1.1)</td>
    </tr>
            <tr>
    <td>image</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><em>ami</em> ID to use for the instance</td>
    </tr>
            <tr>
    <td>instance_ids</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>list of instance ids, currently used for states: absent, running, stopped (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>instance_profile_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of the IAM instance profile to use. Boto library must be 2.5.0+ (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>instance_tags</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>a hash/dictionary of tags to add to the new instance; '{"key":"value"}' and '{"key":"value","key":"value"}' (added in Ansible 1.0)</td>
    </tr>
            <tr>
    <td>instance_type</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>instance type to use for the instance</td>
    </tr>
            <tr>
    <td>kernel</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>kernel <em>eki</em> to use for the instance</td>
    </tr>
            <tr>
    <td>key_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>key pair to use on the instance</td>
    </tr>
            <tr>
    <td>monitoring</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>enable detailed monitoring (CloudWatch) for instance (added in Ansible 1.1)</td>
    </tr>
            <tr>
    <td>placement_group</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>placement group for the instance when using EC2 Clustered Compute (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>private_ip</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the private ip address to assign the instance (from the vpc subnet) (added in Ansible 1.2)</td>
    </tr>
            <tr>
    <td>profile</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>uses a boto profile. Only works with boto &gt;= 2.24.0 (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>ramdisk</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>ramdisk <em>eri</em> to use for the instance</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The AWS region to use.  Must be specified if ec2_url is not used. If not specified then the value of the EC2_REGION environment variable, if any, is used. (added in Ansible 1.2)</td>
    </tr>
            <tr>
    <td>security_token</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>security token to authenticate against AWS (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>source_dest_check</td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>Enable or Disable the Source/Destination checks (for NAT instances and Virtual Routers) (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>spot_price</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Maximum spot price to bid, If not set a regular on-demand instance is requested. A spot request is made with this maximum bid. When it is filled, the instance is started. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>spot_wait_timeout</td>
    <td>no</td>
    <td>600</td>
        <td><ul></ul></td>
        <td>how long to wait for the spot instance request to be fulfilled (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>running</li><li>stopped</li></ul></td>
        <td>create or terminate instances (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>tenancy</td>
    <td>no</td>
    <td>default</td>
        <td><ul></ul></td>
        <td>An instance with a tenancy of "dedicated" runs on single-tenant hardware and can only be launched into a VPC. Valid values are "default" or "dedicated". Note that to use dedicated tenancy you MUST specify a vpc_subnet_id as well. Dedicated tenancy is not available for EC2 "micro" instances. (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>user_data</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>opaque blob of data which is made available to the ec2 instance (added in Ansible 0.9)</td>
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
        <td>a list of volume dicts, each containing device name and optionally ephemeral id or snapshot id. Size and type (and number of iops for io device type) must be specified for a new volume or a root volume, and may be passed for a snapshot volume. For any volume, a volume size less than 1 will be interpreted as a request not to create the volume. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>vpc_subnet_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>the subnet ID in which to launch the instance (VPC) (added in Ansible 1.1)</td>
    </tr>
            <tr>
    <td>wait</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>wait for the instance to be 'running' before returning.  Does not wait for SSH, see 'wait_for' example for details.</td>
    </tr>
            <tr>
    <td>wait_timeout</td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td>how long before wait gives up, in seconds</td>
    </tr>
            <tr>
    <td>zone</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>AWS availability zone in which to launch the instance (added in Ansible 1.2)</td>
    </tr>
        </table>


.. note:: Requires boto


Examples
--------

.. raw:: html

    <br/>


::

    # Note: These examples do not set authentication details, see the AWS Guide for details.
    
    # Basic provisioning example
    - ec2:
        key_name: mykey
        instance_type: t2.micro
        image: ami-123456
        wait: yes
        group: webserver
        count: 3
        vpc_subnet_id: subnet-29e63245
        assign_public_ip: yes
    
    # Advanced example with tagging and CloudWatch
    - ec2:
        key_name: mykey
        group: databases
        instance_type: t2.micro
        image: ami-123456
        wait: yes
        wait_timeout: 500
        count: 5
        instance_tags: 
           db: postgres
        monitoring: yes
        vpc_subnet_id: subnet-29e63245
        assign_public_ip: yes
    
    # Single instance with additional IOPS volume from snapshot and volume delete on termination
    - ec2:
        key_name: mykey
        group: webserver
        instance_type: c3.medium
        image: ami-123456
        wait: yes
        wait_timeout: 500
        volumes:
          - device_name: /dev/sdb
            snapshot: snap-abcdef12
            device_type: io1
            iops: 1000
            volume_size: 100
            delete_on_termination: true
        monitoring: yes
        vpc_subnet_id: subnet-29e63245
        assign_public_ip: yes
    
    # Multiple groups example
    - ec2:
        key_name: mykey
        group: ['databases', 'internal-services', 'sshable', 'and-so-forth']
        instance_type: m1.large
        image: ami-6e649707
        wait: yes
        wait_timeout: 500
        count: 5
        instance_tags: 
            db: postgres
        monitoring: yes
        vpc_subnet_id: subnet-29e63245
        assign_public_ip: yes
    
    # Multiple instances with additional volume from snapshot
    - ec2:
        key_name: mykey
        group: webserver
        instance_type: m1.large
        image: ami-6e649707
        wait: yes
        wait_timeout: 500
        count: 5
        volumes:
        - device_name: /dev/sdb
          snapshot: snap-abcdef12
          volume_size: 10
        monitoring: yes
        vpc_subnet_id: subnet-29e63245
        assign_public_ip: yes
    
    # Dedicated tenancy example
    - local_action:
        module: ec2
        assign_public_ip: yes
        group_id: sg-1dc53f72
        key_name: mykey
        image: ami-6e649707
        instance_type: m1.small
        tenancy: dedicated
        vpc_subnet_id: subnet-29e63245
        wait: yes
    
    # Spot instance example
    - ec2:
        spot_price: 0.24
        spot_wait_timeout: 600
        keypair: mykey
        group_id: sg-1dc53f72
        instance_type: m1.small
        image: ami-6e649707
        wait: yes
        vpc_subnet_id: subnet-29e63245
        assign_public_ip: yes
    
    # Launch instances, runs some tasks
    # and then terminate them
    
    - name: Create a sandbox instance
      hosts: localhost
      gather_facts: False
      vars:
        key_name: my_keypair
        instance_type: m1.small
        security_group: my_securitygroup
        image: my_ami_id
        region: us-east-1
      tasks:
        - name: Launch instance
          ec2: 
             key_name: "{{ keypair }}"
             group: "{{ security_group }}"
             instance_type: "{{ instance_type }}"
             image: "{{ image }}"
             wait: true
             region: "{{ region }}"
             vpc_subnet_id: subnet-29e63245
             assign_public_ip: yes
          register: ec2
        - name: Add new instance to host group
          add_host: hostname={{ item.public_ip }} groupname=launched
          with_items: ec2.instances
        - name: Wait for SSH to come up
          wait_for: host={{ item.public_dns_name }} port=22 delay=60 timeout=320 state=started
          with_items: ec2.instances
    
    - name: Configure instance(s)
      hosts: launched
      sudo: True
      gather_facts: True
      roles:
        - my_awesome_role
        - my_awesome_test
    
    - name: Terminate instances
      hosts: localhost
      connection: local
      tasks:
        - name: Terminate instances that were previously launched
          ec2:
            state: 'absent'
            instance_ids: '{{ ec2.instance_ids }}'
    
    # Start a few existing instances, run some tasks
    # and stop the instances
    
    - name: Start sandbox instances
      hosts: localhost
      gather_facts: false
      connection: local
      vars:
        instance_ids:
          - 'i-xxxxxx'
          - 'i-xxxxxx'
          - 'i-xxxxxx'
        region: us-east-1
      tasks:
        - name: Start the sandbox instances
          ec2:
            instance_ids: '{{ instance_ids }}'
            region: '{{ region }}'
            state: running
            wait: True
            vpc_subnet_id: subnet-29e63245
            assign_public_ip: yes
      role:
        - do_neat_stuff
        - do_more_neat_stuff
    
    - name: Stop sandbox instances
      hosts: localhost
      gather_facts: false
      connection: local
      vars:
        instance_ids:
          - 'i-xxxxxx'
          - 'i-xxxxxx'
          - 'i-xxxxxx'
        region: us-east-1
      tasks:
        - name: Stop the sandbox instances
          ec2:
            instance_ids: '{{ instance_ids }}'
            region: '{{ region }}'
            state: stopped
            wait: True
            vpc_subnet_id: subnet-29e63245
            assign_public_ip: yes
    
    #
    # Enforce that 5 instances with a tag "foo" are running
    # (Highly recommended!)
    #
    
    - ec2:
        key_name: mykey
        instance_type: c1.medium
        image: ami-40603AD1
        wait: yes
        group: webserver
        instance_tags:
            foo: bar
        exact_count: 5
        count_tag: foo
        vpc_subnet_id: subnet-29e63245
        assign_public_ip: yes
    
    #
    # Enforce that 5 running instances named "database" with a "dbtype" of "postgres"
    #
    
    - ec2:
        key_name: mykey
        instance_type: c1.medium
        image: ami-40603AD1
        wait: yes
        group: webserver
        instance_tags: 
            Name: database
            dbtype: postgres
        exact_count: 5
        count_tag: 
            Name: database
            dbtype: postgres
        vpc_subnet_id: subnet-29e63245
        assign_public_ip: yes
    
    #
    # count_tag complex argument examples
    #
    
        # instances with tag foo
        count_tag:
            foo:
    
        # instances with tag foo=bar
        count_tag:
            foo: bar
    
        # instances with tags foo=bar & baz
        count_tag:
            foo: bar
            baz:
    
        # instances with tags foo & bar & baz=bang
        count_tag:
            - foo
            - bar
            - baz: bang
    

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

