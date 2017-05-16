.. _ec2_ami:


ec2_ami - create or destroy an image in ec2
+++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Creates or deletes ec2 images.


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
                <tr><td>architecture<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The target architecture of the image to register</div>        </td></tr>
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
                <tr><td>delete_snapshot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Delete snapshots when deregistering the AMI.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Human-readable string describing the contents and purpose of the AMI.</div>        </td></tr>
                <tr><td>device_mapping<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of device hashes/dictionaries with custom configurations (same block-device-mapping parameters)</div><div>Valid properties include: device_name, volume_type, size (in GB), delete_on_termination (boolean), no_device (boolean), snapshot_id, iops (for io1 volume_type)</div>        </td></tr>
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>image_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Image ID to be deregistered.</div>        </td></tr>
                <tr><td>instance_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Instance ID to create the AMI from.</div>        </td></tr>
                <tr><td>kernel_id<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The target kernel id of the image to register</div>        </td></tr>
                <tr><td>launch_permissions<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Users and groups that should be able to launch the AMI. Expects dictionary with a key of user_ids and/or group_names. user_ids should be a list of account ids. group_name should be a list of groups, "all" is the only acceptable value currently.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of the new AMI.</div>        </td></tr>
                <tr><td>no_reboot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Flag indicating that the bundling process should not attempt to shutdown the instance before bundling. If this flag is True, the responsibility of maintaining file system integrity is left to the owner of the instance.</div>        </td></tr>
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
                <tr><td>root_device_name<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The root device name of the image to register</div>        </td></tr>
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>Create or deregister/delete AMI.</div>        </td></tr>
                <tr><td>tags<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A dictionary of tags to add to the new image; '{"key":"value"}' and '{"key":"value","key":"value"}'</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div>        </td></tr>
                <tr><td>virtualization_type<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The virtualization type of the image to register</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Wait for the AMI to be in state 'available' before returning.</div>        </td></tr>
                <tr><td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td></td>
        <td><div>How long before wait gives up, in seconds.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Basic AMI Creation
    - ec2_ami:
        aws_access_key: xxxxxxxxxxxxxxxxxxxxxxx
        aws_secret_key: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
        instance_id: i-xxxxxx
        wait: yes
        name: newtest
        tags:
          Name: newtest
          Service: TestService
      register: image
    
    # Basic AMI Creation, without waiting
    - ec2_ami:
        aws_access_key: xxxxxxxxxxxxxxxxxxxxxxx
        aws_secret_key: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
        region: xxxxxx
        instance_id: i-xxxxxx
        wait: no
        name: newtest
      register: image
    
    # AMI Registration from EBS Snapshot
    - ec2_ami:
        aws_access_key: xxxxxxxxxxxxxxxxxxxxxxx
        aws_secret_key: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
        region: xxxxxx
        name: newtest
        state: present
        architecture: x86_64
        virtualization_type: hvm
        root_device_name: /dev/xvda
        device_mapping:
          - device_name: /dev/xvda
            size: 8
            snapshot_id: snap-xxxxxxxx
            delete_on_termination: true
            volume_type: gp2
      register: image
    
    # AMI Creation, with a custom root-device size and another EBS attached
    - ec2_ami:
        aws_access_key: xxxxxxxxxxxxxxxxxxxxxxx
        aws_secret_key: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
        instance_id: i-xxxxxx
        name: newtest
        device_mapping:
            - device_name: /dev/sda1
              size: XXX
              delete_on_termination: true
              volume_type: gp2
            - device_name: /dev/sdb
              size: YYY
              delete_on_termination: false
              volume_type: gp2
      register: image
    
    # AMI Creation, excluding a volume attached at /dev/sdb
    - ec2_ami:
        aws_access_key: xxxxxxxxxxxxxxxxxxxxxxx
        aws_secret_key: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
        instance_id: i-xxxxxx
        name: newtest
        device_mapping:
            - device_name: /dev/sda1
              size: XXX
              delete_on_termination: true
              volume_type: gp2
            - device_name: /dev/sdb
              no_device: yes
      register: image
    
    # Deregister/Delete AMI (keep associated snapshots)
    - ec2_ami:
        aws_access_key: xxxxxxxxxxxxxxxxxxxxxxx
        aws_secret_key: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
        region: xxxxxx
        image_id: "{{ instance.image_id }}"
        delete_snapshot: False
        state: absent
    
    # Deregister AMI (delete associated snapshots too)
    - ec2_ami:
        aws_access_key: xxxxxxxxxxxxxxxxxxxxxxx
        aws_secret_key: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
        region: xxxxxx
        image_id: "{{ instance.image_id }}"
        delete_snapshot: True
        state: absent
    
    # Update AMI Launch Permissions, making it public
    - ec2_ami:
        aws_access_key: xxxxxxxxxxxxxxxxxxxxxxx
        aws_secret_key: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
        region: xxxxxx
        image_id: "{{ instance.image_id }}"
        state: present
        launch_permissions:
          group_names: ['all']
    
    # Allow AMI to be launched by another account
    - ec2_ami:
        aws_access_key: xxxxxxxxxxxxxxxxxxxxxxx
        aws_secret_key: xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
        region: xxxxxx
        image_id: "{{ instance.image_id }}"
        state: present
        launch_permissions:
          user_ids: ['123456789012']

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
        <td> root device type of image </td>
        <td align=center> when AMI is created or already exists </td>
        <td align=center> string </td>
        <td align=center> ebs </td>
    </tr>
            <tr>
        <td> description </td>
        <td> description of image </td>
        <td align=center> when AMI is created or already exists </td>
        <td align=center> string </td>
        <td align=center> nat-server </td>
    </tr>
            <tr>
        <td> block_device_mapping </td>
        <td> block device mapping associated with image </td>
        <td align=center> when AMI is created or already exists </td>
        <td align=center> a dictionary of block devices </td>
        <td align=center> {'/dev/sda1': {'encrypted': False, 'size': 10, 'delete_on_termination': True, 'volume_type': 'standard', 'snapshot_id': 'snap-1a03b80e7'}} </td>
    </tr>
            <tr>
        <td> image_id </td>
        <td> id of the image </td>
        <td align=center> when AMI is created or already exists </td>
        <td align=center> string </td>
        <td align=center> ami-1234abcd </td>
    </tr>
            <tr>
        <td> is_public </td>
        <td> whether image is public </td>
        <td align=center> when AMI is created or already exists </td>
        <td align=center> bool </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> creationDate </td>
        <td> creation date of image </td>
        <td align=center> when AMI is created or already exists </td>
        <td align=center> string </td>
        <td align=center> 2015-10-15T22:43:44.000Z </td>
    </tr>
            <tr>
        <td> name </td>
        <td> ami name of image </td>
        <td align=center> when AMI is created or already exists </td>
        <td align=center> string </td>
        <td align=center> nat-server </td>
    </tr>
            <tr>
        <td> hypervisor </td>
        <td> type of hypervisor </td>
        <td align=center> when AMI is created or already exists </td>
        <td align=center> string </td>
        <td align=center> xen </td>
    </tr>
            <tr>
        <td> tags </td>
        <td> a dictionary of tags assigned to image </td>
        <td align=center> when AMI is created or already exists </td>
        <td align=center> dictionary of tags </td>
        <td align=center> {'Name': 'nat-server', 'Env': 'devel'} </td>
    </tr>
            <tr>
        <td> snapshots_deleted </td>
        <td> a list of snapshot ids deleted after deregistering image </td>
        <td align=center> after AMI is deregistered, if 'delete_snapshot' is set to 'yes' </td>
        <td align=center> list </td>
        <td align=center> ['snap-fbcccb8f', 'snap-cfe7cdb4'] </td>
    </tr>
            <tr>
        <td> location </td>
        <td> location of image </td>
        <td align=center> when AMI is created or already exists </td>
        <td align=center> string </td>
        <td align=center> 315210894379/nat-server </td>
    </tr>
            <tr>
        <td> platform </td>
        <td> platform of image </td>
        <td align=center> when AMI is created or already exists </td>
        <td align=center> string </td>
        <td align=center> None </td>
    </tr>
            <tr>
        <td> state </td>
        <td> state of image </td>
        <td align=center> when AMI is created or already exists </td>
        <td align=center> string </td>
        <td align=center> available </td>
    </tr>
            <tr>
        <td> root_device_name </td>
        <td> root device name of image </td>
        <td align=center> when AMI is created or already exists </td>
        <td align=center> string </td>
        <td align=center> /dev/sda1 </td>
    </tr>
            <tr>
        <td> ownerId </td>
        <td> owner of image </td>
        <td align=center> when AMI is created or already exists </td>
        <td align=center> string </td>
        <td align=center> 435210894375 </td>
    </tr>
            <tr>
        <td> virtualization_type </td>
        <td> image virtualization type </td>
        <td align=center> when AMI is created or already exists </td>
        <td align=center> string </td>
        <td align=center> hvm </td>
    </tr>
            <tr>
        <td> architecture </td>
        <td> architecture of image </td>
        <td align=center> when AMI is created or already exists </td>
        <td align=center> string </td>
        <td align=center> x86_64 </td>
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
