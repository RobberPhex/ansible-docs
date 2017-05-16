.. _ec2_elb_lb:


ec2_elb_lb - Creates or destroys Amazon ELB.
++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.5


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Returns information about the load balancer.
Will be marked changed when called only if state is changed.


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
    <td>access_logs<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>An associative array of access logs configuration settings (see example)</div></td></tr>
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
    <td>connection_draining_timeout<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Wait a specified timeout allowing connections to drain before terminating an instance</div></td></tr>
            <tr>
    <td>cross_az_load_balancing<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Distribute load across all configured Availability Zones</div></td></tr>
            <tr>
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>health_check<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>An associative array of health check configuration settings (see example)</div></td></tr>
            <tr>
    <td>idle_timeout<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>ELB connections from clients and to servers are timed out after this amount of time</div></td></tr>
            <tr>
    <td>instance_ids<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of instance ids to attach to this ELB</div></td></tr>
            <tr>
    <td>listeners<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of ports/protocols for this ELB to listen on (see example)</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the ELB</div></td></tr>
            <tr>
    <td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>uses a boto profile. Only works with boto &gt;= 2.24.0</div></td></tr>
            <tr>
    <td>purge_instance_ids<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Purge existing instance ids on ELB that are not found in instance_ids</div></td></tr>
            <tr>
    <td>purge_listeners<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Purge existing listeners on ELB that are not found in listeners</div></td></tr>
            <tr>
    <td>purge_subnets<br/><div style="font-size: small;"> (added in 1.7)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Purge existing subnet on ELB that are not found in subnets</div></td></tr>
            <tr>
    <td>purge_zones<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Purge existing availability zones on ELB that are not found in zones</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The AWS region to use. If not specified then the value of the AWS_REGION or EC2_REGION environment variable, if any, is used. See <a href='http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region'>http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region</a></div></br>
        <div style="font-size: small;">aliases: aws_region, ec2_region<div></td></tr>
            <tr>
    <td>scheme<br/><div style="font-size: small;"> (added in 1.7)</div></td>
    <td>no</td>
    <td>internet-facing</td>
        <td><ul></ul></td>
        <td><div>The scheme to use when creating the ELB. For a private VPC-visible ELB use 'internal'.</div></td></tr>
            <tr>
    <td>security_group_ids<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A list of security groups to apply to the elb</div></td></tr>
            <tr>
    <td>security_group_names<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A list of security group names to apply to the elb</div></td></tr>
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
        <td><div>Create or destroy the ELB</div></td></tr>
            <tr>
    <td>stickiness<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>An associative array of stickness policy settings. Policy will be applied to all listeners ( see example )</div></td></tr>
            <tr>
    <td>subnets<br/><div style="font-size: small;"> (added in 1.7)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A list of VPC subnets to use when creating ELB. Zones should be empty if using this.</div></td></tr>
            <tr>
    <td>tags<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>An associative array of tags. To delete all tags, supply an empty dict.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When specified, Ansible will check the status of the load balancer to ensure it has been successfully removed from AWS.</div></td></tr>
            <tr>
    <td>wait_timeout<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>60</td>
        <td><ul></ul></td>
        <td><div>Used in conjunction with wait. Number of seconds to wait for the elb to be terminated. A maximum of 600 seconds (10 minutes) is allowed.</div></td></tr>
            <tr>
    <td>zones<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of availability zones to enable on this ELB</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note: None of these examples set aws_access_key, aws_secret_key, or region.
    # It is assumed that their matching environment variables are set.
    
    # Basic provisioning example (non-VPC)
    
    - local_action:
        module: ec2_elb_lb
        name: "test-please-delete"
        state: present
        zones:
          - us-east-1a
          - us-east-1d
        listeners:
          - protocol: http # options are http, https, ssl, tcp
            load_balancer_port: 80
            instance_port: 80
            proxy_protocol: True
          - protocol: https
            load_balancer_port: 443
            instance_protocol: http # optional, defaults to value of protocol setting
            instance_port: 80
            # ssl certificate required for https or ssl
            ssl_certificate_id: "arn:aws:iam::123456789012:server-certificate/company/servercerts/ProdServerCert"
    
    # Internal ELB example
    
    - local_action:
        module: ec2_elb_lb
        name: "test-vpc"
        scheme: internal
        state: present
        instance_ids:
          - i-abcd1234
        purge_instance_ids: true
        subnets:
          - subnet-abcd1234
          - subnet-1a2b3c4d
        listeners:
          - protocol: http # options are http, https, ssl, tcp
            load_balancer_port: 80
            instance_port: 80
    
    # Configure a health check and the access logs
    - local_action:
        module: ec2_elb_lb
        name: "test-please-delete"
        state: present
        zones:
          - us-east-1d
        listeners:
          - protocol: http
            load_balancer_port: 80
            instance_port: 80
        health_check:
            ping_protocol: http # options are http, https, ssl, tcp
            ping_port: 80
            ping_path: "/index.html" # not required for tcp or ssl
            response_timeout: 5 # seconds
            interval: 30 # seconds
            unhealthy_threshold: 2
            healthy_threshold: 10
        access_logs:
            interval: 5 # minutes (defaults to 60)
            s3_location: "my-bucket" # This value is required if access_logs is set
            s3_prefix: "logs"
    
    # Ensure ELB is gone
    - local_action:
        module: ec2_elb_lb
        name: "test-please-delete"
        state: absent
    
    # Ensure ELB is gone and wait for check (for default timeout)
    - local_action:
        module: ec2_elb_lb
        name: "test-please-delete"
        state: absent
        wait: yes
    
    # Ensure ELB is gone and wait for check with timeout value
    - local_action:
        module: ec2_elb_lb
        name: "test-please-delete"
        state: absent
        wait: yes
        wait_timeout: 600
    
    # Normally, this module will purge any listeners that exist on the ELB
    # but aren't specified in the listeners parameter. If purge_listeners is
    # false it leaves them alone
    - local_action:
        module: ec2_elb_lb
        name: "test-please-delete"
        state: present
        zones:
          - us-east-1a
          - us-east-1d
        listeners:
          - protocol: http
            load_balancer_port: 80
            instance_port: 80
        purge_listeners: no
    
    # Normally, this module will leave availability zones that are enabled
    # on the ELB alone. If purge_zones is true, then any extraneous zones
    # will be removed
    - local_action:
        module: ec2_elb_lb
        name: "test-please-delete"
        state: present
        zones:
          - us-east-1a
          - us-east-1d
        listeners:
          - protocol: http
            load_balancer_port: 80
            instance_port: 80
        purge_zones: yes
    
    # Creates a ELB and assigns a list of subnets to it.
    - local_action:
        module: ec2_elb_lb
        state: present
        name: 'New ELB'
        security_group_ids: 'sg-123456, sg-67890'
        region: us-west-2
        subnets: 'subnet-123456,subnet-67890'
        purge_subnets: yes
        listeners:
          - protocol: http
            load_balancer_port: 80
            instance_port: 80
    
    # Create an ELB with connection draining, increased idle timeout and cross availability
    # zone load balancing
    - local_action:
        module: ec2_elb_lb
        name: "New ELB"
        state: present
        connection_draining_timeout: 60
        idle_timeout: 300
        cross_az_load_balancing: "yes"
        region: us-east-1
        zones:
          - us-east-1a
          - us-east-1d
        listeners:
          - protocols: http
          - load_balancer_port: 80
          - instance_port: 80
    
    # Create an ELB with load balanacer stickiness enabled
    - local_action:
        module: ec2_elb_lb
        name: "New ELB"
        state: present
        region: us-east-1
        zones:
          - us-east-1a
          - us-east-1d
        listeners:
          - protocols: http
          - load_balancer_port: 80
          - instance_port: 80
        stickiness:
          type: loadbalancer
          enabled: yes
          expiration: 300
    
    # Create an ELB with application stickiness enabled
    - local_action:
        module: ec2_elb_lb
        name: "New ELB"
        state: present
        region: us-east-1
        zones:
          - us-east-1a
          - us-east-1d
        listeners:
          - protocols: http
          - load_balancer_port: 80
          - instance_port: 80
        stickiness:
          type: application
          enabled: yes
          cookie: SESSIONID
    
    # Create an ELB and add tags
    - local_action:
        module: ec2_elb_lb
        name: "New ELB"
        state: present
        region: us-east-1
        zones:
          - us-east-1a
          - us-east-1d
        listeners:
          - protocols: http
          - load_balancer_port: 80
          - instance_port: 80
        tags:
          Name: "New ELB"
          stack: "production"
          client: "Bob"
    
    # Delete all tags from an ELB
    - local_action:
        module: ec2_elb_lb
        name: "New ELB"
        state: present
        region: us-east-1
        zones:
          - us-east-1a
          - us-east-1d
        listeners:
          - protocols: http
          - load_balancer_port: 80
          - instance_port: 80
        tags: {}


Notes
-----

.. note:: If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

