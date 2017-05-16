.. _ec2_eni:


ec2_eni - Create and optionally attach an Elastic Network Interface (ENI) to an instance
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create and optionally attach an Elastic Network Interface (ENI) to an instance. If an ENI ID or private_ip is       provided, the existing ENI (if any) will be modified. The 'attached' parameter controls the attachment status       of the network interface.


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
    <td>attached<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Specifies if network interface should be attached or detached from instance. If ommited, attachment status       won't change</div></td></tr>
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
    <td>delete_on_termination<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Delete the interface when the instance it is attached to is terminated. You can only specify this flag when the interface is being modified, not on creation.</div></td></tr>
            <tr>
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Optional description of the ENI.</div></td></tr>
            <tr>
    <td>device_index<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The index of the device for the network interface attachment on the instance.</div></td></tr>
            <tr>
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>eni_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The ID of the ENI</div></td></tr>
            <tr>
    <td>force_detach<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Force detachment of the interface. This applies either when explicitly detaching the interface by setting instance_id to None or when deleting an interface with state=absent.</div></td></tr>
            <tr>
    <td>instance_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Instance ID that you wish to attach ENI to. Since version 2.2, use the 'attached' parameter to attach or       detach an ENI. Prior to 2.2, to detach an ENI from an instance, use 'None'.</div></td></tr>
            <tr>
    <td>private_ip_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Private IP address.</div></td></tr>
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
    <td>secondary_private_ip_address_count<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The number of secondary IP addresses to assign to the network interface. This option is mutually exclusive of secondary_private_ip_addresses</div></td></tr>
            <tr>
    <td>secondary_private_ip_addresses<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of IP addresses to assign as secondary IP addresses to the network interface. This option is mutually exclusive of secondary_private_ip_address_count</div></td></tr>
            <tr>
    <td>security_groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of security groups associated with the interface. Only used when state=present. Since version 2.2, you       can specify security groups by ID or by name or a combination of both. Prior to 2.2, you can specify only by ID.</div></td></tr>
            <tr>
    <td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
        <div style="font-size: small;">aliases: access_token<div></td></tr>
            <tr>
    <td>source_dest_check<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>By default, interfaces perform source/destination checks. NAT instances however need this check to be disabled. You can only specify this flag when the interface is being modified, not on creation.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Create or delete ENI</div></td></tr>
            <tr>
    <td>subnet_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>ID of subnet in which to create the ENI. Only required when state=present.</div></td></tr>
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

    # Note: These examples do not set authentication details, see the AWS Guide for details.
    
    # Create an ENI. As no security group is defined, ENI will be created in default security group
    - ec2_eni:
        private_ip_address: 172.31.0.20
        subnet_id: subnet-xxxxxxxx
        state: present
    
    # Create an ENI and attach it to an instance
    - ec2_eni:
        instance_id: i-xxxxxxx
        device_index: 1
        private_ip_address: 172.31.0.20
        subnet_id: subnet-xxxxxxxx
        state: present
    
    # Create an ENI with two secondary addresses
    - ec2_eni:
        subnet_id: subnet-xxxxxxxx
        state: present
        secondary_private_ip_address_count: 2
    
    # Assign a secondary IP address to an existing ENI
    # This will purge any existing IPs
    - ec2_eni:
        subnet_id: subnet-xxxxxxxx
        eni_id: eni-yyyyyyyy
        state: present
        secondary_private_ip_addresses:
          - 172.16.1.1
    
    # Remove any secondary IP addresses from an existing ENI
    - ec2_eni:
        subnet_id: subnet-xxxxxxxx
        eni_id: eni-yyyyyyyy
        state: present
        secondary_private_ip_addresses:
          -
    
    # Destroy an ENI, detaching it from any instance if necessary
    - ec2_eni:
        eni_id: eni-xxxxxxx
        force_detach: yes
        state: absent
    
    # Update an ENI
    - ec2_eni:
        eni_id: eni-xxxxxxx
        description: "My new description"
        state: present
    
    # Detach an ENI from an instance
    - ec2_eni:
        eni_id: eni-xxxxxxx
        instance_id: None
        state: present
    
    ### Delete an interface on termination
    # First create the interface
    - ec2_eni:
        instance_id: i-xxxxxxx
        device_index: 1
        private_ip_address: 172.31.0.20
        subnet_id: subnet-xxxxxxxx
        state: present
      register: eni
    
    # Modify the interface to enable the delete_on_terminaton flag
    - ec2_eni:
        eni_id: {{ "eni.interface.id" }}
        delete_on_termination: true
    

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
        <td> interface </td>
        <td> Network interface attributes </td>
        <td align=center> when state != absent </td>
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

                <tr>
        <td> status </td>
        <td> network interface status </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> pending </td>
        </tr>
                <tr>
        <td> description </td>
        <td> interface description </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> Firewall network interface </td>
        </tr>
                <tr>
        <td> subnet_id </td>
        <td> which vpc subnet the interface is bound </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> subnet-b0a0393c </td>
        </tr>
                <tr>
        <td> private_ip_addresses </td>
        <td> list of all private ip addresses associated to this interface </td>
        <td align=center>  </td>
        <td align=center> list of dictionaries </td>
        <td align=center> [{'private_ip_address': '10.20.30.40', 'primary_address': True}] </td>
        </tr>
                <tr>
        <td> mac_address </td>
        <td> interface's physical address </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> 00:00:5E:00:53:23 </td>
        </tr>
                <tr>
        <td> private_ip_address </td>
        <td> primary ip address of this interface </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> 10.20.30.40 </td>
        </tr>
                <tr>
        <td> vpc_id </td>
        <td> which vpc this network interface is bound </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> vpc-9a9a9da </td>
        </tr>
                <tr>
        <td> groups </td>
        <td> list of security groups </td>
        <td align=center>  </td>
        <td align=center> list of dictionaries </td>
        <td align=center> [{'sg-f8a8a9da': 'default'}] </td>
        </tr>
                <tr>
        <td> id </td>
        <td> network interface id </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> eni-1d889198 </td>
        </tr>
                <tr>
        <td> source_dest_check </td>
        <td> value of source/dest check flag </td>
        <td align=center>  </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
        </tr>
                <tr>
        <td> owner_id </td>
        <td> aws account id </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> 812381371 </td>
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

