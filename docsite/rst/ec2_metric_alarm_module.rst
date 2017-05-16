.. _ec2_metric_alarm:


ec2_metric_alarm - Create/update or delete AWS Cloudwatch 'metric alarms'
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Can create or delete AWS metric alarms
Metrics you wish to alarm on must already exist

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
    <td>alarm_actions</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A list of the names action(s) taken when the alarm is in the 'alarm' status</td>
    </tr>
            <tr>
    <td>aws_access_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>AWS access key. If not set then the value of the AWS_ACCESS_KEY environment variable is used.</td>
    </tr>
            <tr>
    <td>aws_secret_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>AWS secret key. If not set then the value of the AWS_SECRET_KEY environment variable is used.</td>
    </tr>
            <tr>
    <td>comparison</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Determines how the threshold value is compared</td>
    </tr>
            <tr>
    <td>description</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A longer desciption of the alarm</td>
    </tr>
            <tr>
    <td>dimensions</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Describes to what the alarm is applied</td>
    </tr>
            <tr>
    <td>ec2_url</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Must be specified if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used</td>
    </tr>
            <tr>
    <td>evaluation_periods</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The number of times in which the metric is evaluated before final calculation</td>
    </tr>
            <tr>
    <td>insufficient_data_actions</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A list of the names of action(s) to take when the alarm is in the 'insufficient_data' status</td>
    </tr>
            <tr>
    <td>metric</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of the monitored metric (e.g. CPUUtilization)Metric must already exist</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td></td>
    </tr>
            <tr>
    <td>namespace</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of the appropriate namespace ('AWS/EC2', 'System/Linux', etc.), which determines the category it will appear under in cloudwatch</td>
    </tr>
            <tr>
    <td>ok_actions</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A list of the names of action(s) to take when the alarm is in the 'ok' status</td>
    </tr>
            <tr>
    <td>period</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The time (in seconds) between metric evaluations</td>
    </tr>
            <tr>
    <td>profile</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>uses a boto profile. Only works with boto &gt;= 2.24.0 (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>security_token</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>security token to authenticate against AWS (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>register or deregister the alarm</td>
    </tr>
            <tr>
    <td>statistic</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Operation applied to the metricWorks in conjunction with period and evaluation_periods to determine the comparison value</td>
    </tr>
            <tr>
    <td>threshold</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Sets the min/max bound for triggering the alarm</td>
    </tr>
            <tr>
    <td>unit</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The threshold's unit of measurement</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0. (added in Ansible 1.5)</td>
    </tr>
        </table>


.. note:: Requires boto


Examples
--------

.. raw:: html

    <br/>


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
    
    

.. note:: The following environment variables can be used ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY`` or ``AWS_ACCESS_KEY_ID``, ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY`` or ``AWS_SECRET_ACCESS_KEY``, ``AWS_REGION`` or ``EC2_REGION``, ``AWS_SECURITY_TOKEN``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

