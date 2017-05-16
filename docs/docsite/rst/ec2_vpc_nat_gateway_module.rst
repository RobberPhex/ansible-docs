.. _ec2_vpc_nat_gateway:


ec2_vpc_nat_gateway - Manage AWS VPC NAT Gateways.
++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Ensure the state of AWS VPC NAT Gateways based on their id, allocation and subnet ids.


Requirements (on host that executes module)
-------------------------------------------

  * boto
  * boto3
  * botocore
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
                <tr><td>allocation_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The id of the elastic IP allocation. If this is not passed and the eip_address is not passed. An EIP is generated for this NAT Gateway.</div>        </td></tr>
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
                <tr><td>client_token<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Optional unique token to be used during create to ensure idempotency. When specifying this option, ensure you specify the eip_address parameter as well otherwise any subsequent runs will fail.</div>        </td></tr>
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>eip_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The elastic IP address of the EIP you want attached to this NAT Gateway. If this is not passed and the allocation_id is not passed, an EIP is generated for this NAT Gateway.</div>        </td></tr>
                <tr><td>if_exist_do_not_create<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>if a NAT Gateway exists already in the subnet_id, then do not create a new one.</div>        </td></tr>
                <tr><td>nat_gateway_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The id AWS dynamically allocates to the NAT Gateway on creation. This is required when the absent option is present.</div>        </td></tr>
                <tr><td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Uses a boto profile. Only works with boto &gt;= 2.24.0.</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The AWS region to use. If not specified then the value of the AWS_REGION or EC2_REGION environment variable, if any, is used. See <a href='http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region'>http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region</a></div></br>
    <div style="font-size: small;">aliases: aws_region, ec2_region<div>        </td></tr>
                <tr><td>release_eip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Deallocate the EIP from the VPC.</div><div>Option is only valid with the absent state.</div><div>You should use this with the wait option. Since you can not release an address while a delete operation is happening.</div>        </td></tr>
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Ensure NAT Gateway is present or absent.</div>        </td></tr>
                <tr><td>subnet_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The id of the subnet to create the NAT Gateway in. This is required with the present option.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Wait for operation to complete before returning.</div>        </td></tr>
                <tr><td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td></td>
        <td><div>How many seconds to wait for an operation to complete before timing out.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note: These examples do not set authentication details, see the AWS Guide for details.
    
    - name: Create new nat gateway with client token.
      ec2_vpc_nat_gateway:
        state: present
        subnet_id: subnet-12345678
        eip_address: 52.1.1.1
        region: ap-southeast-2
        client_token: abcd-12345678
      register: new_nat_gateway
    
    - name: Create new nat gateway using an allocation-id.
      ec2_vpc_nat_gateway:
        state: present
        subnet_id: subnet-12345678
        allocation_id: eipalloc-12345678
        region: ap-southeast-2
      register: new_nat_gateway
    
    - name: Create new nat gateway, using an EIP address  and wait for available status.
      ec2_vpc_nat_gateway:
        state: present
        subnet_id: subnet-12345678
        eip_address: 52.1.1.1
        wait: yes
        region: ap-southeast-2
      register: new_nat_gateway
    
    - name: Create new nat gateway and allocate new EIP.
      ec2_vpc_nat_gateway:
        state: present
        subnet_id: subnet-12345678
        wait: yes
        region: ap-southeast-2
      register: new_nat_gateway
    
    - name: Create new nat gateway and allocate new EIP if a nat gateway does not yet exist in the subnet.
      ec2_vpc_nat_gateway:
        state: present
        subnet_id: subnet-12345678
        wait: yes
        region: ap-southeast-2
        if_exist_do_not_create: true
      register: new_nat_gateway
    
    - name: Delete nat gateway using discovered nat gateways from facts module.
      ec2_vpc_nat_gateway:
        state: absent
        region: ap-southeast-2
        wait: yes
        nat_gateway_id: "{{ item.NatGatewayId }}"
        release_eip: yes
      register: delete_nat_gateway_result
      with_items: "{{ gateways_to_remove.result }}"
    
    - name: Delete nat gateway and wait for deleted status.
      ec2_vpc_nat_gateway:
        state: absent
        nat_gateway_id: nat-12345678
        wait: yes
        wait_timeout: 500
        region: ap-southeast-2
    
    - name: Delete nat gateway and release EIP.
      ec2_vpc_nat_gateway:
        state: absent
        nat_gateway_id: nat-12345678
        release_eip: yes
        wait: yes
        wait_timeout: 300
        region: ap-southeast-2

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
        <td> state </td>
        <td> The current state of the NAT Gateway. </td>
        <td align=center> In all cases. </td>
        <td align=center> string </td>
        <td align=center> available </td>
    </tr>
            <tr>
        <td> create_time </td>
        <td> The ISO 8601 date time formatin UTC. </td>
        <td align=center> In all cases. </td>
        <td align=center> string </td>
        <td align=center> 2016-03-05T05:19:20.282000+00:00' </td>
    </tr>
            <tr>
        <td> nat_gateway_id </td>
        <td> id of the VPC NAT Gateway </td>
        <td align=center> In all cases. </td>
        <td align=center> string </td>
        <td align=center> nat-0d1e3a878585988f8 </td>
    </tr>
            <tr>
        <td> subnet_id </td>
        <td> id of the Subnet </td>
        <td align=center> In all cases. </td>
        <td align=center> string </td>
        <td align=center> subnet-12345 </td>
    </tr>
            <tr>
        <td> vpc_id </td>
        <td> id of the VPC. </td>
        <td align=center> In all cases. </td>
        <td align=center> string </td>
        <td align=center> vpc-12345 </td>
    </tr>
            <tr>
        <td> nat_gateway_addresses </td>
        <td> List of dictionairies containing the public_ip, network_interface_id, private_ip, and allocation_id. </td>
        <td align=center> In all cases. </td>
        <td align=center> string </td>
        <td align=center> [{'public_ip': '52.52.52.52', 'network_interface_id': 'eni-12345', 'private_ip': '10.0.0.100', 'allocation_id': 'eipalloc-12345'}] </td>
    </tr>
        
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

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
