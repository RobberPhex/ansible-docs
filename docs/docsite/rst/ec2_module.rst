.. _ec2:


ec2 - create, terminate, start or stop an instance in ec2
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Creates or terminates ec2 instances.
* ``state=restarted`` was added in 2.2


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
                <tr><td>assign_public_ip<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>when provisioning within vpc, assign a public IP address. Boto library must be 2.13.0+</div>        </td></tr>
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
                <tr><td>count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td></td>
        <td><div>number of instances to launch</div>        </td></tr>
                <tr><td>count_tag<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Used with 'exact_count' to determine how many nodes based on a specific tag criteria should be running.  This can be expressed in multiple ways and is shown in the EXAMPLES section.  For instance, one can request 25 servers that are tagged with "class=webserver". The specified tag must already exist or be passed in as the 'instance_tags' option.</div>        </td></tr>
                <tr><td>ebs_optimized<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td>false</td>
        <td></td>
        <td><div>whether instance is using optimized EBS volumes, see <a href='http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSOptimized.html'>http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/EBSOptimized.html</a></div>        </td></tr>
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>exact_count<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>An integer value which indicates how many instances that match the 'count_tag' parameter should be running. Instances are either created or terminated based on this value.</div>        </td></tr>
                <tr><td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>security group (or list of groups) to use with the instance</div></br>
    <div style="font-size: small;">aliases: groups<div>        </td></tr>
                <tr><td>group_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>security group id (or list of ids) to use with the instance</div>        </td></tr>
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>identifier for this instance or set of instances, so that the module will be idempotent with respect to EC2 instances. This identifier is valid for at least 24 hours after the termination of the instance, and should not be reused for another call later on. For details, see the description of client token at <a href='http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Run_Instance_Idempotency.html'>http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/Run_Instance_Idempotency.html</a>.</div>        </td></tr>
                <tr><td>image<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div><em>ami</em> ID to use for the instance</div>        </td></tr>
                <tr><td>instance_ids<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>list of instance ids, currently used for states: absent, running, stopped</div></br>
    <div style="font-size: small;">aliases: instance_id<div>        </td></tr>
                <tr><td>instance_initiated_shutdown_behavior<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>stop</td>
        <td><ul><li>stop</li><li>terminate</li></ul></td>
        <td><div>Set whether AWS will Stop or Terminate an instance on shutdown</div>        </td></tr>
                <tr><td>instance_profile_name<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the IAM instance profile to use. Boto library must be 2.5.0+</div>        </td></tr>
                <tr><td>instance_tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a hash/dictionary of tags to add to the new instance or for starting/stopping instance by tag; '{"key":"value"}' and '{"key":"value","key":"value"}'</div>        </td></tr>
                <tr><td>instance_type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>instance type to use for the instance, see <a href='http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html'>http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/instance-types.html</a></div>        </td></tr>
                <tr><td>kernel<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>kernel <em>eki</em> to use for the instance</div>        </td></tr>
                <tr><td>key_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>key pair to use on the instance</div></br>
    <div style="font-size: small;">aliases: keypair<div>        </td></tr>
                <tr><td>monitoring<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>enable detailed monitoring (CloudWatch) for instance</div>        </td></tr>
                <tr><td>network_interfaces<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A list of existing network interfaces to attach to the instance at launch. When specifying existing network interfaces, none of the assign_public_ip, private_ip, vpc_subnet_id, group, or group_id parameters may be used. (Those parameters are for creating a new network interface at launch.)</div></br>
    <div style="font-size: small;">aliases: network_interface<div>        </td></tr>
                <tr><td>placement_group<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>placement group for the instance when using EC2 Clustered Compute</div>        </td></tr>
                <tr><td>private_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the private ip address to assign the instance (from the vpc subnet)</div>        </td></tr>
                <tr><td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Uses a boto profile. Only works with boto &gt;= 2.24.0.</div>        </td></tr>
                <tr><td>ramdisk<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>ramdisk <em>eri</em> to use for the instance</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The AWS region to use.  Must be specified if ec2_url is not used. If not specified then the value of the EC2_REGION environment variable, if any, is used. See <a href='http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region'>http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region</a></div></br>
    <div style="font-size: small;">aliases: aws_region, ec2_region<div>        </td></tr>
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>source_dest_check<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Enable or Disable the Source/Destination checks (for NAT instances and Virtual Routers)</div>        </td></tr>
                <tr><td>spot_launch_group<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Launch group for spot request, see <a href='http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/how-spot-instances-work.html#spot-launch-group'>http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/how-spot-instances-work.html#spot-launch-group</a></div>        </td></tr>
                <tr><td>spot_price<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Maximum spot price to bid, If not set a regular on-demand instance is requested. A spot request is made with this maximum bid. When it is filled, the instance is started.</div>        </td></tr>
                <tr><td>spot_type<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>one-time</td>
        <td><ul><li>one-time</li><li>persistent</li></ul></td>
        <td><div>Type of spot request; one of "one-time" or "persistent". Defaults to "one-time" if not supplied.</div>        </td></tr>
                <tr><td>spot_wait_timeout<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>600</td>
        <td></td>
        <td><div>how long to wait for the spot instance request to be fulfilled</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>running</li><li>restarted</li><li>stopped</li></ul></td>
        <td><div>create or terminate instances</div>        </td></tr>
                <tr><td>tenancy<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>default</td>
        <td><ul><li>default</li><li>dedicated</li></ul></td>
        <td><div>An instance with a tenancy of "dedicated" runs on single-tenant hardware and can only be launched into a VPC. Note that to use dedicated tenancy you MUST specify a vpc_subnet_id as well. Dedicated tenancy is not available for EC2 "micro" instances.</div>        </td></tr>
                <tr><td>termination_protection<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Enable or Disable the Termination Protection</div>        </td></tr>
                <tr><td>user_data<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>opaque blob of data which is made available to the ec2 instance</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div>        </td></tr>
                <tr><td>volumes<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>a list of hash/dictionaries of volumes to add to the new instance; '[{"key":"value", "key":"value"}]'; keys allowed are - device_name (str; required), delete_on_termination (bool; False), device_type (deprecated), ephemeral (str), encrypted (bool; False), snapshot (str), volume_type (str), iops (int) - device_type is deprecated use volume_type, iops must be set when volume_type='io1', ephemeral and snapshot are mutually exclusive.</div>        </td></tr>
                <tr><td>vpc_subnet_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>the subnet ID in which to launch the instance (VPC)</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>wait for the instance to reach its desired state before returning.  Does not wait for SSH, see 'wait_for' example for details.</div>        </td></tr>
                <tr><td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td></td>
        <td><div>how long before wait gives up, in seconds</div>        </td></tr>
                <tr><td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS availability zone in which to launch the instance</div></br>
    <div style="font-size: small;">aliases: aws_zone, ec2_zone<div>        </td></tr>
        </table>
    </br>



Examples
--------

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
            volume_type: io1
            iops: 1000
            volume_size: 100
            delete_on_termination: true
        monitoring: yes
        vpc_subnet_id: subnet-29e63245
        assign_public_ip: yes
    
    # Single instance with ssd gp2 root volume
    - ec2:
        key_name: mykey
        group: webserver
        instance_type: c3.medium
        image: ami-123456
        wait: yes
        wait_timeout: 500
        volumes:
          - device_name: /dev/xvda
            volume_type: gp2
            volume_size: 8
        vpc_subnet_id: subnet-29e63245
        assign_public_ip: yes
        exact_count: 1
    
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
        spot_launch_group: report_generators
    
    # Examples using pre-existing network interfaces
    - ec2:
        key_name: mykey
        instance_type: t2.small
        image: ami-f005ba11
        network_interface: eni-deadbeef
    
    - ec2:
        key_name: mykey
        instance_type: t2.small
        image: ami-f005ba11
        network_interfaces: ['eni-deadbeef', 'eni-5ca1ab1e']
    
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
          add_host:
            hostname: "{{ item.public_ip }}"
            groupname: launched
          with_items: "{{ ec2.instances }}"
    
        - name: Wait for SSH to come up
          wait_for:
            host: "{{ item.public_dns_name }}"
            port: 22
            delay: 60
            timeout: 320
            state: started
          with_items: "{{ ec2.instances }}"
    
    - name: Configure instance(s)
      hosts: launched
      become: True
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
      roles:
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
    # Start stopped instances specified by tag
    #
    - local_action:
        module: ec2
        instance_tags:
            Name: ExtraPower
        state: running
    
    #
    # Restart instances specified by tag
    #
    - local_action:
        module: ec2
        instance_tags:
            Name: ExtraPower
        state: restarted
    
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
