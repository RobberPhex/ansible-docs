.. _kinesis_stream:


kinesis_stream - Manage a Kinesis Stream.
+++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create or Delete a Kinesis Stream.
Update the retention period of a Kinesis Stream.
Update Tags on a Kinesis Stream.


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
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the Kinesis Stream you are managing.</div></td></tr>
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
    <td>retention_period<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The default retention period is 24 hours and can not be less than 24 hours.</div><div>The retention period can be modified during any point in time.</div></td></tr>
            <tr>
    <td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
        <div style="font-size: small;">aliases: access_token<div></td></tr>
            <tr>
    <td>shards<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The number of shards you want to have with this stream. This can not be modified after being created.</div><div>This is required when state == present</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Create or Delete the Kinesis Stream.</div></td></tr>
            <tr>
    <td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A dictionary of resource tags of the form: { tag1: value1, tag2: value2 }.</div></br>
        <div style="font-size: small;">aliases: resource_tags<div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Wait for operation to complete before returning.</div></td></tr>
            <tr>
    <td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td><div>How many seconds to wait for an operation to complete before timing out.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note: These examples do not set authentication details, see the AWS Guide for details.
    
    # Basic creation example:
    - name: Set up Kinesis Stream with 10 shards and wait for the stream to become ACTIVE
      kinesis_stream:
        name: test-stream
        shards: 10
        wait: yes
        wait_timeout: 600
      register: test_stream
    
    # Basic creation example with tags:
    - name: Set up Kinesis Stream with 10 shards, tag the environment, and wait for the stream to become ACTIVE
      kinesis_stream:
        name: test-stream
        shards: 10
        tags:
          Env: development
        wait: yes
        wait_timeout: 600
      register: test_stream
    
    # Basic creation example with tags and increase the retention period from the default 24 hours to 48 hours:
    - name: Set up Kinesis Stream with 10 shards, tag the environment, increase the retention period and wait for the stream to become ACTIVE
      kinesis_stream:
        name: test-stream
        retention_period: 48
        shards: 10
        tags:
          Env: development
        wait: yes
        wait_timeout: 600
      register: test_stream
    
    # Basic delete example:
    - name: Delete Kinesis Stream test-stream and wait for it to finish deleting.
      kinesis_stream:
        name: test-stream
        state: absent
        wait: yes
        wait_timeout: 600
      register: test_stream

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
        <td> stream_status </td>
        <td> The current state of the Kinesis Stream. </td>
        <td align=center> when state == present. </td>
        <td align=center> string </td>
        <td align=center> ACTIVE </td>
    </tr>
            <tr>
        <td> stream_name </td>
        <td> The name of the Kinesis Stream. </td>
        <td align=center> when state == present. </td>
        <td align=center> string </td>
        <td align=center> test-stream </td>
    </tr>
            <tr>
        <td> retention_period_hours </td>
        <td> Number of hours messages will be kept for a Kinesis Stream. </td>
        <td align=center> when state == present. </td>
        <td align=center> int </td>
        <td align=center> 24 </td>
    </tr>
            <tr>
        <td> stream_arn </td>
        <td> The amazon resource identifier </td>
        <td align=center> when state == present. </td>
        <td align=center> string </td>
        <td align=center> arn:aws:kinesis:east-side:123456789:stream/test-stream </td>
    </tr>
            <tr>
        <td> tags </td>
        <td> Dictionary containing all the tags associated with the Kinesis stream. </td>
        <td align=center> when state == present. </td>
        <td align=center> dict </td>
        <td align=center> {'Name': 'Splunk', 'Env': 'development'} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

