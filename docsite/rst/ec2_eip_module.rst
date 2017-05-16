.. _ec2_eip:


ec2_eip - manages EC2 elastic IP (EIP) addresses.
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module can allocate or release an EIP.
This module can associate/disassociate an EIP with instances or network interfaces.


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
    <td>device_id<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The id of the device for the EIP. Can be an EC2 Instance id or Elastic Network Interface (ENI) id.</div></br>
        <div style="font-size: small;">aliases: instance_id<div></td></tr>
            <tr>
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>in_vpc<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>allocate an EIP inside a VPC or not</div></td></tr>
            <tr>
    <td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>uses a boto profile. Only works with boto &gt;= 2.24.0</div></td></tr>
            <tr>
    <td>public_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The IP address of a previously allocated EIP.</div><div>If present and device is specified, the EIP is associated with the device.</div><div>If absent and device is specified, the EIP is disassociated from the device.</div></br>
        <div style="font-size: small;">aliases: ip<div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The AWS region to use. If not specified then the value of the AWS_REGION or EC2_REGION environment variable, if any, is used. See <a href='http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region'>http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region</a></div></br>
        <div style="font-size: small;">aliases: aws_region, ec2_region<div></td></tr>
            <tr>
    <td>release_on_disassociation<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>whether or not to automatically release the EIP when it is disassociated</div></td></tr>
            <tr>
    <td>reuse_existing_ip_allowed<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Reuse an EIP that is not associated to a device (when available), instead of allocating a new one.</div></td></tr>
            <tr>
    <td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
        <div style="font-size: small;">aliases: access_token<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>If present, allocate an EIP or associate an existing EIP with a device.</div><div>If absent, disassociate the EIP from the device and optionally release it.</div></td></tr>
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

    - name: associate an elastic IP with an instance
      ec2_eip: device_id=i-1212f003 ip=93.184.216.119
    - name: associate an elastic IP with a device
      ec2_eip: device_id=eni-c8ad70f3 ip=93.184.216.119
    - name: disassociate an elastic IP from an instance
      ec2_eip: device_id=i-1212f003 ip=93.184.216.119 state=absent
    - name: disassociate an elastic IP with a device
      ec2_eip: device_id=eni-c8ad70f3 ip=93.184.216.119 state=absent
    - name: allocate a new elastic IP and associate it with an instance
      ec2_eip: device_id=i-1212f003
    - name: allocate a new elastic IP without associating it to anything
      action: ec2_eip
      register: eip
    - name: output the IP
      debug: msg="Allocated IP is {{ eip.public_ip }}"
    - name: another way of allocating an elastic IP without associating it to anything
      ec2_eip: state='present'
    - name: provision new instances with ec2
      ec2: keypair=mykey instance_type=c1.medium image=ami-40603AD1 wait=yes


Notes
-----

.. note:: This module will return ``public_ip`` on success, which will contain the public IP address associated with the device.
.. note:: There may be a delay between the time the EIP is assigned and when the cloud instance is reachable via the new address. Use wait_for and pause to delay further playbook execution until the instance is reachable, if necessary.
.. note:: This module returns multiple changed statuses on disassociation or release. It returns an overall status based on any changes occuring. It also returns individual changed statuses for disassociation and release.
.. note:: If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

