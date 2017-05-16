.. _ec2_vpc_dhcp_options:


ec2_vpc_dhcp_options - Manages DHCP Options, and can ensure the DHCP options for the given VPC match what's requested
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module removes, or creates DHCP option sets, and can associate them to a VPC. Optionally, a new DHCP Options set can be created that converges a VPC's existing DHCP option set with values provided. When dhcp_options_id is provided, the module will 1. remove (with state='absent') 2. ensure tags are applied (if state='present' and tags are provided 3. attach it to a VPC (if state='present' and a vpc_id is provided. If any of the optional values are missing, they will either be treated as a no-op (i.e., inherit what already exists for the VPC) To remove existing options while inheriting, supply an empty value (e.g. set ntp_servers to [] if you want to remove them from the VPC's options) Most of the options should be self-explanatory.


Requirements (on host that executes module)
-------------------------------------------

  * boto
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
                <tr><td>delete_old<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Whether to delete the old VPC DHCP option set when associating a new one. This is primarily useful for debugging/development purposes when you want to quickly roll back to the old option set. Note that this setting will be ignored, and the old DHCP option set will be preserved, if it is in use by any other VPC. (Otherwise, AWS will return an error.)</div>        </td></tr>
                <tr><td>dhcp_options_id<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The resource_id of an existing DHCP options set. If this is specified, then it will override other settings, except tags (which will be updated to match)</div>        </td></tr>
                <tr><td>dns_servers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A list of hosts to set the DNS servers for the VPC to. (Should be a list of IP addresses rather than host names.)</div>        </td></tr>
                <tr><td>domain_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>The domain name to set in the DHCP option sets</div>        </td></tr>
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>inherit_existing<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>For any DHCP options not specified in these parameters, whether to inherit them from the options set already applied to vpc_id, or to reset them to be empty.</div>        </td></tr>
                <tr><td>netbios_name_servers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>List of hosts to advertise as NetBIOS servers.</div>        </td></tr>
                <tr><td>netbios_node_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>NetBIOS node type to advertise in the DHCP options. The AWS recommendation is to use 2 (when using netbios name services) http://docs.aws.amazon.com/AmazonVPC/latest/UserGuide/VPC_DHCP_Options.html</div>        </td></tr>
                <tr><td>ntp_servers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>List of hosts to advertise as NTP servers for the VPC.</div>        </td></tr>
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
                <tr><td>state<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>create/assign or remove the DHCP options. If state is set to absent, then a DHCP options set matched either by id, or tags and options will be removed if possible.</div>        </td></tr>
                <tr><td>tags<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Tags to be applied to a VPC options set if a new one is created, or if the resource_id is provided. (options must match)</div></br>
    <div style="font-size: small;">aliases: resource_tags<div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div>        </td></tr>
                <tr><td>vpc_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>VPC ID to associate with the requested DHCP option set. If no vpc id is provided, and no matching option set is found then a new DHCP option set is created.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Completely overrides the VPC DHCP options associated with VPC vpc-123456 and deletes any existing
    # DHCP option set that may have been attached to that VPC.
    - ec2_vpc_dhcp_options:
        domain_name: "foo.example.com"
        region: us-east-1
        dns_servers:
            - 10.0.0.1
            - 10.0.1.1
        ntp_servers:
            - 10.0.0.2
            - 10.0.1.2
        netbios_name_servers:
            - 10.0.0.1
            - 10.0.1.1
        netbios_node_type: 2
        vpc_id: vpc-123456
        delete_old: True
        inherit_existing: False
    
    
    # Ensure the DHCP option set for the VPC has 10.0.0.4 and 10.0.1.4 as the specified DNS servers, but
    # keep any other existing settings. Also, keep the old DHCP option set around.
    - ec2_vpc_dhcp_options:
        region: us-east-1
        dns_servers:
          - "{{groups['dns-primary']}}"
          - "{{groups['dns-secondary']}}"
        vpc_id: vpc-123456
        inherit_existing: True
        delete_old: False
    
    
    ## Create a DHCP option set with 4.4.4.4 and 8.8.8.8 as the specified DNS servers, with tags
    ## but do not assign to a VPC
    - ec2_vpc_dhcp_options:
        region: us-east-1
        dns_servers:
          - 4.4.4.4
          - 8.8.8.8
        tags:
          Name: google servers
          Environment: Test
    
    ## Delete a DHCP options set that matches the tags and options specified
    - ec2_vpc_dhcp_options:
        region: us-east-1
        dns_servers:
          - 4.4.4.4
          - 8.8.8.8
        tags:
          Name: google servers
          Environment: Test
      state: absent
    
    ## Associate a DHCP options set with a VPC by ID
    - ec2_vpc_dhcp_options:
        region: us-east-1
        dhcp_options_id: dopt-12345678
        vpc_id: vpc-123456
    

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
        <td> changed </td>
        <td> Whether the dhcp options were changed </td>
        <td align=center> always </td>
        <td align=center> bool </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> dhcp_options_id </td>
        <td> The aws resource id of the primary DCHP options set created, found or removed </td>
        <td align=center> when available </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> new_options </td>
        <td> The DHCP options created, associated or found </td>
        <td align=center> when appropriate </td>
        <td align=center> dict </td>
        <td align=center> {'domain-name': 'my.example.com', 'domain-name-servers': ['10.0.0.1', '10.0.1.1'], 'netbois-name-servers': ['10.0.0.1', '10.0.1.1'], 'netbios-node-type': 2} </td>
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

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is supported mainly by the community and is curated by core committers.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
