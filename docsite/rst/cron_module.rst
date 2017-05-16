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
    <td>backup</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>If set, create a backup of the crontab before it is modified. The location of the backup is returned in the <code>backup</code> variable by this module.</td>
    </tr>
            <tr>
    <td>cron_file</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>If specified, uses this file in cron.d instead of an individual user's crontab.</td>
    </tr>
            <tr>
    <td>day</td>
    <td>no</td>
    <td>*</td>
        <td><ul></ul></td>
        <td>Day of the month the job should run ( 1-31, *, */2, etc )</td>
    </tr>
            <tr>
    <td>hour</td>
    <td>no</td>
    <td>*</td>
        <td><ul></ul></td>
        <td>Hour when the job should run ( 0-23, *, */2, etc )</td>
    </tr>
            <tr>
    <td>job</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The command to execute. Required if state=present.</td>
    </tr>
            <tr>
    <td>minute</td>
    <td>no</td>
    <td>*</td>
        <td><ul></ul></td>
        <td>Minute when the job should run ( 0-59, *, */2, etc )</td>
    </tr>
            <tr>
    <td>month</td>
    <td>no</td>
    <td>*</td>
        <td><ul></ul></td>
        <td>Month of the year the job should run ( 1-12, *, */2, etc )</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Description of a crontab entry.</td>
    </tr>
            <tr>
    <td>reboot</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If the job should be run at reboot. This option is deprecated. Users should use special_time. (added in Ansible 1.0)</td>
    </tr>
            <tr>
    <td>special_time</td>
    <td>no</td>
    <td></td>
        <td><ul><li>reboot</li><li>yearly</li><li>annually</li><li>monthly</li><li>weekly</li><li>daily</li><li>hourly</li></ul></td>
        <td>Special time specification nickname. (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Whether to ensure the job is present or absent.</td>
    </tr>
            <tr>
    <td>user</td>
    <td>no</td>
    <td>root</td>
        <td><ul></ul></td>
        <td>The specific user whose crontab should be modified.</td>
    </tr>
            <tr>
    <td>weekday</td>
    <td>no</td>
    <td>*</td>
        <td><ul></ul></td>
        <td>Day of the week that the job should run ( 0-6 for Sunday-Saturday, *, etc )</td>
    </tr>
        </table>


.. note:: Requires cron


Examples
--------

.. raw:: html

    <br/>


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
    - cron: cron_file=ansible_yum-autoupdate state=absent



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

