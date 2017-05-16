.. _datadog_monitor:


datadog_monitor - Manages Datadog monitors
++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manages monitors within Datadog
* Options like described on http://docs.datadoghq.com/api/


Requirements (on host that executes module)
-------------------------------------------

  * datadog


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
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Your DataDog API key.</div>        </td></tr>
                <tr><td>app_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Your DataDog app key.</div>        </td></tr>
                <tr><td>escalation_message<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A message to include with a re-notification. Supports the '@username' notification we allow elsewhere. Not applicable if renotify_interval is None</div>        </td></tr>
                <tr><td>id<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The id of the alert. If set, will be used instead of the name to locate the alert.</div>        </td></tr>
                <tr><td>locked<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A boolean indicating whether changes to this monitor should be restricted to the creator or admins.</div>        </td></tr>
                <tr><td>message<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A message to include with notifications for this monitor. Email notifications can be sent to specific users by using the same '@username' notation as events. Monitor message template variables can be accessed by using double square brackets, i.e '[[' and ']]'.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the alert.</div>        </td></tr>
                <tr><td>no_data_timeframe<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>2x timeframe for metric, 2 minutes for service</td>
        <td></td>
        <td><div>The number of minutes before a monitor will notify when data stops reporting. Must be at least 2x the monitor timeframe for metric alerts or 2 minutes for service checks.</div>        </td></tr>
                <tr><td>notify_audit<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A boolean indicating whether tagged users will be notified on changes to this monitor.</div>        </td></tr>
                <tr><td>notify_no_data<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A boolean indicating whether this monitor will notify when data stops reporting..</div>        </td></tr>
                <tr><td>query<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The monitor query to notify on with syntax varying depending on what type of monitor you are creating.</div>        </td></tr>
                <tr><td>renotify_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The number of minutes after the last notification before a monitor will re-notify on the current status. It will only re-notify if it's not resolved.</div>        </td></tr>
                <tr><td>require_full_window<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A boolean indicating whether this monitor needs a full window of data before it's evaluated. We highly recommend you set this to False for sparse metrics, otherwise some evaluations will be skipped.</div>        </td></tr>
                <tr><td>silenced<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dictionary of scopes to timestamps or None. Each scope will be muted until the given POSIX timestamp or forever if the value is None. </div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>muted</li><li>unmuted</li></ul></td>
        <td><div>The designated state of the monitor.</div>        </td></tr>
                <tr><td>tags<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A list of tags to associate with your monitor when creating or updating. This can help you categorize and filter monitors.</div>        </td></tr>
                <tr><td>thresholds<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>{u'warning': 1, u'ok': 1, u'critical': 1}</td>
        <td></td>
        <td><div>A dictionary of thresholds by status. This option is only available for service checks and metric alerts. Because each of them can have multiple thresholds, we don't define them directly in the query.</div>        </td></tr>
                <tr><td>timeout_h<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The number of hours of the monitor not reporting data before it will automatically resolve from a triggered state.</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>metric alert</li><li>service check</li><li>event alert</li></ul></td>
        <td><div>The type of the monitor.</div><div>The 'event alert'is available starting at Ansible 2.1</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a metric monitor
    datadog_monitor:
      type: "metric alert"
      name: "Test monitor"
      state: "present"
      query: "datadog.agent.up.over('host:host1').last(2).count_by_status()"
      message: "Host [[host.name]] with IP [[host.ip]] is failing to report to datadog."
      api_key: "9775a026f1ca7d1c6c5af9d94d9595a4"
      app_key: "87ce4a24b5553d2e482ea8a8500e71b8ad4554ff"
    
    # Deletes a monitor
    datadog_monitor:
      name: "Test monitor"
      state: "absent"
      api_key: "9775a026f1ca7d1c6c5af9d94d9595a4"
      app_key: "87ce4a24b5553d2e482ea8a8500e71b8ad4554ff"
    
    # Mutes a monitor
    datadog_monitor:
      name: "Test monitor"
      state: "mute"
      silenced: '{"*":None}'
      api_key: "9775a026f1ca7d1c6c5af9d94d9595a4"
      app_key: "87ce4a24b5553d2e482ea8a8500e71b8ad4554ff"
    
    # Unmutes a monitor
    datadog_monitor:
      name: "Test monitor"
      state: "unmute"
      api_key: "9775a026f1ca7d1c6c5af9d94d9595a4"
      app_key: "87ce4a24b5553d2e482ea8a8500e71b8ad4554ff"





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
