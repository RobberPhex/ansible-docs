.. _ec2_lc_facts:


ec2_lc_facts - Gather facts about AWS Autoscaling Launch Configurations
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Gather facts about AWS Autoscaling Launch Configurations


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
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A name or a list of name to match.</div>        </td></tr>
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
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>sort<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>launch_configuration_name</li><li>image_id</li><li>created_time</li><li>instance_type</li><li>kernel_id</li><li>ramdisk_id</li><li>key_name</li></ul></td>
        <td><div>Optional attribute which with to sort the results.</div>        </td></tr>
                <tr><td>sort_end<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Which result to end with (when sorting).</div><div>Corresponds to Python slice notation.</div>        </td></tr>
                <tr><td>sort_order<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ascending</td>
        <td><ul><li>ascending</li><li>descending</li></ul></td>
        <td><div>Order in which to sort results.</div><div>Only used when the 'sort' parameter is specified.</div>        </td></tr>
                <tr><td>sort_start<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Which result to start with (when sorting).</div><div>Corresponds to Python slice notation.</div>        </td></tr>
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

    # Note: These examples do not set authentication details, see the AWS Guide for details.
    
    # Gather facts about all launch configurations
    - ec2_lc_facts:
    
    # Gather facts about launch configuration with name "example"
    - ec2_lc_facts:
        name: example
    
    # Gather facts sorted by created_time from most recent to least recent
    - ec2_lc_facts:
        sort: created_time
        sort_order: descending

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
        <td> ramdisk_id </td>
        <td> ID of the RAM disk associated with the AMI </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> None </td>
    </tr>
            <tr>
        <td> block_device_mapping </td>
        <td> Block device mapping for the instances of launch configuration </td>
        <td align=center>  </td>
        <td align=center> list of block devices </td>
        <td align=center> [{ 'device_name': '/dev/xvda':, 'ebs': { 'delete_on_termination': true, 'volume_size': 8, 'volume_type': 'gp2' }] </td>
    </tr>
            <tr>
        <td> kernel_id </td>
        <td> ID of the kernel associated with the AMI </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> None </td>
    </tr>
            <tr>
        <td> key_name </td>
        <td> Name of the key pair </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> user_app </td>
    </tr>
            <tr>
        <td> launch_configuration_name </td>
        <td> Name of the launch configuration </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> lc-app </td>
    </tr>
            <tr>
        <td> ebs_optimized </td>
        <td> EBS I/O optimized (true ) or not (false ) </td>
        <td align=center>  </td>
        <td align=center> bool </td>
        <td align=center> true, </td>
    </tr>
            <tr>
        <td> user_data </td>
        <td> User data available </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> None </td>
    </tr>
            <tr>
        <td> image_id </td>
        <td> ID of the Amazon Machine Image (AMI) </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> ami-12345678 </td>
    </tr>
            <tr>
        <td> instance_type </td>
        <td> Instance type </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> t2.micro </td>
    </tr>
            <tr>
        <td> created_time </td>
        <td> The creation date and time for the launch configuration </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> 2016-05-27T13:47:44.216000+00:00 </td>
    </tr>
            <tr>
        <td> instance_monitoring </td>
        <td> Launched with detailed monitoring or not </td>
        <td align=center>  </td>
        <td align=center> dict </td>
        <td align=center> { 'enabled': true } </td>
    </tr>
            <tr>
        <td> launch_configuration_arn </td>
        <td> Amazon Resource Name (ARN) of the launch configuration </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> arn:aws:autoscaling:us-east-1:666612345678:launchConfiguration:ba785e3a-dd42-6f02-4585-ea1a2b458b3d:launchConfigurationName/lc-app </td>
    </tr>
            <tr>
        <td> security_groups </td>
        <td> Security groups to associated </td>
        <td align=center>  </td>
        <td align=center> list </td>
        <td align=center> [ 'web' ] </td>
    </tr>
            <tr>
        <td> classic_link_vpc_security_groups </td>
        <td> IDs of one or more security groups for the VPC specified in classic_link_vpc_id </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> None </td>
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
