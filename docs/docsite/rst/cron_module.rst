.. _cron:


cron - Manage cron.d and crontab entries.
+++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Use this module to manage crontab and environment variables entries. This module allows you to create environment variables and named crontab entries, update, or delete them.
* When crontab jobs are managed: the module includes one line with the description of the crontab entry ``"#Ansible: <name>"`` corresponding to the "name" passed to the module, which is used by future ansible/module calls to find/check the state. The "name" parameter should be unique, and changing the "name" value will result in a new cron task being created (or a different one being removed).
* When environment variables are managed: no comment line is added, but, when the module needs to find/check the state, it uses the "name" parameter to find the environment variable definition line.
* When using symbols such as %, they must be properly escaped.


Requirements (on host that executes module)
-------------------------------------------

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
                <tr><td>backup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If set, create a backup of the crontab before it is modified. The location of the backup is returned in the <code>backup_file</code> variable by this module.</div>        </td></tr>
                <tr><td>cron_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If specified, uses this file instead of an individual user's crontab. If this is a relative path, it is interpreted with respect to /etc/cron.d. (If it is absolute, it will typically be /etc/crontab). To use the <code>cron_file</code> parameter you must specify the <code>user</code> as well.</div>        </td></tr>
                <tr><td>day<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>*</td>
        <td></td>
        <td><div>Day of the month the job should run ( 1-31, *, */2, etc )</div></br>
    <div style="font-size: small;">aliases: dom<div>        </td></tr>
                <tr><td>disabled<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If the job should be disabled (commented out) in the crontab. Only has effect if state=present</div>        </td></tr>
                <tr><td>env<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If set, manages a crontab's environment variable. New variables are added on top of crontab. "name" and "value" parameters are the name and the value of environment variable.</div>        </td></tr>
                <tr><td>hour<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>*</td>
        <td></td>
        <td><div>Hour when the job should run ( 0-23, *, */2, etc )</div>        </td></tr>
                <tr><td>insertafter<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Used with <code>state=present</code> and <code>env</code>. If specified, the environment variable will be inserted after the declaration of specified environment variable.</div>        </td></tr>
                <tr><td>insertbefore<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Used with <code>state=present</code> and <code>env</code>. If specified, the environment variable will be inserted before the declaration of specified environment variable.</div>        </td></tr>
                <tr><td>job<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The command to execute or, if env is set, the value of environment variable. Required if state=present.</div></br>
    <div style="font-size: small;">aliases: value<div>        </td></tr>
                <tr><td>minute<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>*</td>
        <td></td>
        <td><div>Minute when the job should run ( 0-59, *, */2, etc )</div>        </td></tr>
                <tr><td>month<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>*</td>
        <td></td>
        <td><div>Month of the year the job should run ( 1-12, *, */2, etc )</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Description of a crontab entry or, if env is set, the name of environment variable. Required if state=absent. Note that if name is not set and state=present, then a new crontab entry will always be created, regardless of existing ones.</div>        </td></tr>
                <tr><td>reboot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If the job should be run at reboot. This option is deprecated. Users should use special_time.</div>        </td></tr>
                <tr><td>special_time<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>reboot</li><li>yearly</li><li>annually</li><li>monthly</li><li>weekly</li><li>daily</li><li>hourly</li></ul></td>
        <td><div>Special time specification nickname.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether to ensure the job or environment variable is present or absent.</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>root</td>
        <td></td>
        <td><div>The specific user whose crontab should be modified.</div>        </td></tr>
                <tr><td>weekday<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>*</td>
        <td></td>
        <td><div>Day of the week that the job should run ( 0-6 for Sunday-Saturday, *, etc )</div></br>
    <div style="font-size: small;">aliases: dow<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure a job that runs at 2 and 5 exists.
    # Creates an entry like "0 5,2 * * ls -alh > /dev/null"
    - cron:
        name: "check dirs"
        minute: "0"
        hour: "5,2"
        job: "ls -alh > /dev/null"
    
    # Ensure an old job is no longer present. Removes any job that is prefixed
    # by "#Ansible: an old job" from the crontab
    - cron:
        name: "an old job"
        state: absent
    
    # Creates an entry like "@reboot /some/job.sh"
    - cron:
        name: "a job for reboot"
        special_time: reboot
        job: "/some/job.sh"
    
    # Creates an entry like "PATH=/opt/bin" on top of crontab
    - cron:
        name: PATH
        env: yes
        value: /opt/bin
    
    # Creates an entry like "APP_HOME=/srv/app" and insert it after PATH
    # declaration
    - cron:
        name: APP_HOME
        env: yes
        value: /srv/app
        insertafter: PATH
    
    # Creates a cron file under /etc/cron.d
    - cron:
        name: yum autoupdate
        weekday: 2
        minute: 0
        hour: 12
        user: root
        job: "YUMINTERACTIVE: 0 /usr/sbin/yum-autoupdate"
        cron_file: ansible_yum-autoupdate
    
    # Removes a cron file from under /etc/cron.d
    - cron:
        name: "yum autoupdate"
        cron_file: ansible_yum-autoupdate
        state: absent
    
    # Removes "APP_HOME" environment variable from crontab
    - cron:
        name: APP_HOME
        env: yes
        state: absent





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is supported mainly by the community and is curated by core committers.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
