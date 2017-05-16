.. _monit:


monit - Manage the state of a program monitored via Monit
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage the state of a program monitored via *Monit*




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
        <td><div>The name of the <em>monit</em> program/process to manage</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>started</li><li>stopped</li><li>restarted</li><li>monitored</li><li>unmonitored</li><li>reloaded</li></ul></td>
        <td><div>The state of service</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Manage the state of program "httpd" to be in "started" state.
    - monit: name=httpd state=started




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

