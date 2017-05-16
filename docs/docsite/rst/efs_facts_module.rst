.. _efs_facts:


efs_facts - Get information about Amazon EFS file systems
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Module searches Amazon EFS file systems


Requirements (on host that executes module)
-------------------------------------------

  * boto
  * boto3
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
                <tr><td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>ID of Amazon EFS.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Creation Token of Amazon EFS file system.</div>        </td></tr>
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
                <tr><td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>List of tags of Amazon EFS. Should be defined as dictionary</div>        </td></tr>
                <tr><td>targets<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>List of mounted targets. It should be a list of dictionaries, every dictionary should include next attributes: - SubnetId - Mandatory. The ID of the subnet to add the mount target in. - IpAddress - Optional. A valid IPv4 address within the address range of the specified subnet. - SecurityGroups - Optional. List of security group IDs, of the form 'sg-xxxxxxxx'. These must be for the same VPC as subnet specified.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # find all existing efs
    - efs_facts:
      register: result
    
    - efs_facts:
        name: myTestNameTag
    
    - efs_facts:
        id: fs-1234abcd
    
    # Searching all EFS instances with tag Name = 'myTestNameTag', in subnet 'subnet-1a2b3c4d' and with security group 'sg-4d3c2b1a'
    - efs_facts:
        tags:
            name: myTestNameTag
        targets:
            - subnet-1a2b3c4d
            - sg-4d3c2b1a

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
        <td> creation_token </td>
        <td> EFS creation token </td>
        <td align=center> None </td>
        <td align=center> UUID </td>
        <td align=center> console-88609e04-9a0e-4a2e-912c-feaa99509961 </td>
    </tr>
            <tr>
        <td> name </td>
        <td> name of the file system </td>
        <td align=center> None </td>
        <td align=center> str </td>
        <td align=center> my-efs </td>
    </tr>
            <tr>
        <td> tags </td>
        <td> tags on the efs instance </td>
        <td align=center> None </td>
        <td align=center> dict </td>
        <td align=center> {'name': 'my-efs', 'key': 'Value'} </td>
    </tr>
            <tr>
        <td> size_in_bytes </td>
        <td> size of the file system in bytes as of a timestamp </td>
        <td align=center> None </td>
        <td align=center> dict </td>
        <td align=center> {'timestamp': '2015-12-21 13:59:59-05:00', 'value': 12288} </td>
    </tr>
            <tr>
        <td> creation_time </td>
        <td> timestamp of creation date </td>
        <td align=center> None </td>
        <td align=center> datetime </td>
        <td align=center> 2015-11-16 12:30:57 </td>
    </tr>
            <tr>
        <td> life_cycle_state </td>
        <td> state of the EFS file system </td>
        <td align=center> None </td>
        <td align=center> str </td>
        <td align=center> creating, available, deleting, deleted </td>
    </tr>
            <tr>
        <td> file_system_id </td>
        <td> ID of the file system </td>
        <td align=center> None </td>
        <td align=center> unique ID </td>
        <td align=center> fs-xxxxxxxx </td>
    </tr>
            <tr>
        <td> mount_point </td>
        <td> url of file system </td>
        <td align=center> None </td>
        <td align=center> str </td>
        <td align=center> .fs-xxxxxxxx.efs.us-west-2.amazonaws.com:/ </td>
    </tr>
            <tr>
        <td> number_of_mount_targets </td>
        <td> the number of targets mounted </td>
        <td align=center> None </td>
        <td align=center> int </td>
        <td align=center> 3 </td>
    </tr>
            <tr>
        <td> mount_targets </td>
        <td> list of mount targets </td>
        <td align=center> None </td>
        <td align=center> list of dicts </td>
        <td align=center> [{'mount_target_id': 'fsmt-d8907871', 'life_cycle_state': 'available', 'file_system_id': 'fs-a7ad440e', 'subnet_id': 'subnet-e265c895', 'network_interface_id': 'eni-6e387e26', 'ip_address': '172.31.17.173', 'security_groups': ['sg-a30b22c6'], 'owner_id': '740748460359'}, '...'] </td>
    </tr>
            <tr>
        <td> performance_mode </td>
        <td> performance mode of the file system </td>
        <td align=center> None </td>
        <td align=center> str </td>
        <td align=center> generalPurpose </td>
    </tr>
            <tr>
        <td> owner_id </td>
        <td> AWS account ID of EFS owner </td>
        <td align=center> None </td>
        <td align=center> str </td>
        <td align=center> XXXXXXXXXXXX </td>
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

This module is supported mainly by the community and is curated by core committers.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
