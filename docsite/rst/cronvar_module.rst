.. _cronvar:


cronvar - Manage variables in crontabs
++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Use this module to manage crontab variables. This module allows you to create, update, or delete cron variable definitions.


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
            <tr>
    <td>backup<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If set, create a backup of the crontab before it is modified. The location of the backup is returned in the <code>backup</code> variable by this module.</div></td></tr>
            <tr>
    <td>cron_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If specified, uses this file instead of an individual user's crontab. Without a leading /, this is assumed to be in /etc/cron.d.  With a leading /, this is taken as absolute.</div></td></tr>
            <tr>
    <td>insertafter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Used with <code>state=present</code>. If specified, the variable will be inserted after the variable specified.</div></td></tr>
            <tr>
    <td>insertbefore<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Used with <code>state=present</code>. If specified, the variable will be inserted just before the variable specified.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the crontab variable.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether to ensure that the variable is present or absent.</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>root</td>
        <td><ul></ul></td>
        <td><div>The specific user whose crontab should be modified.</div></td></tr>
            <tr>
    <td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The value to set this variable to.  Required if state=present.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure a variable exists.
    # Creates an entry like "EMAIL=doug@ansibmod.con.com"
    - cronvar: name="EMAIL" value="doug@ansibmod.con.com"
    
    # Make sure a variable is gone.  This will remove any variable named
    # "LEGACY"
    - cronvar: name="LEGACY" state=absent
    
    # Adds a variable to a file under /etc/cron.d
    - cronvar: name="LOGFILE" value="/var/log/yum-autoupdate.log"
            user="root" cron_file=ansible_yum-autoupdate




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

