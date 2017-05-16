.. _systemd:


systemd - Manage services.
++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Controls systemd services on remote hosts.


Requirements (on host that executes module)
-------------------------------------------

  * A system managed by systemd


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
    <td>daemon_reload<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>run daemon-reload before doing any other operations, to make sure systemd has read any changes.</div></br>
        <div style="font-size: small;">aliases: daemon-reload<div></td></tr>
            <tr>
    <td>enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether the service should start on boot. <b>At least one of state and enabled are required.</b></div></td></tr>
            <tr>
    <td>masked<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether the unit should be masked or not, a masked unit is impossible to start.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the service.</div></br>
        <div style="font-size: small;">aliases: unit, service<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>started</li><li>stopped</li><li>restarted</li><li>reloaded</li></ul></td>
        <td><div><code>started</code>/<code>stopped</code> are idempotent actions that will not run commands unless necessary. <code>restarted</code> will always bounce the service. <code>reloaded</code> will always reload.</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>run systemctl talking to the service manager of the calling user, rather than the service manager of the system.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example action to start service httpd, if not running
    - systemd: state=started name=httpd
    
    # Example action to stop service cron on debian, if running
    - systemd: name=cron state=stopped
    
    # Example action to restart service cron on centos, in all cases, also issue daemon-reload to pick up config changes
    - systemd: state=restarted daemon_reload=yes name=crond
    # Example action to reload service httpd, in all cases
    - systemd: name=httpd state=reloaded
    # Example action to enable service httpd and ensure it is not masked
    - systemd:
        name: httpd
        enabled: yes
        masked: no
    # Example action to enable a timer for dnf-automatic
    - systemd:
        name: dnf-automatic.timer
        state: started
        enabled: True

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
        <td> status </td>
        <td> A dictionary with the key=value pairs returned from `systemctl show` </td>
        <td align=center> success </td>
        <td align=center> complex </td>
        <td align=center> {'ExecStart': '{ path=/usr/sbin/crond ; argv[]=/usr/sbin/crond -n $CRONDARGS ; ignore_errors=no ; start_time=[n/a] ; stop_time=[n/a] ; pid=0 ; code=(null) ; status=0/0 }', 'ConditionResult': 'yes', 'TimeoutStopUSec': '1min 30s', 'ControlGroup': '/system.slice/crond.service', 'MainPID': '595', 'GuessMainPID': 'yes', 'ExecMainCode': '0', 'InactiveExitTimestamp': 'Sun 2016-05-15 18:28:49 EDT', 'FragmentPath': '/usr/lib/systemd/system/crond.service', 'UnitFileState': 'enabled', 'ExecMainPID': '595', 'LimitSIGPENDING': '3902', 'WatchdogUSec': '0', 'ActiveState': 'active', 'Nice': '0', 'OOMScoreAdjust': '0', 'LoadState': 'loaded', 'DefaultDependencies': 'yes', 'StatusErrno': '0', 'RootDirectoryStartOnly': 'no', 'WantedBy': 'multi-user.target', 'TTYVTDisallocate': 'no', 'RestartUSec': '100ms', 'Transient': 'no', 'CPUAccounting': 'no', 'CPUSchedulingPolicy': '0', 'StartLimitInterval': '10000000', 'WatchdogTimestampMonotonic': '0', 'LimitSTACK': '18446744073709551615', 'Restart': 'no', 'RemainAfterExit': 'no', 'LimitNOFILE': '4096', 'CanReload': 'yes', 'LimitLOCKS': '18446744073709551615', 'AllowIsolate': 'no', 'IgnoreOnSnapshot': 'no', 'CanIsolate': 'no', 'ActiveEnterTimestampMonotonic': '8135942', 'NeedDaemonReload': 'no', 'TTYVHangup': 'no', 'EnvironmentFile': '/etc/sysconfig/crond (ignore_errors=no)', 'StandardInput': 'null', 'CPUSchedulingPriority': '0', 'KillSignal': '15', 'LimitFSIZE': '18446744073709551615', 'IgnoreOnIsolate': 'no', 'Requires': 'basic.target', 'LimitCPU': '18446744073709551615', 'ActiveEnterTimestamp': 'Sun 2016-05-15 18:28:49 EDT', 'ExecMainStatus': '0', 'PermissionsStartOnly': 'no', 'LimitDATA': '18446744073709551615', 'MemoryLimit': '18446744073709551615', 'StopWhenUnneeded': 'no', 'LimitMSGQUEUE': '819200', 'OnFailureIsolate': 'no', 'CanStart': 'yes', 'PrivateTmp': 'no', 'Before': 'shutdown.target multi-user.target', 'IOScheduling': '0', 'LimitAS': '18446744073709551615', 'Slice': 'system.slice', 'ExecMainExitTimestampMonotonic': '0', 'LimitRTTIME': '18446744073709551615', 'InactiveExitTimestampMonotonic': '8135942', 'NotifyAccess': 'none', 'SendSIGHUP': 'no', 'BlockIOAccounting': 'no', 'PrivateNetwork': 'no', 'MemoryAccounting': 'no', 'CanStop': 'yes', 'NoNewPrivileges': 'no', 'ExecMainStartTimestampMonotonic': '8134990', 'Type': 'simple', 'SyslogPriority': '30', 'SameProcessGroup': 'no', 'SubState': 'running', 'TimeoutStartUSec': '1min 30s', 'StartLimitBurst': '5', 'LimitNPROC': '3902', 'After': 'auditd.service systemd-user-sessions.service time-sync.target systemd-journald.socket basic.target system.slice', 'UMask': '0022', 'NonBlocking': 'no', 'DevicePolicy': 'auto', 'RefuseManualStop': 'no', 'ExecMainStartTimestamp': 'Sun 2016-05-15 18:28:49 EDT', 'StartLimitAction': 'none', 'Conflicts': 'shutdown.target', 'ConditionTimestamp': 'Sun 2016-05-15 18:28:49 EDT', 'CapabilityBoundingSet': '18446744073709551615', 'TTYReset': 'no', 'Names': 'crond.service', 'Wants': 'system.slice', 'StandardOutput': 'journal', 'MountFlags': '0', 'RefuseManualStart': 'no', 'InactiveEnterTimestampMonotonic': '0', 'KillMode': 'process', 'SyslogLevelPrefix': 'yes', 'LimitRSS': '18446744073709551615', 'StandardError': 'inherit', 'SendSIGKILL': 'yes', 'LimitRTPRIO': '0', 'IgnoreSIGPIPE': 'yes', 'Delegate': 'no', 'ExecReload': '{ path=/bin/kill ; argv[]=/bin/kill -HUP $MAINPID ; ignore_errors=no ; start_time=[n/a] ; stop_time=[n/a] ; pid=0 ; code=(null) ; status=0/0 }', 'SecureBits': '0', 'Description': 'Command Scheduler', 'LimitCORE': '18446744073709551615', 'ActiveExitTimestampMonotonic': '0', 'JobTimeoutUSec': '0', 'TimerSlackNSec': '50000', 'LimitNICE': '0', 'BlockIOWeight': '1000', 'CPUSchedulingResetOnFork': 'no', 'Result': 'success', 'CPUShares': '1024', 'ControlPID': '0', 'Id': 'crond.service', 'ConditionTimestampMonotonic': '7902742', 'LimitMEMLOCK': '65536'} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: One option other than name is required.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

