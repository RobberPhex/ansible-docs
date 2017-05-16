.. _route53:


route53 - add or delete entries in Amazons Route53 DNS service
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.3


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Creates and deletes DNS records in Amazons Route53 service


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
    <td>alias<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Indicates if this is an alias record.</div></td></tr>
            <tr>
    <td>alias_evaluate_target_health<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether or not to evaluate an alias target health. Useful for aliases to Elastic Load Balancers.</div></td></tr>
            <tr>
    <td>alias_hosted_zone_id<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The hosted zone identifier.</div></td></tr>
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
    <td>command<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>get</li><li>create</li><li>delete</li></ul></td>
        <td><div>Specifies the action to take.</div></td></tr>
            <tr>
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>failover<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Failover resource record sets only. Whether this is the primary or secondary resource record set. Allowed values are PRIMARY and SECONDARY</div></td></tr>
            <tr>
    <td>health_check<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Health check to associate with this record</div></td></tr>
            <tr>
    <td>hosted_zone_id<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The Hosted Zone ID of the DNS zone to modify</div></td></tr>
            <tr>
    <td>identifier<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Have to be specified for Weighted, latency-based and failover resource record sets only. An identifier that differentiates among multiple resource record sets that have the same combination of DNS name and type.</div></td></tr>
            <tr>
    <td>overwrite<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether an existing record should be overwritten on create if values do not match</div></td></tr>
            <tr>
    <td>private_zone<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If set to true, the private zone matching the requested name within the domain will be used if there are both public and private zones. The default is to use the public zone.</div></td></tr>
            <tr>
    <td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>uses a boto profile. Only works with boto &gt;= 2.24.0</div></td></tr>
            <tr>
    <td>record<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The full DNS record to create or delete</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Latency-based resource record sets only Among resource record sets that have the same combination of DNS name and type, a value that determines which region this should be associated with for the latency-based routing</div></td></tr>
            <tr>
    <td>retry_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>500</td>
        <td><ul></ul></td>
        <td><div>In the case that route53 is still servicing a prior request, this module will wait and try again after this many seconds. If you have many domain names, the default of 500 seconds may be too long.</div></td></tr>
            <tr>
    <td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
        <div style="font-size: small;">aliases: access_token<div></td></tr>
            <tr>
    <td>ttl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3600 (one hour)</td>
        <td><ul></ul></td>
        <td><div>The TTL to give the new record</div></td></tr>
            <tr>
    <td>type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>A</li><li>CNAME</li><li>MX</li><li>AAAA</li><li>TXT</li><li>PTR</li><li>SRV</li><li>SPF</li><li>NS</li><li>SOA</li></ul></td>
        <td><div>The type of DNS record to create</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div></td></tr>
            <tr>
    <td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The new value when creating a DNS record.  Multiple comma-spaced values are allowed for non-alias records.  When deleting a record all values for the record must be specified or Route53 will not delete it.</div></td></tr>
            <tr>
    <td>vpc_id<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>When used in conjunction with private_zone: true, this will only modify records in the private hosted zone attached to this VPC.</div><div>This allows you to have multiple private hosted zones, all with the same name, attached to different VPCs.</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Wait until the changes have been replicated to all Amazon Route 53 DNS servers.</div></td></tr>
            <tr>
    <td>wait_timeout<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td><div>How long to wait for the changes to be replicated, in seconds.</div></td></tr>
            <tr>
    <td>weight<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Weighted resource record sets only. Among resource record sets that have the same combination of DNS name and type, a value that determines what portion of traffic for the current resource record set is routed to the associated location.</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The DNS zone to modify</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Add new.foo.com as an A record with 3 IPs and wait until the changes have been replicated
    - route53:
          command: create
          zone: foo.com
          record: new.foo.com
          type: A
          ttl: 7200
          value: 1.1.1.1,2.2.2.2,3.3.3.3
          wait: yes
    
    # Retrieve the details for new.foo.com
    - route53:
          command: get
          zone: foo.com
          record: new.foo.com
          type: A
      register: rec
    
    # Delete new.foo.com A record using the results from the get command
    - route53:
          command: delete
          zone: foo.com
          record: "{{ rec.set.record }}"
          ttl: "{{ rec.set.ttl }}"
          type: "{{ rec.set.type }}"
          value: "{{ rec.set.value }}"
    
    # Add an AAAA record.  Note that because there are colons in the value
    # that the entire parameter list must be quoted:
    - route53:
          command: "create"
          zone: "foo.com"
          record: "localhost.foo.com"
          type: "AAAA"
          ttl: "7200"
          value: "::1"
    
    # Add a SRV record with multiple fields for a service on port 22222
    # For more information on SRV records see:
    # https://en.wikipedia.org/wiki/SRV_record
    - route53:
          command: "create"
          "zone": "foo.com"
          "record": "_example-service._tcp.foo.com"
          "type": "SRV"
          "value": ["0 0 22222 host1.foo.com", "0 0 22222 host2.foo.com"]
    
    # Add a TXT record. Note that TXT and SPF records must be surrounded
    # by quotes when sent to Route 53:
    - route53:
          command: "create"
          zone: "foo.com"
          record: "localhost.foo.com"
          type: "TXT"
          ttl: "7200"
          value: '"bar"'
    
    # Add an alias record that points to an Amazon ELB:
    - route53:
          command=create
          zone=foo.com
          record=elb.foo.com
          type=A
          value="{{ elb_dns_name }}"
          alias=True
          alias_hosted_zone_id="{{ elb_zone_id }}"
    
    # Retrieve the details for elb.foo.com
    - route53:
          command: get
          zone: foo.com
          record: elb.foo.com
          type: A
      register: rec
    
    # Delete an alias record using the results from the get command
    - route53:
          command: delete
          zone: foo.com
          record: "{{ rec.set.record }}"
          ttl: "{{ rec.set.ttl }}"
          type: "{{ rec.set.type }}"
          value: "{{ rec.set.value }}"
          alias: True
          alias_hosted_zone_id: "{{ rec.set.alias_hosted_zone_id }}"
    
    # Add an alias record that points to an Amazon ELB and evaluates it health:
    - route53:
          command=create
          zone=foo.com
          record=elb.foo.com
          type=A
          value="{{ elb_dns_name }}"
          alias=True
          alias_hosted_zone_id="{{ elb_zone_id }}"
          alias_evaluate_target_health=True
    
    # Add an AAAA record with Hosted Zone ID.  Note that because there are colons in the value
    # that the entire parameter list must be quoted:
    - route53:
          command: "create"
          zone: "foo.com"
          hosted_zone_id: "Z2AABBCCDDEEFF"
          record: "localhost.foo.com"
          type: "AAAA"
          ttl: "7200"
          value: "::1"
    
    # Add an AAAA record with Hosted Zone ID.  Note that because there are colons in the value
    # that the entire parameter list must be quoted:
    - route53:
          command: "create"
          zone: "foo.com"
          hosted_zone_id: "Z2AABBCCDDEEFF"
          record: "localhost.foo.com"
          type: "AAAA"
          ttl: "7200"
          value: "::1"
    
    # Use a routing policy to distribute traffic:
    - route53:
          command: "create"
          zone: "foo.com"
          record: "www.foo.com"
          type: "CNAME"
          value: "host1.foo.com"
          ttl: 30
          # Routing policy
          identifier: "host1@www"
          weight: 100
          health_check: "d994b780-3150-49fd-9205-356abdd42e75"
    


Notes
-----

.. note:: If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

