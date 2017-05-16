.. _cloudwatchevent_rule:


cloudwatchevent_rule - Manage CloudWatch Event rules and targets
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module creates and manages CloudWatch event rules and targets.


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
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A description of the rule</div></td></tr>
            <tr>
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>event_pattern<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A string pattern (in valid JSON format) that is used to match against incoming events to determine if the rule should be triggered</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the rule you are creating, updating or deleting. No spaces or special characters allowed (i.e. must match <code>[\.\-_A-Za-z0-9]+</code>)</div></td></tr>
            <tr>
    <td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>uses a boto profile. Only works with boto &gt;= 2.24.0</div></td></tr>
            <tr>
    <td>role_arn<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The Amazon Resource Name (ARN) of the IAM role associated with the rule</div></td></tr>
            <tr>
    <td>schedule_expression<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A cron or rate expression that defines the schedule the rule will trigger on. For example, <code>cron(0 20 * * ? *</code>), <code>rate(5 minutes</code>)</div></td></tr>
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
        <td><ul><li>present</li><li>disabled</li><li>absent</li></ul></td>
        <td><div>Whether the rule is present (and enabled), disabled, or absent</div></td></tr>
            <tr>
    <td>targets<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A dictionary array of targets to add to or update for the rule, in the form <code>{ id: [string], arn: [string], input: [valid JSON string], input_path: [valid JSONPath string] }</code>. <em>id</em> [required] is the unique target assignment ID. <em>arn</em> (required) is the Amazon Resource Name associated with the target. <em>input</em> (optional) is a JSON object that will override the event data when passed to the target.  <em>input_path</em> (optional) is a JSONPath string (e.g. <code>$.detail</code>) that specifies the part of the event data to be passed to the target. If neither <em>input</em> nor <em>input_path</em> is specified, then the entire event is passed to the target in JSON form.</div></td></tr>
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

    - cloudwatchevent_rule:
        name: MyCronTask
        schedule_expression: "cron(0 20 * * ? *)"
        description: Run my scheduled task
        targets:
          - id: MyTargetId
            arn: arn:aws:lambda:us-east-1:123456789012:function:MyFunction
    
    - cloudwatchevent_rule:
        name: MyDisabledCronTask
        schedule_expression: "cron(5 minutes)"
        description: Run my disabled scheduled task
        state: disabled
        targets:
          - id: MyOtherTargetId
            arn: arn:aws:lambda:us-east-1:123456789012:function:MyFunction
            input: '{"foo": "bar"}'
    
    - cloudwatchevent_rule: name=MyCronTask state=absent

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
        <td> targets </td>
        <td> CloudWatch Event target(s) assigned to the rule </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> [{ 'arn': 'arn:aws:lambda:us-east-1:123456789012:function:MyFunction', 'id': 'MyTargetId' }] </td>
    </tr>
            <tr>
        <td> rule </td>
        <td> CloudWatch Event rule data </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> { 'arn': 'arn:aws:events:us-east-1:123456789012:rule/MyCronTask', 'description': 'Run my scheduled task', 'name': 'MyCronTask', 'schedule_expression': 'cron(0 20 * * ? *)', 'state': 'ENABLED' } </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: A rule must contain at least an *event_pattern* or *schedule_expression*. A rule can have both an *event_pattern* and a *schedule_expression*, in which case the rule will trigger on matching events as well as on a schedule.
.. note:: When specifying targets, *input* and *input_path* are mutually-exclusive and optional parameters.
.. note:: If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

