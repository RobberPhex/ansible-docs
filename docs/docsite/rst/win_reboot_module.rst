.. _win_reboot:


win_reboot - Reboot a windows machine
+++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Reboot a Windows machine, wait for it to go down, come back up, and respond to commands.




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
                <tr><td>connect_timeout_sec<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5</td>
        <td></td>
        <td><div>Maximum seconds to wait for a single successful TCP connection to the WinRM endpoint before trying again</div>        </td></tr>
                <tr><td>msg<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Reboot initiated by Ansible</td>
        <td></td>
        <td><div>Message to display to users</div>        </td></tr>
                <tr><td>pre_reboot_delay_sec<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>2</td>
        <td></td>
        <td><div>Seconds for shutdown to wait before requesting reboot</div>        </td></tr>
                <tr><td>reboot_timeout_sec<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>600</td>
        <td></td>
        <td><div>Maximum seconds to wait for machine to re-appear on the network and respond to a test command</div><div>This timeout is evaluated separately for both network appearance and test command success (so maximum clock time is actually twice this value)</div>        </td></tr>
                <tr><td>shutdown_timeout_sec<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>600</td>
        <td></td>
        <td><div>Maximum seconds to wait for shutdown to occur</div><div>Increase this timeout for very slow hardware, large update applications, etc</div>        </td></tr>
                <tr><td>test_command<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>whoami</td>
        <td></td>
        <td><div>Command to expect success for to determine the machine is ready for management</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Unconditionally reboot the machine with all defaults
    - win_reboot:
    
    # Apply updates and reboot if necessary
    - win_updates:
      register: update_result
    - win_reboot:
      when: update_result.reboot_required
    
    # Reboot a slow machine that might have lots of updates to apply
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

Notes
-----

.. note::
    - If a shutdown was already scheduled on the system, ``win_reboot`` will abort the scheduled shutdown and enforce its own shutdown.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
