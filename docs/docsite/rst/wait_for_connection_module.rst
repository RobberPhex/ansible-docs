.. _wait_for_connection:


wait_for_connection - Waits until remote system is reachable/usable
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Waits for a total of ``timeout`` seconds.
* Retries the transport connection after a timeout of ``connect_timeout``.
* Tests the transport connection every ``sleep`` seconds.
* This module makes use of internal ansible transport (and configuration) and the ping/win_ping module to guarantee correct end-to-end functioning.




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
                <tr><td>connect_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5</td>
        <td></td>
        <td><div>Maximum number of seconds to wait for a connection to happen before closing and retrying.</div>        </td></tr>
                <tr><td>delay<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of seconds to wait before starting to poll.</div>        </td></tr>
                <tr><td>sleep<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td></td>
        <td><div>Number of seconds to sleep between checks.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>600</td>
        <td></td>
        <td><div>Maximum number of seconds to wait for.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Wait 600 seconds for target connection to become reachable/usable
      wait_for_connection:
    
    - name: Wait 300 seconds, but only start checking after 60 seconds
      wait_for_connection:
        delay: 60
        timeout: 300
    
    # Wake desktops, wait for them to become ready and continue playbook
    - hosts: all
      gather_facts: no
      tasks:
      - name: Send magic Wake-On-Lan packet to turn on individual systems
        wakeonlan:
          mac: '{{ mac }}'
          broadcast: 192.168.0.255
        delegate_to: localhost
    
      - name: Wait for system to become reachable
        wait_for_connection:
    
      - name: Gather facts for first time
        setup:
    
    # Build a new VM, wait for it to become ready and continue playbook
    - hosts: all
      gather_facts: no
      tasks:
      - name: Clone new VM, if missing
        vmware_guest:
          hostname: '{{ vcenter_ipaddress }}'
          name: '{{ inventory_hostname_short }}'
          template: Windows 2012R2
          customization:
            hostname: '{{ vm_shortname }}'
            runonce:
            - powershell.exe -ExecutionPolicy Unrestricted -File C:\Windows\Temp\ConfigureRemotingForAnsible.ps1 -ForceNewSSLCert -EnableCredSSP
        delegate_to: localhost
    
      - name: Wait for system to become reachable over WinRM
        wait_for_connection:
          timeout: 900
    
      - name: Gather facts for first time
        setup:

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
        <td> elapsed </td>
        <td> The number of seconds that elapsed waiting for the connection to appear. </td>
        <td align=center> always </td>
        <td align=center> integer </td>
        <td align=center> 23 </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
