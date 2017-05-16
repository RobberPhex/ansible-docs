.. _ec2_vpc_peer:


ec2_vpc_peer - create, delete, accept, and reject VPC peering connections between two VPCs.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Read the AWS documentation for VPC Peering Connections http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/vpc-peering.html


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
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>peer_owner_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The AWS account number for cross account peering.</div>        </td></tr>
                <tr><td>peer_vpc_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>VPC id of the accepting VPC.</div>        </td></tr>
                <tr><td>peering_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Peering connection id.</div>        </td></tr>
                <tr><td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Uses a boto profile. Only works with boto &gt;= 2.24.0.</div>        </td></tr>
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>accept</li><li>reject</li></ul></td>
        <td><div>Create, delete, accept, reject a peering connection.</div>        </td></tr>
                <tr><td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dictionary of tags to look for and apply when creating a Peering Connection.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div>        </td></tr>
                <tr><td>vpc_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>VPC id of the requesting VPC.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Complete example to create and accept a local peering connection.
    - name: Create local account VPC peering Connection
      ec2_vpc_peer:
        region: ap-southeast-2
        vpc_id: vpc-12345678
        peer_vpc_id: vpc-87654321
        state: present
        tags:
          Name: Peering connection for VPC 21 to VPC 22
          CostCode: CC1234
          Project: phoenix
      register: vpc_peer
    
    - name: Accept local VPC peering request
      ec2_vpc_peer:
        region: ap-southeast-2
        peering_id: "{{ vpc_peer.peering_id }}"
        state: accept
      register: action_peer
    
    # Complete example to delete a local peering connection.
    - name: Create local account VPC peering Connection
      ec2_vpc_peer:
        region: ap-southeast-2
        vpc_id: vpc-12345678
        peer_vpc_id: vpc-87654321
        state: present
        tags:
          Name: Peering connection for VPC 21 to VPC 22
          CostCode: CC1234
          Project: phoenix
      register: vpc_peer
    
    - name: delete a local VPC peering Connection
      ec2_vpc_peer:
        region: ap-southeast-2
        peering_id: "{{ vpc_peer.peering_id }}"
        state: absent
      register: vpc_peer
    
      # Complete example to create and accept a cross account peering connection.
    - name: Create cross account VPC peering Connection
      ec2_vpc_peer:
        region: ap-southeast-2
        vpc_id: vpc-12345678
        peer_vpc_id: vpc-12345678
        peer_owner_id: 123456789102
        state: present
        tags:
          Name: Peering connection for VPC 21 to VPC 22
          CostCode: CC1234
          Project: phoenix
      register: vpc_peer
    
    - name: Accept peering connection from remote account
      ec2_vpc_peer:
        region: ap-southeast-2
        peering_id: "{{ vpc_peer.peering_id }}"
        profile: bot03_profile_for_cross_account
        state: accept
      register: vpc_peer
    
    # Complete example to create and reject a local peering connection.
    - name: Create local account VPC peering Connection
      ec2_vpc_peer:
        region: ap-southeast-2
        vpc_id: vpc-12345678
        peer_vpc_id: vpc-87654321
        state: present
        tags:
          Name: Peering connection for VPC 21 to VPC 22
          CostCode: CC1234
          Project: phoenix
      register: vpc_peer
    
    - name: Reject a local VPC peering Connection
      ec2_vpc_peer:
        region: ap-southeast-2
        peering_id: "{{ vpc_peer.peering_id }}"
        state: reject
    
    # Complete example to create and accept a cross account peering connection.
    - name: Create cross account VPC peering Connection
      ec2_vpc_peer:
        region: ap-southeast-2
        vpc_id: vpc-12345678
        peer_vpc_id: vpc-12345678
        peer_owner_id: 123456789102
        state: present
        tags:
          Name: Peering connection for VPC 21 to VPC 22
          CostCode: CC1234
          Project: phoenix
      register: vpc_peer
    
    - name: Accept a cross account VPC peering connection request
      ec2_vpc_peer:
        region: ap-southeast-2
        peering_id: "{{ vpc_peer.peering_id }}"
        profile: bot03_profile_for_cross_account
        state: accept
        tags:
          Name: Peering connection for VPC 21 to VPC 22
          CostCode: CC1234
          Project: phoenix
    
    # Complete example to create and reject a cross account peering connection.
    - name: Create cross account VPC peering Connection
      ec2_vpc_peer:
        region: ap-southeast-2
        vpc_id: vpc-12345678
        peer_vpc_id: vpc-12345678
        peer_owner_id: 123456789102
        state: present
        tags:
          Name: Peering connection for VPC 21 to VPC 22
          CostCode: CC1234
          Project: phoenix
      register: vpc_peer
    
    - name: Reject a cross account VPC peering Connection
      ec2_vpc_peer:
        region: ap-southeast-2
        peering_id: "{{ vpc_peer.peering_id }}"
        profile: bot03_profile_for_cross_account
        state: reject
    

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
        <td> The result of the create, accept, reject or delete action. </td>
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
