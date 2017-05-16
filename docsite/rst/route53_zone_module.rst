.. _route53_zone:


route53_zone - add or delete Route53 zones
++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Creates and deletes Route53 private and public zones


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
    <td>comment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Comment associated with the zone</div></td></tr>
            <tr>
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
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
    <td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
        <div style="font-size: small;">aliases: access_token<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>whether or not the zone should exist or not</div></td></tr>
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
        <td><div>The VPC ID the zone should be a part of (if this is going to be a private zone)</div></td></tr>
            <tr>
    <td>vpc_region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The VPC Region the zone should be a part of (if this is going to be a private zone)</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The DNS zone record (eg: foo.com.)</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # create a public zone
    - route53_zone: zone=example.com state=present comment="this is an example"
    
    # delete a public zone
    - route53_zone: zone=example.com state=absent
    
    - name: private zone for devel
      route53_zone: zone=devel.example.com state=present vpc_id={{myvpc_id}} comment='developer domain'
    
    # more complex example
    - name: register output after creating zone in parameterized region
      route53_zone:
        vpc_id: "{{ vpc.vpc_id }}"
        vpc_region: "{{ ec2_region }}"
        zone: "{{ vpc_dns_zone }}"
        state: present
        register: zone_out
    
    - debug: var=zone_out
    

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> comment </td>
        <td> optional hosted zone comment </td>
        <td align=center> when hosted zone exists </td>
        <td align=center> string </td>
        <td align=center> Private zone </td>
    </tr>
            <tr>
        <td> private_zone </td>
        <td> whether hosted zone is private or public </td>
        <td align=center> when hosted zone exists </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> name </td>
        <td> hosted zone name </td>
        <td align=center> when hosted zone exists </td>
        <td align=center> string </td>
        <td align=center> private.local. </td>
    </tr>
            <tr>
        <td> vpc_region </td>
        <td> region of vpc attached to private hosted zone </td>
        <td align=center> for private hosted zone </td>
        <td align=center> string </td>
        <td align=center> eu-west-1 </td>
    </tr>
            <tr>
        <td> vpc_id </td>
        <td> id of vpc attached to private hosted zone </td>
        <td align=center> for private hosted zone </td>
        <td align=center> string </td>
        <td align=center> vpc-1d36c84f </td>
    </tr>
            <tr>
        <td> zone_id </td>
        <td> hosted zone id </td>
        <td align=center> when hosted zone exists </td>
        <td align=center> string </td>
        <td align=center> Z6JQG9820BEFMW </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

