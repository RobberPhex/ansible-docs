.. _cs_snapshot_policy:


cs_snapshot_policy - Manages volume snapshot policies on Apache CloudStack based clouds.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create, update and delete volume snapshot policies.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * cs >= 0.6.10


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
    <td>account<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Account the volume is related to.</div></td></tr>
            <tr>
    <td>api_http_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>get</td>
        <td><ul><li>get</li><li>post</li></ul></td>
        <td><div>HTTP method used.</div></td></tr>
            <tr>
    <td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>API key of the CloudStack API.</div></td></tr>
            <tr>
    <td>api_region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cloudstack</td>
        <td><ul></ul></td>
        <td><div>Name of the ini section in the <code>cloustack.ini</code> file.</div></td></tr>
            <tr>
    <td>api_secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Secret key of the CloudStack API.</div></td></tr>
            <tr>
    <td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>HTTP timeout.</div></td></tr>
            <tr>
    <td>api_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>URL of the CloudStack API e.g. https://cloud.example.com/client/api.</div></td></tr>
            <tr>
    <td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Domain the volume is related to.</div></td></tr>
            <tr>
    <td>interval_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>daily</td>
        <td><ul><li>hourly</li><li>daily</li><li>weekly</li><li>monthly</li></ul></td>
        <td><div>Interval of the snapshot.</div></br>
        <div style="font-size: small;">aliases: interval<div></td></tr>
            <tr>
    <td>max_snaps<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>8</td>
        <td><ul></ul></td>
        <td><div>Max number of snapshots.</div></br>
        <div style="font-size: small;">aliases: max<div></td></tr>
            <tr>
    <td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the project the volume is related to.</div></td></tr>
            <tr>
    <td>schedule<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Time the snapshot is scheduled. Required if <code>state=present</code>.</div><div>Format for <code>interval_type=HOURLY</code>: <code>MM</code></div><div>Format for <code>interval_type=DAILY</code>: <code>MM:HH</code></div><div>Format for <code>interval_type=WEEKLY</code>: <code>MM:HH:DD (1-7</code>)</div><div>Format for <code>interval_type=MONTHLY</code>: <code>MM:HH:DD (1-28</code>)</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the snapshot policy.</div></td></tr>
            <tr>
    <td>time_zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>UTC</td>
        <td><ul></ul></td>
        <td><div>Specifies a timezone for this command.</div></br>
        <div style="font-size: small;">aliases: timezone<div></td></tr>
            <tr>
    <td>volume<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the volume.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure a snapshot policy daily at 1h00 UTC
    - local_action:
        module: cs_snapshot_policy
        volume: ROOT-478
        schedule: '00:1'
        max_snaps: 3
    
    # Ensure a snapshot policy hourly at minute 5 UTC
    - local_action:
        module: cs_snapshot_policy
        volume: ROOT-478
        schedule: '5'
        interval_type: hourly
        max_snaps: 1
    
    # Ensure a snapshot policy weekly on Sunday at 05h00, TZ Europe/Zurich
    - local_action:
        module: cs_snapshot_policy
        volume: ROOT-478
        schedule: '00:5:1'
        interval_type: weekly
        max_snaps: 1
        time_zone: 'Europe/Zurich'
    
    # Ensure a snapshot policy is absent
    - local_action:
        module: cs_snapshot_policy
        volume: ROOT-478
        interval_type: hourly
        state: absent

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
        <td> volume </td>
        <td> the volume of the snapshot policy. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Etc/UTC </td>
    </tr>
            <tr>
        <td> account </td>
        <td> Account the volume is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example account </td>
    </tr>
            <tr>
        <td> zone </td>
        <td> Name of zone the volume is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ch-gva-2 </td>
    </tr>
            <tr>
        <td> schedule </td>
        <td> schedule of the snapshot policy. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> None </td>
    </tr>
            <tr>
        <td> interval_type </td>
        <td> interval type of the snapshot policy. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> daily </td>
    </tr>
            <tr>
        <td> time_zone </td>
        <td> the time zone of the snapshot policy. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Etc/UTC </td>
    </tr>
            <tr>
        <td> project </td>
        <td> Name of project the volume is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Production </td>
    </tr>
            <tr>
        <td> domain </td>
        <td> Domain the volume is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example domain </td>
    </tr>
            <tr>
        <td> max_snaps </td>
        <td> maximum number of snapshots retained. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 10 </td>
    </tr>
            <tr>
        <td> id </td>
        <td> UUID of the snapshot policy. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> a6f7a5fc-43f8-11e5-a151-feff819cdc9f </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Ansible uses the ``cs`` library's configuration method if credentials are not provided by the arguments ``api_url``, ``api_key``, ``api_secret``. Configuration is read from several locations, in the following order. - The ``CLOUDSTACK_ENDPOINT``, ``CLOUDSTACK_KEY``, ``CLOUDSTACK_SECRET`` and ``CLOUDSTACK_METHOD``. ``CLOUDSTACK_TIMEOUT`` environment variables. - A ``CLOUDSTACK_CONFIG`` environment variable pointing to an ``.ini`` file, - A ``cloudstack.ini`` file in the current working directory. - A ``.cloudstack.ini`` file in the users home directory. Optionally multiple credentials and endpoints can be specified using ini sections in ``cloudstack.ini``. Use the argument ``api_region`` to select the section name, default section is ``cloudstack``. See https://github.com/exoscale/cs for more information.
.. note:: A detailed guide about cloudstack modules can be found on http://docs.ansible.com/ansible/guide_cloudstack.html
.. note:: This module supports check mode.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

