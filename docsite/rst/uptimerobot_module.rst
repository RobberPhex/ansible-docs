.. _uptimerobot:


uptimerobot - Pause and start Uptime Robot monitoring
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module will let you start and pause Uptime Robot Monitoring


Requirements
------------

  * Valid Uptime Robot API Key


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
    <td>apikey<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Uptime Robot API key.</div></td></tr>
            <tr>
    <td>monitorid<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>ID of the monitor to check.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>started</li><li>paused</li></ul></td>
        <td><div>Define whether or not the monitor should be running or paused.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Pause the monitor with an ID of 12345.
    - uptimerobot: monitorid=12345
               apikey=12345-1234512345
               state=paused
    
    # Start the monitor with an ID of 12345.
    - uptimerobot: monitorid=12345
               apikey=12345-1234512345
               state=started
    


Notes
-----

.. note:: Support for adding and removing monitors and alert contacts has not yet been implemented.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

