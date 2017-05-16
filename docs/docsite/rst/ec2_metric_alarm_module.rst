.. _ec2_metric_alarm:


ec2_metric_alarm - Create/update or delete AWS Cloudwatch 'metric alarms'
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Can create or delete AWS metric alarms.
* Metrics you wish to alarm on must already exist.


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
                <tr><td>alarm_actions<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A list of the names action(s) taken when the alarm is in the 'alarm' status</div>        </td></tr>
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
                <tr><td>comparison<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li><=</li><li><</li><li>></li><li>>=</li></ul></td>
        <td><div>Determines how the threshold value is compared</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A longer description of the alarm</div>        </td></tr>
                <tr><td>dimensions<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Describes to what the alarm is applied</div>        </td></tr>
                <tr><td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints). Ignored for modules where region is required. Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div>        </td></tr>
                <tr><td>evaluation_periods<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The number of times in which the metric is evaluated before final calculation</div>        </td></tr>
                <tr><td>insufficient_data_actions<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A list of the names of action(s) to take when the alarm is in the 'insufficient_data' status</div>        </td></tr>
                <tr><td>metric<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the monitored metric (e.g. CPUUtilization)</div><div>Metric must already exist</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Unique name for the alarm</div>        </td></tr>
                <tr><td>namespace<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the appropriate namespace ('AWS/EC2', 'System/Linux', etc.), which determines the category it will appear under in cloudwatch</div>        </td></tr>
                <tr><td>ok_actions<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A list of the names of action(s) to take when the alarm is in the 'ok' status</div>        </td></tr>
                <tr><td>period<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The time (in seconds) between metric evaluations</div>        </td></tr>
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
                <tr><td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
    <div style="font-size: small;">aliases: access_token<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>register or deregister the alarm</div>        </td></tr>
                <tr><td>statistic<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>SampleCount</li><li>Average</li><li>Sum</li><li>Minimum</li><li>Maximum</li></ul></td>
        <td><div>Operation applied to the metric</div><div>Works in conjunction with period and evaluation_periods to determine the comparison value</div>        </td></tr>
                <tr><td>threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sets the min/max bound for triggering the alarm</div>        </td></tr>
                <tr><td>unit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>Seconds</li><li>Microseconds</li><li>Milliseconds</li><li>Bytes</li><li>Kilobytes</li><li>Megabytes</li><li>Gigabytes</li><li>Terabytes</li><li>Bits</li><li>Kilobits</li><li>Megabits</li><li>Gigabits</li><li>Terabits</li><li>Percent</li><li>Count</li><li>Bytes/Second</li><li>Kilobytes/Second</li><li>Megabytes/Second</li><li>Gigabytes/Second</li><li>Terabytes/Second</li><li>Bits/Second</li><li>Kilobits/Second</li><li>Megabits/Second</li><li>Gigabits/Second</li><li>Terabits/Second</li><li>Count/Second</li><li>None</li></ul></td>
        <td><div>The threshold's unit of measurement</div>        </td></tr>
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

      - name: create alarm
        ec2_metric_alarm:
          state: present
          region: ap-southeast-2
          name: "cpu-low"
          metric: "CPUUtilization"
          namespace: "AWS/EC2"
          statistic: Average
          comparison: "<="
          threshold: 5.0
          period: 300
          evaluation_periods: 3
          unit: "Percent"
          description: "This will alarm when a bamboo slave's cpu usage average is lower than 5% for 15 minutes "
          dimensions: {'InstanceId':'i-XXX'}
          alarm_actions: ["action1","action2"]
    
    


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
