.. _ec2_lc_find:


ec2_lc_find - Find AWS Autoscaling Launch Configurations
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Returns list of matching Launch Configurations for a given name, along with other useful information
* Results can be sorted and sliced
* It depends on boto
* Based on the work by Tom Bamford (https://github.com/tombamford)


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * boto3


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
                <tr><td>limit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>How many results to show.</div><div>Corresponds to Python slice notation like list[:limit].</div>        </td></tr>
                <tr><td>name_regex<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>A Launch Configuration to match</div><div>It'll be compiled as regex</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The AWS region to use.</div></br>
    <div style="font-size: small;">aliases: aws_region, ec2_region<div>        </td></tr>
                <tr><td>sort_order<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ascending</td>
        <td><ul><li>ascending</li><li>descending</li></ul></td>
        <td><div>Order in which to sort results.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note: These examples do not set authentication details, see the AWS Guide for details.
    
    # Search for the Launch Configurations that start with "app"
    - ec2_lc_find:
        name_regex: app.*
        sort_order: descending
        limit: 2

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
        <td> ram_disk_id </td>
        <td> Launch Configuration ram disk property </td>
        <td align=center> when Launch Configuration was found </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name of the AMI </td>
        <td align=center> when Launch Configuration was found </td>
        <td align=center> string </td>
        <td align=center> myapp-v123 </td>
    </tr>
            <tr>
        <td> image_id </td>
        <td> AMI id </td>
        <td align=center> when Launch Configuration was found </td>
        <td align=center> string </td>
        <td align=center> ami-0d75df7e </td>
    </tr>
            <tr>
        <td> kernel_id </td>
        <td> Launch Configuration kernel to use </td>
        <td align=center> when Launch Configuration was found </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> ebs_optimized </td>
        <td> Launch Configuration EBS optimized property </td>
        <td align=center> when Launch Configuration was found </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> user_data </td>
        <td> User data used to start instance </td>
        <td align=center> when Launch Configuration was found </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> instance_type </td>
        <td> Type of ec2 instance </td>
        <td align=center> when Launch Configuration was found </td>
        <td align=center> string </td>
        <td align=center> t2.small </td>
    </tr>
            <tr>
        <td> keyname </td>
        <td> Launch Configuration ssh key </td>
        <td align=center> when Launch Configuration was found </td>
        <td align=center> string </td>
        <td align=center> mykey </td>
    </tr>
            <tr>
        <td> arn </td>
        <td> Name of the AMI </td>
        <td align=center> when Launch Configuration was found </td>
        <td align=center> string </td>
        <td align=center> arn:aws:autoscaling:eu-west-1:12345:launchConfiguration:d82f050e-e315:launchConfigurationName/yourproject </td>
    </tr>
            <tr>
        <td> associate_public_address </td>
        <td> Assign public address or not </td>
        <td align=center> when Launch Configuration was found </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> created_time </td>
        <td> When it was created </td>
        <td align=center> when Launch Configuration was found </td>
        <td align=center> string </td>
        <td align=center> 2016-06-29T14:59:22.222000+00:00 </td>
    </tr>
            <tr>
        <td> instance_monitoring </td>
        <td> Launch Configuration instance monitoring property </td>
        <td align=center> when Launch Configuration was found </td>
        <td align=center> string </td>
        <td align=center> {'Enabled': False} </td>
    </tr>
            <tr>
        <td> classic_link_vpc_security_groups </td>
        <td> Launch Configuration classic link vpc security groups property </td>
        <td align=center> when Launch Configuration was found </td>
        <td align=center> list </td>
        <td align=center> [] </td>
    </tr>
            <tr>
        <td> security_groups </td>
        <td> Launch Configuration security groups </td>
        <td align=center> when Launch Configuration was found </td>
        <td align=center> list </td>
        <td align=center> [] </td>
    </tr>
            <tr>
        <td> block_device_mappings </td>
        <td> Launch Configuration block device mappings property </td>
        <td align=center> when Launch Configuration was found </td>
        <td align=center> list </td>
        <td align=center> [] </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
