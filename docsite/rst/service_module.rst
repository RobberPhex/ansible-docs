.. _service:


service - Manage services.
++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Controls services on remote hosts. Supported init systems include BSD init, OpenRC, SysV, Solaris SMF, systemd, upstart.




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
    <td>arguments<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Additional arguments provided on the command line</div></br>
        <div style="font-size: small;">aliases: args<div></td></tr>
            <tr>
    <td>enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether the service should start on boot. <b>At least one of state and enabled are required.</b></div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the service.</div></td></tr>
            <tr>
    <td>pattern<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If the service does not respond to the status command, name a substring to look for as would be found in the output of the <em>ps</em> command as a stand-in for a status result.  If the string is found, the service will be assumed to be running.</div></td></tr>
            <tr>
    <td>runlevel<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>default</td>
        <td><ul></ul></td>
        <td><div>For OpenRC init scripts (ex: Gentoo) only.  The runlevel that this service belongs to.</div></td></tr>
            <tr>
    <td>sleep<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If the service is being <code>restarted</code> then sleep this many seconds between the stop and start command. This helps to workaround badly behaving init scripts that exit immediately after signaling a process to stop.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>started</li><li>stopped</li><li>restarted</li><li>reloaded</li></ul></td>
        <td><div><code>started</code>/<code>stopped</code> are idempotent actions that will not run commands unless necessary.  <code>restarted</code> will always bounce the service.  <code>reloaded</code> will always reload. <b>At least one of state and enabled are required.</b></div></td></tr>
            <tr>
    <td>use<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>auto</td>
        <td><ul></ul></td>
        <td><div>The service module actually uses system specific modules, normally through auto detection, this setting can force a specific module.</div><div>Normally it uses the value of the 'ansible_service_mgr' fact and falls back to the old 'service' module when none matching is found.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example action to start service httpd, if not running
    - service: name=httpd state=started
    
    # Example action to stop service httpd, if running
    - service: name=httpd state=stopped
    
    # Example action to restart service httpd, in all cases
    - service: name=httpd state=restarted
    
    # Example action to reload service httpd, in all cases
    - service: name=httpd state=reloaded
    
    # Example action to enable service httpd, and not touch the running state
    - service: name=httpd enabled=yes
    
    # Example action to start service foo, based on running process /usr/bin/foo
    - service: name=foo pattern=/usr/bin/foo state=started
    
    # Example action to restart network service for interface eth0
    - service: name=network state=restarted args=eth0
    




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

