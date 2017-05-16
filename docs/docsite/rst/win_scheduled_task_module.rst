.. _win_scheduled_task:


win_scheduled_task - Manage scheduled tasks
+++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage scheduled tasks




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
                <tr><td>arguments<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Arguments to provide scheduled task action</div></br>
    <div style="font-size: small;">aliases: argument<div>        </td></tr>
                <tr><td>days_of_week<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Days of the week to run a weekly task, not idempotent</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The description for the scheduled task</div>        </td></tr>
                <tr><td>enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Enable/disable the task</div>        </td></tr>
                <tr><td>executable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Command the scheduled task should execute</div></br>
    <div style="font-size: small;">aliases: execute<div>        </td></tr>
                <tr><td>frequency<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>once</li><li>daily</li><li>weekly</li></ul></td>
        <td><div>The frequency of the command, not idempotent</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the scheduled task</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>\</td>
        <td></td>
        <td><div>Task folder in which this task will be stored</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State that the task should become</div>        </td></tr>
                <tr><td>time<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Time to execute scheduled task, not idempotent</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>User to run scheduled task as</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a scheduled task to open a command prompt
    - win_scheduled_task:
        name: TaskName
        description: open command prompt
        executable: cmd
        arguments: -opt1 -opt2
        path: example
        time: 9am
        frequency: daily
        state: present
        enabled: yes
        user: SYSTEM


Notes
-----

.. note::
    - This module requires Windows Server 2012 or later.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
