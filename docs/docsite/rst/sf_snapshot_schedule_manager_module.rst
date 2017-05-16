.. _sf_snapshot_schedule_manager:


sf_snapshot_schedule_manager - Manage SolidFire snapshot schedules
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, destroy, or update accounts on SolidFire


Requirements (on host that executes module)
-------------------------------------------

  * solidfire-sdk-python (1.1.0.92)


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
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The hostname or IP address of the SolidFire cluster.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name for the snapshot schedule.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password for the specified user.</div>        </td></tr>
                <tr><td>paused<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Pause / Resume a schedule.</div>        </td></tr>
                <tr><td>recurring<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Should the schedule recur?</div>        </td></tr>
                <tr><td>retention<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Retention period for the snapshot.</div><div>Format is 'HH:mm:ss'.</div>        </td></tr>
                <tr><td>schedule_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The schedule ID for the schedule that you want to update or delete.</div>        </td></tr>
                <tr><td>snapshot_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name for the created snapshots.</div>        </td></tr>
                <tr><td>starting_date<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Starting date for the schedule.</div><div>Required when <code>state=present</code>.</div><div>Please use two '-' in the above format, or you may see an error- TypeError, is not JSON serializable description.</div><div>Format: <code>2016--12--01T00:00:00Z</code></div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the specified schedule should exist or not.</div>        </td></tr>
                <tr><td>time_interval_days<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td></td>
        <td><div>Time interval in days.</div>        </td></tr>
                <tr><td>time_interval_hours<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Time interval in hours.</div>        </td></tr>
                <tr><td>time_interval_minutes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Time interval in minutes.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Please ensure that the user has the adequate permissions. For more information, please read the official documentation <a href='https://goo.gl/ddJa4Q'>https://goo.gl/ddJa4Q</a>.</div>        </td></tr>
                <tr><td>volumes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Volume IDs that you want to set the snapshot schedule for.</div><div>At least 1 volume ID is required for creating a new schedule.</div><div>required when <code>state=present</code></div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

       - name: Create Snapshot schedule
         sf_snapshot_schedule_manager:
           hostname: "{{ solidfire_hostname }}"
           username: "{{ solidfire_username }}"
           password: "{{ solidfire_password }}"
           state: present
           name: Schedule_A
           time_interval_days: 1
           starting_date: 2016--12--01T00:00:00Z
           volumes: 7
    
       - name: Update Snapshot schedule
         sf_snapshot_schedule_manager:
           hostname: "{{ solidfire_hostname }}"
           username: "{{ solidfire_username }}"
           password: "{{ solidfire_password }}"
           state: present
           schedule_id: 6
           recurring: True
           snapshot_name: AnsibleSnapshots
    
       - name: Delete Snapshot schedule
         sf_snapshot_schedule_manager:
           hostname: "{{ solidfire_hostname }}"
           username: "{{ solidfire_username }}"
           password: "{{ solidfire_password }}"
           state: absent
           schedule_id: 6

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
        <td> schedule_id </td>
        <td> Schedule ID of the newly created schedule </td>
        <td align=center> success </td>
        <td align=center>  </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - The modules prefixed with ``sf\_`` are built to support the SolidFire storage platform.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
