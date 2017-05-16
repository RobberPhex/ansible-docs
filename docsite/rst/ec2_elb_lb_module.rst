.. _ec2_elb_lb:


ec2_elb_lb - Creates or destroys Amazon ELB.
++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.5

Returns information about the load balancer.
Will be marked changed when called only if state is changed.

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
    <td>connection_draining_timeout</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Wait a specified timeout allowing connections to drain before terminating an instance (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>cross_az_load_balancing</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Distribute load across all configured Availablity Zones (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>ec2_url</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Must be specified if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used</td>
    </tr>
            <tr>
    <td>health_check</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>An associative array of health check configuration settigs (see example)</td>
    </tr>
            <tr>
    <td>listeners</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>List of ports/protocols for this ELB to listen on (see example)</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The name of the ELB</td>
    </tr>
            <tr>
    <td>profile</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>uses a boto profile. Only works with boto &gt;= 2.24.0 (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>purge_listeners</td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>Purge existing listeners on ELB that are not found in listeners</td>
    </tr>
            <tr>
    <td>purge_subnets</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Purge existing subnet on ELB that are not found in subnets (added in Ansible 1.7)</td>
    </tr>
            <tr>
    <td>purge_zones</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Purge existing availability zones on ELB that are not found in zones</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The AWS region to use. If not specified then the value of the EC2_REGION environment variable, if any, is used.</td>
    </tr>
            <tr>
    <td>scheme</td>
    <td>no</td>
    <td>internet-facing</td>
        <td><ul></ul></td>
        <td>The scheme to use when creating the ELB. For a private VPC-visible ELB use 'internal'. (added in Ansible 1.7)</td>
    </tr>
            <tr>
    <td>security_group_ids</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>A list of security groups to apply to the elb (added in Ansible 1.6)</td>
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
        <td><ul></ul></td>
        <td>Create or destroy the ELB</td>
    </tr>
            <tr>
    <td>subnets</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>A list of VPC subnets to use when creating ELB. Zones should be empty if using this. (added in Ansible 1.7)</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>zones</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>List of availability zones to enable on this ELB</td>
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
    
    # Basic provisioning example
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
          - protocol: https
            load_balancer_port: 443
            instance_protocol: http # optional, defaults to value of protocol setting
            instance_port: 80
            # ssl certificate required for https or ssl
            ssl_certificate_id: "arn:aws:iam::123456789012:server-certificate/company/servercerts/ProdServerCert"
    
    
    # Basic VPC provisioning example
    - local_action:
        module: ec2_elb_lb
        name: "test-vpc"
        scheme: internal
        state: present
        subnets: 
          - subnet-abcd1234
          - subnet-1a2b3c4d
        listeners:
          - protocol: http # options are http, https, ssl, tcp
            load_balancer_port: 80
            instance_port: 80
    
    # Configure a health check
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
    
    # Ensure ELB is gone
    - local_action:
        module: ec2_elb_lb
        name: "test-please-delete"
        state: absent
    
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
    # on the ELB alone. If purge_zones is true, then any extreneous zones
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
        subnets: 'subnet-123456, subnet-67890'
        purge_subnets: yes
        listeners:
          - protocol: http
            load_balancer_port: 80
            instance_port: 80
    
    # Create an ELB with connection draining and cross availability
    # zone load balancing
    - local_action:
        module: ec2_elb_lb
        name: "New ELB"
        state: present
        connection_draining_timeout: 60
        cross_az_load_balancing: "yes"
        region: us-east-1
        zones:
          - us-east-1a
          - us-east-1d
        listeners:
          - protocols: http
          - load_balancer_port: 80
          - instance_port: 80

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

