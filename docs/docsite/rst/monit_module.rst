.. _monit:


monit - Manage the state of a program monitored via Monit
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage the state of a program monitored via *Monit*




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
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the <em>monit</em> program/process to manage</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>started</li><li>stopped</li><li>restarted</li><li>monitored</li><li>unmonitored</li><li>reloaded</li></ul></td>
        <td><div>The state of service</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>300</td>
        <td></td>
        <td><div>If there are pending actions for the service monitored by monit, then Ansible will check for up to this many seconds to verify the the requested action has been performed. Ansible will sleep for five seconds between each check.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Manage the state of program "httpd" to be in "started" state.
    - monit:
        name: httpd
        state: started





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
