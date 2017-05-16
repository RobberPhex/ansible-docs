.. _s3_lifecycle:


s3_lifecycle - Manage s3 bucket lifecycle rules in AWS
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage s3 bucket lifecycle rules in AWS


Requirements (on host that executes module)
-------------------------------------------

  * boto
  * python >= 2.6
  * python-dateutil


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
                <tr><td>expiration_date<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Indicates the lifetime of the objects that are subject to the rule by the date they will expire. The value must be ISO-8601 format, the time must be midnight and a GMT timezone must be specified.</div>        </td></tr>
                <tr><td>expiration_days<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Indicates the lifetime, in days, of the objects that are subject to the rule. The value must be a non-zero positive integer.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the s3 bucket</div>        </td></tr>
                <tr><td>prefix<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Prefix identifying one or more objects to which the rule applies.  If no prefix is specified, the rule will apply to the whole bucket.</div>        </td></tr>
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
                <tr><td>rule_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Unique identifier for the rule. The value cannot be longer than 255 characters. A unique value for the rule will be generated if no value is provided.</div>        </td></tr>
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Create or remove the lifecycle rule</div>        </td></tr>
                <tr><td>status<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>enabled</td>
        <td><ul><li>enabled</li><li>disabled</li></ul></td>
        <td><div>If 'enabled', the rule is currently being applied. If 'disabled', the rule is not currently being applied.</div>        </td></tr>
                <tr><td>storage_class<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>glacier</td>
        <td><ul><li>glacier</li><li>standard_ia</li></ul></td>
        <td><div>The storage class to transition to. Currently there are two supported values - 'glacier' or 'standard_ia'.</div><div>The 'standard_ia' class is only being available from Ansible version 2.2.</div>        </td></tr>
                <tr><td>transition_date<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Indicates the lifetime of the objects that are subject to the rule by the date they will transition to a different storage class. The value must be ISO-8601 format, the time must be midnight and a GMT timezone must be specified. If transition_days is not specified, this parameter is required.</div>        </td></tr>
                <tr><td>transition_days<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Indicates when, in days, an object transitions to a different storage class. If transition_date is not specified, this parameter is required.</div>        </td></tr>
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
    
    # Configure a lifecycle rule on a bucket to expire (delete) items with a prefix of /logs/ after 30 days
    - s3_lifecycle:
        name: mybucket
        expiration_days: 30
        prefix: /logs/
        status: enabled
        state: present
    
    # Configure a lifecycle rule to transition all items with a prefix of /logs/ to glacier after 7 days and then delete after 90 days
    - s3_lifecycle:
        name: mybucket
        transition_days: 7
        expiration_days: 90
        prefix: /logs/
        status: enabled
        state: present
    
    # Configure a lifecycle rule to transition all items with a prefix of /logs/ to glacier on 31 Dec 2020 and then delete on 31 Dec 2030. Note that midnight GMT must be specified.
    # Be sure to quote your date strings
    - s3_lifecycle:
        name: mybucket
        transition_date: "2020-12-30T00:00:00.000Z"
        expiration_date: "2030-12-30T00:00:00.000Z"
        prefix: /logs/
        status: enabled
        state: present
    
    # Disable the rule created above
    - s3_lifecycle:
        name: mybucket
        prefix: /logs/
        status: disabled
        state: present
    
    # Delete the lifecycle rule created above
    - s3_lifecycle:
        name: mybucket
        prefix: /logs/
        state: absent
    
    # Configure a lifecycle rule to transition all backup files older than 31 days in /backups/ to standard infrequent access class.
    - s3_lifecycle:
        name: mybucket
        prefix: /backups/
        storage_class: standard_ia
        transition_days: 31
        state: present
        status: enabled
    


Notes
-----

.. note::
    - If specifying expiration time as days then transition time must also be specified in days
    - If specifying expiration time as a date then transition time must also be specified as a date
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
