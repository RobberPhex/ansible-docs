.. _win_service:


win_service - Manages Windows services
++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.7


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages Windows services




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
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the service</div></td></tr>
            <tr>
    <td>start_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>auto</li><li>manual</li><li>disabled</li></ul></td>
        <td><div>Set the startup type for the service</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>started</li><li>stopped</li><li>restarted</li></ul></td>
        <td><div><code>started</code>/<code>stopped</code> are idempotent actions that will not run commands unless necessary.  <code>restarted</code> will always bounce the service.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

      # Restart a service
      win_service:
        name: spooler
        state: restarted
    
      # Set service startup mode to auto and ensure it is started
      win_service:
        name: spooler
        start_mode: auto
        state: started




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

