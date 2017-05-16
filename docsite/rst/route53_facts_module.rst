.. _route53_facts:


route53_facts - Retrieves route53 details using AWS methods
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Gets various details related to Route53 zone, record set or health check details


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
    <td>change_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The ID of the change batch request. The value that you specify here is the value that ChangeResourceRecordSets returned in the Id element when you submitted the request.</div></td></tr>
            <tr>
    <td>delegation_set_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The DNS Zone delegation set ID</div></td></tr>
            <tr>
    <td>dns_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The first name in the lexicographic ordering of domain names that you want the list_command to start listing from</div></td></tr>
            <tr>
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>health_check_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The ID of the health check</div></td></tr>
            <tr>
    <td>health_check_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>list</td>
        <td><ul><li>list</li><li>details</li><li>status</li><li>failure_reason</li><li>count</li><li>tags</li></ul></td>
        <td><div>This is used in conjunction with query: health_check. It allows for listing details, counts or tags of various health check details.</div></td></tr>
            <tr>
    <td>hosted_zone_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The Hosted Zone ID of the DNS zone</div></td></tr>
            <tr>
    <td>hosted_zone_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>list</td>
        <td><ul><li>details</li><li>list</li><li>list_by_name</li><li>count</li><li>tags</li></ul></td>
        <td><div>This is used in conjunction with query: hosted_zone. It allows for listing details, counts or tags of various hosted zone details.</div></td></tr>
            <tr>
    <td>max_items<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Maximum number of items to return for various get/list requests</div></td></tr>
            <tr>
    <td>next_marker<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Some requests such as list_command: hosted_zones will return a maximum number of entries - EG 100. If the number of entries exceeds this maximum another request can be sent using the NextMarker entry from the first response to get the next page of results</div></td></tr>
            <tr>
    <td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>uses a boto profile. Only works with boto &gt;= 2.24.0</div></td></tr>
            <tr>
    <td>query<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>change</li><li>checker_ip_range</li><li>health_check</li><li>hosted_zone</li><li>record_sets</li><li>reusable_delegation_set</li></ul></td>
        <td><div>specifies the query action to take</div></td></tr>
            <tr>
    <td>resource_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The ID/s of the specified resource/s</div></br>
        <div style="font-size: small;">aliases: resource_ids<div></td></tr>
            <tr>
    <td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
        <div style="font-size: small;">aliases: access_token<div></td></tr>
            <tr>
    <td>start_record_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The first name in the lexicographic ordering of domain names that you want the list_command: record_sets to start listing from</div></td></tr>
            <tr>
    <td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>A</li><li>CNAME</li><li>MX</li><li>AAAA</li><li>TXT</li><li>PTR</li><li>SRV</li><li>SPF</li><li>NS</li></ul></td>
        <td><div>The type of DNS record</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Simple example of listing all hosted zones
    - name: List all hosted zones
      route53_facts:
        query: hosted_zone
      register: hosted_zones
    
    # Getting a count of hosted zones
    - name: Return a count of all hosted zones
      route53_facts:
        query: hosted_zone
        hosted_zone_method: count
      register: hosted_zone_count
    
    - name: List the first 20 resource record sets in a given hosted zone
      route53_facts:
        profile: account_name
        query: record_sets
        hosted_zone_id: 'ZZZ1111112222'
        max_items: 20
      register: record_sets
    
    - name: List first 20 health checks
      route53_facts:
        query: health_check
        health_check_method: list
        max_items: 20
      register: health_checks
    
    - name: Get health check last failure_reason
      route53_facts:
        query: health_check
        health_check_method: failure_reason
        health_check_id: '00000000-1111-2222-3333-12345678abcd'
      register: health_check_failure_reason
    
    - name: Retrieve reusable delegation set details
      route53_facts:
        query: reusable_delegation_set
        delegation_set_id: 'delegation id'
      register: delegation_sets
    


Notes
-----

.. note:: If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

