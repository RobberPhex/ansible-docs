.. _svc:


svc - Manage daemontools services.
++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Controls daemontools services on remote hosts using the svc utility.




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
    <td>downed<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Should a 'down' file exist or not, if it exists it disables auto startup. defaults to no. Downed does not imply stopped.</div></td></tr>
            <tr>
    <td>enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Wheater the service is enabled or not, if disabled it also implies stopped. Make note that a service can be enabled and downed (no auto restart).</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the service to manage.</div></td></tr>
            <tr>
    <td>service_dir<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/service</td>
        <td><ul></ul></td>
        <td><div>directory svscan watches for services</div></td></tr>
            <tr>
    <td>service_src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>directory where services are defined, the source of symlinks to service_dir.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>started</li><li>stopped</li><li>restarted</li><li>reloaded</li><li>once</li></ul></td>
        <td><div><code>Started</code>/<code>stopped</code> are idempotent actions that will not run commands unless necessary.  <code>restarted</code> will always bounce the svc (svc -t) and <code>killed</code> will always bounce the svc (svc -k). <code>reloaded</code> will send a sigusr1 (svc -1). <code>once</code> will run a normally downed svc once (svc -o), not really an idempotent operation.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example action to start svc dnscache, if not running
     - svc: name=dnscache state=started
    
    # Example action to stop svc dnscache, if running
     - svc: name=dnscache state=stopped
    
    # Example action to kill svc dnscache, in all cases
     - svc : name=dnscache state=killed
    
    # Example action to restart svc dnscache, in all cases
     - svc : name=dnscache state=restarted
    
    # Example action to reload svc dnscache, in all cases
     - svc: name=dnscache state=reloaded
    
    # Example using alt svc directory location
     - svc: name=dnscache state=reloaded service_dir=/var/service




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

