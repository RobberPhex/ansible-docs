.. _ec2_vol:


ec2_vol - create and attach a volume, return volume id and device map
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

creates an EBS volume and optionally attaches it to an instance.  If both an instance ID and a device name is given and the instance has a device at the device name, then no volume is created and no attachment is made.  This module has a dependency on python-boto.


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
    <td>device_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>device id to override device mapping. Assumes /dev/sdf for Linux/UNIX and /dev/xvdf for Windows.</div></td></tr>
            <tr>
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>encrypted<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Enable encryption at rest for this volume.</div></td></tr>
            <tr>
    <td>id<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>volume id if you wish to attach an existing volume (requires instance) or remove an existing volume</div></td></tr>
            <tr>
    <td>instance<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>instance ID if you wish to attach the volume. Since 1.9 you can set to None to detach.</div></td></tr>
            <tr>
    <td>iops<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td>100</td>
        <td><ul></ul></td>
        <td><div>the provisioned IOPs you want to associate with this volume (integer).</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>volume Name tag if you wish to attach an existing volume (requires instance)</div></td></tr>
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
    <td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
        <div style="font-size: small;">aliases: access_token<div></td></tr>
            <tr>
    <td>snapshot<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>snapshot ID on which to base the volume</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li><li>list</li></ul></td>
        <td><div>whether to ensure the volume is present or absent, or to list existing volumes (The <code>list</code> option was added in version 1.8).</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div></td></tr>
            <tr>
    <td>volume_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>size of volume (in GB) to create.</div></td></tr>
            <tr>
    <td>volume_type<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>standard</td>
        <td><ul></ul></td>
        <td><div>Type of EBS volume; standard (magnetic), gp2 (SSD), io1 (Provisioned IOPS). "Standard" is the old EBS default and continues to remain the Ansible default for backwards compatibility.</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>zone in which to create the volume, if unset uses the zone the instance is in (if set)</div></br>
        <div style="font-size: small;">aliases: aws_zone, ec2_zone<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Simple attachment action
    - ec2_vol: 
        instance: XXXXXX 
        volume_size: 5 
        device_name: sdd
    
    # Example using custom iops params   
    - ec2_vol:
        instance: XXXXXX 
        volume_size: 5 
        iops: 100
        device_name: sdd
    
    # Example using snapshot id
    - ec2_vol:
        instance: XXXXXX
        snapshot: "{{ snapshot }}"
    
    # Playbook example combined with instance launch 
    - ec2:
        keypair: "{{ keypair }}"
        image: "{{ image }}"
        wait: yes 
        count: 3
      register: ec2
    - ec2_vol:
        instance: "{{ item.id }} " 
        volume_size: 5
      with_items: ec2.instances
      register: ec2_vol
    
    # Example: Launch an instance and then add a volume if not already attached
    #   * Volume will be created with the given name if not already created.
    #   * Nothing will happen if the volume is already attached.
    #   * Requires Ansible 2.0
    
    - ec2:
        keypair: "{{ keypair }}"
        image: "{{ image }}"
        zone: YYYYYY
        id: my_instance
        wait: yes
        count: 1
      register: ec2
    
    - ec2_vol:
        instance: "{{ item.id }}"
        name: my_existing_volume_Name_tag
        device_name: /dev/xvdf
      with_items: ec2.instances
      register: ec2_vol
    
    # Remove a volume
    - ec2_vol:
        id: vol-XXXXXXXX
        state: absent
    
    # Detach a volume (since 1.9)
    - ec2_vol:
        id: vol-XXXXXXXX
        instance: None
    
    # List volumes for an instance
    - ec2_vol:
        instance: i-XXXXXX
        state: list
    
    # Create new volume using SSD storage
    - ec2_vol:
        instance: XXXXXX
        volume_size: 50
        volume_type: gp2
        device_name: /dev/xvdf


Notes
-----

.. note:: If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

