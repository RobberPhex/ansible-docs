.. _ec2_snapshot_facts:


ec2_snapshot_facts - Gather facts about ec2 volume snapshots in AWS
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Gather facts about ec2 volume snapshots in AWS


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
                <tr><td>filters<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A dict of filters to apply. Each dict item consists of a filter key and a filter value. See       <a href='http://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeSnapshots.html'>http://docs.aws.amazon.com/AWSEC2/latest/APIReference/API_DescribeSnapshots.html</a> for possible filters. Filter       names and values are case sensitive.</div>        </td></tr>
                <tr><td>owner_ids<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If you specify one or more snapshot owners, only snapshots from the specified owners and for which you have       access are returned.</div>        </td></tr>
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
                <tr><td>restorable_by_user_ids<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If you specify a list of restorable users, only snapshots with create snapshot permissions for those users are       returned.</div>        </td></tr>
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>snapshot_ids<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If you specify one or more snapshot IDs, only snapshots that have the specified IDs are returned.</div>        </td></tr>
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
    
    # Gather facts about all snapshots, including public ones
    - ec2_snapshot_facts:
    
    # Gather facts about all snapshots owned by the account 0123456789
    - ec2_snapshot_facts:
        filters:
          owner-id: 0123456789
    
    # Or alternatively...
    - ec2_snapshot_facts:
        owner_ids:
          - 0123456789
    
    # Gather facts about a particular snapshot using ID
    - ec2_snapshot_facts:
        filters:
          snapshot-id: snap-00112233
    
    # Or alternatively...
    - ec2_snapshot_facts:
        snapshot_ids:
          - snap-00112233
    
    # Gather facts about any snapshot with a tag key Name and value Example
    - ec2_snapshot_facts:
        filters:
          "tag:Name": Example
    
    # Gather facts about any snapshot with an error status
    - ec2_snapshot_facts:
        filters:
          status: error
    

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
        <td> state_message </td>
        <td> Encrypted Amazon EBS snapshots are copied asynchronously. If a snapshot copy operation fails (for example, if the proper AWS Key Management Service (AWS KMS) permissions are not obtained) this field displays error state details to help you diagnose why the error occurred. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> None </td>
    </tr>
            <tr>
        <td> description </td>
        <td> The description for the snapshot. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> My important backup </td>
    </tr>
            <tr>
        <td> volume_id </td>
        <td> The ID of the volume that was used to create the snapshot. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> vol-01234567 </td>
    </tr>
            <tr>
        <td> owner_alias </td>
        <td> The AWS account alias (for example, amazon, self) or AWS account ID that owns the snapshot. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> 3699410057 </td>
    </tr>
            <tr>
        <td> encrypted </td>
        <td> Indicates whether the snapshot is encrypted. </td>
        <td align=center>  </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> start_time </td>
        <td> The time stamp when the snapshot was initiated. </td>
        <td align=center>  </td>
        <td align=center> datetime </td>
        <td align=center> 2015-02-12 02:14:02 </td>
    </tr>
            <tr>
        <td> kms_key_id </td>
        <td> The full ARN of the AWS Key Management Service (AWS KMS) customer master key (CMK) that was used to     protect the volume encryption key for the parent volume. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> 74c9742a-a1b2-45cb-b3fe-abcdef123456 </td>
    </tr>
            <tr>
        <td> data_encryption_key_id </td>
        <td> The data encryption key identifier for the snapshot. This value is a unique identifier that     corresponds to the data encryption key that was used to encrypt the original volume or snapshot copy. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> arn:aws:kms:ap-southeast-2:012345678900:key/74c9742a-a1b2-45cb-b3fe-abcdef123456 </td>
    </tr>
            <tr>
        <td> volume_size </td>
        <td> The size of the volume, in GiB. </td>
        <td align=center>  </td>
        <td align=center> integer </td>
        <td align=center> 8 </td>
    </tr>
            <tr>
        <td> state </td>
        <td> The snapshot state (completed, pending or error). </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> completed </td>
    </tr>
            <tr>
        <td> snapshot_id </td>
        <td> The ID of the snapshot. Each snapshot receives a unique identifier when it is created. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> snap-01234567 </td>
    </tr>
            <tr>
        <td> progress </td>
        <td> The progress of the snapshot, as a percentage. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> 100% </td>
    </tr>
            <tr>
        <td> tags </td>
        <td> Any tags assigned to the snapshot. </td>
        <td align=center>  </td>
        <td align=center> dict </td>
        <td align=center> { 'my_tag_key': 'my_tag_value' } </td>
    </tr>
            <tr>
        <td> owner_id </td>
        <td> The AWS account ID of the EBS snapshot owner. </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> 099720109477 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - By default, the module will return all snapshots, including public ones. To limit results to snapshots owned by   the account use the filter 'owner-id'.
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
