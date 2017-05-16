.. _win_reboot:


win_reboot - Reboot a windows machine
+++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Reboot a Windows machine, wait for it to go down, come back up, and respond to commands.




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
    <td>connect_timeout_sec<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5</td>
        <td><ul></ul></td>
        <td><div>Maximum seconds to wait for a single successful TCP connection to the WinRM endpoint before trying again</div></td></tr>
            <tr>
    <td>pre_reboot_delay_sec<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>2</td>
        <td><ul></ul></td>
        <td><div>Seconds for shutdown to wait before requesting reboot</div></td></tr>
            <tr>
    <td>reboot_timeout_sec<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>600</td>
        <td><ul></ul></td>
        <td><div>Maximum seconds to wait for machine to re-appear on the network and respond to a test command</div><div>This timeout is evaluated separately for both network appearance and test command success (so maximum clock time is actually twice this value)</div></td></tr>
            <tr>
    <td>shutdown_timeout_sec<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>600</td>
        <td><ul></ul></td>
        <td><div>Maximum seconds to wait for shutdown to occur</div><div>Increase this timeout for very slow hardware, large update applications, etc</div></td></tr>
            <tr>
    <td>test_command<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>whoami</td>
        <td><ul></ul></td>
        <td><div>Command to expect success for to determine the machine is ready for management</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # unconditionally reboot the machine with all defaults
    - win_reboot:
    
    # apply updates and reboot if necessary
    - win_updates:
      register: update_result
    - win_reboot:
      when: update_result.reboot_required
    
    # reboot a slow machine that might have lots of updates to apply
    - win_reboot:
        shutdown_timeout_sec: 3600
        reboot_timeout_sec: 3600

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
        <td> rebooted </td>
        <td> true if the machine was rebooted </td>
        <td align=center> always </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
        
    </table>
    </br></br>



    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

