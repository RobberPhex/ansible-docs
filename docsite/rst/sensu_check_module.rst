.. _sensu_check:


sensu_check - Manage Sensu checks
+++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage the checks that should be run on a machine by *Sensu*.
Most options do not have a default and will not be added to the check definition unless specified.
All defaults except *path*, *state*, *backup* and *metric* are not managed by this module,
they are simply specified for your convenience.




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
    <td>aggregate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Classifies the check as an aggregate check,</div><div>making it available via the aggregate API</div></td></tr>
            <tr>
    <td>backup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Create a backup file (if yes), including the timestamp information so</div><div>you can get the original file back if you somehow clobbered it incorrectly.</div></td></tr>
            <tr>
    <td>command<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to the sensu check to run (not required when <em>state=absent</em>)</div></td></tr>
            <tr>
    <td>custom<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A hash/dictionary of custom parameters for mixing to the configuration.</div><div>You can't rewrite others module parameters using this</div></td></tr>
            <tr>
    <td>dependencies<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Other checks this check depends on, if dependencies fail,</div><div>handling of this check will be disabled</div></td></tr>
            <tr>
    <td>handle<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether the check should be handled or not</div></td></tr>
            <tr>
    <td>handlers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of handlers to notify when the check fails</div></td></tr>
            <tr>
    <td>high_flap_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The low threshhold for flap detection</div></td></tr>
            <tr>
    <td>interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Check interval in seconds</div></td></tr>
            <tr>
    <td>low_flap_threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The low threshhold for flap detection</div></td></tr>
            <tr>
    <td>metric<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether the check is a metric</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the check</div><div>This is the key that is used to determine whether a check exists</div></td></tr>
            <tr>
    <td>occurrences<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>Number of event occurrences before the handler should take action</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/etc/sensu/conf.d/checks.json</td>
        <td><ul></ul></td>
        <td><div>Path to the json file of the check to be added/removed.</div><div>Will be created if it does not exist (unless <em>state=absent</em>).</div><div>The parent folders need to exist when <em>state=present</em>, otherwise an error will be thrown</div></td></tr>
            <tr>
    <td>publish<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether the check should be scheduled at all.</div><div>You can still issue it via the sensu api</div></td></tr>
            <tr>
    <td>refresh<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Number of seconds handlers should wait before taking second action</div></td></tr>
            <tr>
    <td>source<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The check source, used to create a JIT Sensu client for an external resource (e.g. a network switch).</div></td></tr>
            <tr>
    <td>standalone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether the check should be scheduled by the sensu client or server</div><div>This option obviates the need for specifying the <em>subscribers</em> option</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the check should be present or not</div></td></tr>
            <tr>
    <td>subdue_begin<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>When to disable handling of check failures</div></td></tr>
            <tr>
    <td>subdue_end<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>When to enable handling of check failures</div></td></tr>
            <tr>
    <td>subscribers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>List of subscribers/channels this check should run for</div><div>See sensu_subscribers to subscribe a machine to a channel</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>Timeout for the check</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Fetch metrics about the CPU load every 60 seconds,
    # the sensu server has a handler called 'relay' which forwards stats to graphite
    - name: get cpu metrics
      sensu_check: name=cpu_load
                   command=/etc/sensu/plugins/system/cpu-mpstat-metrics.rb
                   metric=yes handlers=relay subscribers=common interval=60
    
    # Check whether nginx is running
    - name: check nginx process
      sensu_check: name=nginx_running
                   command='/etc/sensu/plugins/processes/check-procs.rb -f /var/run/nginx.pid'
                   handlers=default subscribers=nginx interval=60
    
    # Stop monitoring the disk capacity.
    # Note that the check will still show up in the sensu dashboard,
    # to remove it completely you need to issue a DELETE request to the sensu api.
    - name: check disk
      sensu_check: name=check_disk_capacity state=absent




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

