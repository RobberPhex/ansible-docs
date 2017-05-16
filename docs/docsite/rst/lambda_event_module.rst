.. _lambda_event:


lambda_event - Creates, updates or deletes AWS Lambda function event mappings.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module allows the management of AWS Lambda function event source mappings such as DynamoDB and Kinesis stream events via the Ansible framework. These event source mappings are relevant only in the AWS Lambda pull model, where AWS Lambda invokes the function. It is idempotent and supports "Check" mode.  Use module :ref:`lambda <lambda>` to manage the lambda function itself and :ref:`lambda_alias <lambda_alias>` to manage function aliases.


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
                <tr><td>alias<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the function alias. Mutually exclusive with <code>version</code>.</div>        </td></tr>
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
                <tr><td>event_source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>stream</td>
        <td><ul><li>stream</li></ul></td>
        <td><div>Source of the event that triggers the lambda function.</div>        </td></tr>
                <tr><td>lambda_function_arn<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name or ARN of the lambda function.</div></br>
    <div style="font-size: small;">aliases: function_name, function_arn<div>        </td></tr>
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
                <tr><td>source_params<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Sub-parameters required for event source.</div><div><em>== stream event source ==</em></div><div><code>source_arn</code> The Amazon Resource Name (ARN) of the Kinesis or DynamoDB stream that is the event source.</div><div><code>enabled</code> Indicates whether AWS Lambda should begin polling the event source. Default is True.</div><div><code>batch_size</code> The largest number of records that AWS Lambda will retrieve from your event source at the time of invoking your function. Default is 100.</div><div><code>starting_position</code> The position in the stream where AWS Lambda should start reading. Choices are TRIM_HORIZON or LATEST.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Describes the desired state.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div>        </td></tr>
                <tr><td>version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Version of the Lambda function. Mutually exclusive with <code>alias</code>.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    ---
    # Example that creates a lambda event notification for a DynamoDB stream
    - hosts: localhost
      gather_facts: no
      vars:
        state: present
      tasks:
      - name: DynamoDB stream event mapping
        lambda_event:
          state: "{{ state | default('present') }}"
          event_source: stream
          function_name: "{{ function_name }}"
          alias: Dev
          source_params:
            source_arn: arn:aws:dynamodb:us-east-1:123456789012:table/tableName/stream/2016-03-19T19:51:37.457
            enabled: True
            batch_size: 100
            starting_position: TRIM_HORIZON
    
      - name: Show source event
        debug:
          var: lambda_stream_events

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
        <td> lambda_stream_events </td>
        <td> list of dictionaries returned by the API describing stream event mappings </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center>  </td>
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
