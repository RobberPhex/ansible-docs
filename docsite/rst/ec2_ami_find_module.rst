.. _ec2_ami_find:


ec2_ami_find - Searches for AMIs to obtain the AMI ID and other information
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Returns list of matching AMIs with AMI ID, along with other useful information
Can search AMIs with different owners
Can search by matching tag(s), by AMI name and/or other criteria
Results can be sorted and sliced


Requirements
------------

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
    <td>ami_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>An AMI ID to match.</div></td></tr>
            <tr>
    <td>ami_tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A hash/dictionary of tags to match for the AMI.</div></td></tr>
            <tr>
    <td>architecture<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>An architecture type to match (e.g. x86_64).</div></td></tr>
            <tr>
    <td>hypervisor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A hypervisor type type to match (e.g. xen).</div></td></tr>
            <tr>
    <td>is_public<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether or not the image(s) are public.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>An AMI name to match.</div></td></tr>
            <tr>
    <td>no_result_action<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>success</td>
        <td><ul><li>success</li><li>fail</li></ul></td>
        <td><div>What to do when no results are found.</div><div>'success' reports success and returns an empty array</div><div>'fail' causes the module to report failure</div></td></tr>
            <tr>
    <td>owner<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Search AMIs owned by the specified owner</div><div>Can specify an AWS account ID, or one of the special IDs 'self', 'amazon' or 'aws-marketplace'</div><div>If not specified, all EC2 AMIs in the specified region will be searched.</div><div>You can include wildcards in many of the search options. An asterisk (*) matches zero or more characters, and a question mark (?) matches exactly one character. You can escape special characters using a backslash (\) before the character. For example, a value of \*amazon\?\ searches for the literal string *amazon?\.</div></td></tr>
            <tr>
    <td>platform<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Platform type to match.</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The AWS region to use.</div></br>
        <div style="font-size: small;">aliases: aws_region, ec2_region<div></td></tr>
            <tr>
    <td>sort<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>name</li><li>description</li><li>tag</li></ul></td>
        <td><div>Optional attribute which with to sort the results.</div><div>If specifying 'tag', the 'tag_name' parameter is required.</div></td></tr>
            <tr>
    <td>sort_end<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Which result to end with (when sorting).</div><div>Corresponds to Python slice notation.</div></td></tr>
            <tr>
    <td>sort_order<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ascending</td>
        <td><ul><li>ascending</li><li>descending</li></ul></td>
        <td><div>Order in which to sort results.</div><div>Only used when the 'sort' parameter is specified.</div></td></tr>
            <tr>
    <td>sort_start<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Which result to start with (when sorting).</div><div>Corresponds to Python slice notation.</div></td></tr>
            <tr>
    <td>sort_tag<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Tag name with which to sort results.</div><div>Required when specifying 'sort=tag'.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>available</td>
        <td><ul></ul></td>
        <td><div>AMI state to match.</div></td></tr>
            <tr>
    <td>virtualization_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Virtualization type to match (e.g. hvm).</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note: These examples do not set authentication details, see the AWS Guide for details.
    
    # Search for the AMI tagged "project:website"
    - ec2_ami_find:
        owner: self
        ami_tags:
          project: website
        no_result_action: fail
      register: ami_find
    
    # Search for the latest Ubuntu 14.04 AMI
    - ec2_ami_find:
        name: "ubuntu/images/ebs/ubuntu-trusty-14.04-amd64-server-*"
        owner: 099720109477
        sort: name
        sort_order: descending
        sort_end: 1
      register: ami_find
    
    # Launch an EC2 instance
    - ec2:
        image: "{{ ami_find.results[0].ami_id }}"
        instance_type: m3.medium
        key_name: mykey
        wait: yes

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
        <td> root_device_type </td>
        <td> rood device type of image </td>
        <td align=center> when AMI found </td>
        <td align=center> string </td>
        <td align=center> ebs </td>
    </tr>
            <tr>
        <td> description </td>
        <td> description of image </td>
        <td align=center> when AMI found </td>
        <td align=center> string </td>
        <td align=center> test-server01 </td>
    </tr>
            <tr>
        <td> block_device_mapping </td>
        <td> block device mapping associated with image </td>
        <td align=center> when AMI found </td>
        <td align=center> dictionary of block devices </td>
        <td align=center> { '/dev/xvda': { 'delete_on_termination': true, 'encrypted': false, 'size': 8, 'snapshot_id': 'snap-ca0330b8', 'volume_type': 'gp2' } </td>
    </tr>
            <tr>
        <td> is_public </td>
        <td> whether image is public </td>
        <td align=center> when AMI found </td>
        <td align=center> bool </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> creationDate </td>
        <td> creation date of image </td>
        <td align=center> when AMI found </td>
        <td align=center> string </td>
        <td align=center> 2015-10-15T22:43:44.000Z </td>
    </tr>
            <tr>
        <td> root_device_name </td>
        <td> rood device name of image </td>
        <td align=center> when AMI found </td>
        <td align=center> string </td>
        <td align=center> /dev/xvda </td>
    </tr>
            <tr>
        <td> ami_id </td>
        <td> id of found amazon image </td>
        <td align=center> when AMI found </td>
        <td align=center> string </td>
        <td align=center> ami-e9095e8c </td>
    </tr>
            <tr>
        <td> name </td>
        <td> ami name of image </td>
        <td align=center> when AMI found </td>
        <td align=center> string </td>
        <td align=center> test-server01-20151015-234343 </td>
    </tr>
            <tr>
        <td> hypervisor </td>
        <td> type of hypervisor </td>
        <td align=center> when AMI found </td>
        <td align=center> string </td>
        <td align=center> xen </td>
    </tr>
            <tr>
        <td> tags </td>
        <td> tags assigned to image </td>
        <td align=center> when AMI found </td>
        <td align=center> dictionary of tags </td>
        <td align=center> { 'Environment': 'devel', 'Name': 'test-server01', 'Role': 'web' } </td>
    </tr>
            <tr>
        <td> location </td>
        <td> location of image </td>
        <td align=center> when AMI found </td>
        <td align=center> string </td>
        <td align=center> 435210894375/test-server01-20151015-234343 </td>
    </tr>
            <tr>
        <td> platform </td>
        <td> plaform of image </td>
        <td align=center> when AMI found </td>
        <td align=center> string </td>
        <td align=center> None </td>
    </tr>
            <tr>
        <td> state </td>
        <td> state of image </td>
        <td align=center> when AMI found </td>
        <td align=center> string </td>
        <td align=center> available </td>
    </tr>
            <tr>
        <td> architecture </td>
        <td> architecture of image </td>
        <td align=center> when AMI found </td>
        <td align=center> string </td>
        <td align=center> x86_64 </td>
    </tr>
            <tr>
        <td> virtualization_type </td>
        <td> image virtualization type </td>
        <td align=center> when AMI found </td>
        <td align=center> string </td>
        <td align=center> hvm </td>
    </tr>
            <tr>
        <td> owner_id </td>
        <td> owner of image </td>
        <td align=center> when AMI found </td>
        <td align=center> string </td>
        <td align=center> 435210894375 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: This module is not backwards compatible with the previous version of the ec2_search_ami module which worked only for Ubuntu AMIs listed on cloud-images.ubuntu.com.
.. note:: See the example below for a suggestion of how to search by distro/release.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

