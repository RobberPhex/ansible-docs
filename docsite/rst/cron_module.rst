.. _cron:


cron - Manage cron.d and crontab entries.
+++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Use this module to manage crontab entries. This module allows you to create named crontab entries, update, or delete them.
The module includes one line with the description of the crontab entry ``"#Ansible: <name>"`` corresponding to the "name" passed to the module, which is used by future ansible/module calls to find/check the state.  The "name" parameter should be unique, and changing the "name" value will result in a new cron task being created (or a different one being removed)


Requirements
------------

  * cron


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
    <td>backup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If set, create a backup of the crontab before it is modified. The location of the backup is returned in the <code>backup_file</code> variable by this module.</div></td></tr>
            <tr>
    <td>cron_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If specified, uses this file in cron.d instead of an individual user's crontab. To use the <code>cron_file</code> parameter you must specify the <code>user</code> as well.</div></td></tr>
            <tr>
    <td>day<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>*</td>
        <td><ul></ul></td>
        <td><div>Day of the month the job should run ( 1-31, *, */2, etc )</div></br>
        <div style="font-size: small;">aliases: dom<div></td></tr>
            <tr>
    <td>disabled<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If the job should be disabled (commented out) in the crontab. Only has effect if state=present</div></td></tr>
            <tr>
    <td>hour<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>*</td>
        <td><ul></ul></td>
        <td><div>Hour when the job should run ( 0-23, *, */2, etc )</div></td></tr>
            <tr>
    <td>job<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The command to execute. Required if state=present.</div></td></tr>
            <tr>
    <td>minute<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>*</td>
        <td><ul></ul></td>
        <td><div>Minute when the job should run ( 0-59, *, */2, etc )</div></td></tr>
            <tr>
    <td>month<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>*</td>
        <td><ul></ul></td>
        <td><div>Month of the year the job should run ( 1-12, *, */2, etc )</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Description of a crontab entry. Required if state=absent</div></td></tr>
            <tr>
    <td>reboot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If the job should be run at reboot. This option is deprecated. Users should use special_time.</div></td></tr>
            <tr>
    <td>special_time<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>reboot</li><li>yearly</li><li>annually</li><li>monthly</li><li>weekly</li><li>daily</li><li>hourly</li></ul></td>
        <td><div>Special time specification nickname.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether to ensure the job is present or absent.</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>root</td>
        <td><ul></ul></td>
        <td><div>The specific user whose crontab should be modified.</div></td></tr>
            <tr>
    <td>weekday<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>*</td>
        <td><ul></ul></td>
        <td><div>Day of the week that the job should run ( 0-6 for Sunday-Saturday, *, etc )</div></br>
        <div style="font-size: small;">aliases: dow<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure a job that runs at 2 and 5 exists.
    # Creates an entry like "0 5,2 * * ls -alh > /dev/null"
    - cron: name="check dirs" minute="0" hour="5,2" job="ls -alh > /dev/null"
    
    # Ensure an old job is no longer present. Removes any job that is prefixed
    # by "#Ansible: an old job" from the crontab
    - cron: name="an old job" state=absent
    
    # Creates an entry like "@reboot /some/job.sh"
    - cron: name="a job for reboot" special_time=reboot job="/some/job.sh"
    
    # Creates a cron file under /etc/cron.d
    - cron: name="yum autoupdate" weekday="2" minute=0 hour=12
            user="root" job="YUMINTERACTIVE=0 /usr/sbin/yum-autoupdate"
            cron_file=ansible_yum-autoupdate
    
    # Removes a cron file from under /etc/cron.d
    - cron: name="yum autoupdate" cron_file=ansible_yum-autoupdate state=absent




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

