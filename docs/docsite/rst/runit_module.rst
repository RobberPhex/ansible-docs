.. _runit:


runit - Manage runit services.
++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Controls runit services on remote hosts using the sv utility.




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
                <tr><td>enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Wheater the service is enabled or not, if disabled it also implies stopped.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the service to manage.</div>        </td></tr>
                <tr><td>service_dir<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/var/service</td>
        <td></td>
        <td><div>directory runsv watches for services</div>        </td></tr>
                <tr><td>service_src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>/etc/sv</td>
        <td></td>
        <td><div>directory where services are defined, the source of symlinks to service_dir.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>started</li><li>stopped</li><li>restarted</li><li>killed</li><li>reloaded</li><li>once</li></ul></td>
        <td><div><code>started</code>/<code>stopped</code> are idempotent actions that will not run commands unless necessary.  <code>restarted</code> will always bounce the service (sv restart) and <code>killed</code> will always bounce the service (sv force-stop). <code>reloaded</code> will send a HUP (sv reload). <code>once</code> will run a normally downed sv once (sv once), not really an idempotent operation.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example action to start sv dnscache, if not running
     - sv:
        name: dnscache
        state: started
    
    # Example action to stop sv dnscache, if running
     - sv:
        name: dnscache
        state: stopped
    
    # Example action to kill sv dnscache, in all cases
     - sv:
        name: dnscache
        state: killed
    
    # Example action to restart sv dnscache, in all cases
     - sv:
        name: dnscache
        state: restarted
    
    # Example action to reload sv dnscache, in all cases
     - sv:
        name: dnscache
        state: reloaded
    
    # Example using alt sv directory location
     - sv:
        name: dnscache
        state: reloaded
        service_dir: /run/service





Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
