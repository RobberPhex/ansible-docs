.. _ec2_vpc_nacl:


ec2_vpc_nacl - create and delete Network ACLs.
++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Read the AWS documentation for Network ACLS http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_ACLs.html


Requirements (on host that executes module)
-------------------------------------------

  * boto
  * boto3
  * botocore
  * json
  * python >= 2.6


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
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>egress<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of rules for outgoing traffic.</div><div>Each rule must be specified as a list.</div></td></tr>
            <tr>
    <td>ingress<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of rules for incoming traffic.</div><div>Each rule must be specified as a list.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Tagged name identifying a network ACL.</div></td></tr>
            <tr>
    <td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>uses a boto profile. Only works with boto &gt;= 2.24.0</div></td></tr>
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
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Creates or modifies an existing NACL</div><div>Deletes a NACL and reassociates subnets to the default NACL</div></td></tr>
            <tr>
    <td>subnets<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The list of subnets that should be associated with the network ACL.</div><div>Must be specified as a list</div><div>Each subnet can be specified as subnet ID, or its tagged name.</div></td></tr>
            <tr>
    <td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Dictionary of tags to look for and apply when creating a network ACL.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div></td></tr>
            <tr>
    <td>vpc_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>VPC id of the requesting VPC.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    # Complete example to create and delete a network ACL
    # that allows SSH, HTTP and ICMP in, and all traffic out.
    - name: "Create and associate production DMZ network ACL with DMZ subnets"
      ec2_vpc_nacl:
        vpc_id: vpc-12345678
        name: prod-dmz-nacl
        region: ap-southeast-2
        subnets: ['prod-dmz-1', 'prod-dmz-2']
        tags:
          CostCode: CC1234
          Project: phoenix
          Description: production DMZ
        ingress: [
            # rule no, protocol, allow/deny, cidr, icmp_code, icmp_type,
            #                                             port from, port to
            [100, 'tcp', 'allow', '0.0.0.0/0', null, null, 22, 22],
            [200, 'tcp', 'allow', '0.0.0.0/0', null, null, 80, 80],
            [300, 'icmp', 'allow', '0.0.0.0/0', 0, 8],
        ]
        egress: [
            [100, 'all', 'allow', '0.0.0.0/0', null, null, null, null]
        ]
        state: 'present'
    
    - name: "Remove the ingress and egress rules - defaults to deny all"
      ec2_vpc_nacl:
        vpc_id: vpc-12345678
        name: prod-dmz-nacl
        region: ap-southeast-2
        subnets:
          - prod-dmz-1
          - prod-dmz-2
        tags:
          CostCode: CC1234
          Project: phoenix
          Description: production DMZ
        state: present
    
    - name: "Remove the NACL subnet associations and tags"
      ec2_vpc_nacl:
        vpc_id: 'vpc-12345678'
        name: prod-dmz-nacl
        region: ap-southeast-2
        state: present
    
    - name: "Delete nacl and subnet associations"
      ec2_vpc_nacl:
        vpc_id: vpc-12345678
        name: prod-dmz-nacl
        state: absent

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
        <td> task </td>
        <td> The result of the create, or delete action. </td>
        <td align=center> success </td>
        <td align=center> dictionary </td>
        <td align=center>  </td>
    </tr>
        <tr><td>contains: </td>
    <td colspan=4>
        <table border=1 cellpadding=2>
        <tr>
        <th class="head">name</th>
        <th class="head">description</th>
        <th class="head">returned</th>
        <th class="head">type</th>
        <th class="head">sample</th>
        </tr>

        
        </table>
    </td></tr>

        
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

