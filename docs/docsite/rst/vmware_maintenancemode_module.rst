.. _vmware_maintenancemode:


vmware_maintenancemode - Place a host into maintenance mode
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Place an ESXI host into maintenance mode
* Support for VSAN compliant maintenance mode when selected


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * PyVmomi


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
                <tr><td>esxi_hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the host as defined in vCenter</div>        </td></tr>
                <tr><td>evacuate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>If True, evacuate all powered off VMs</div>        </td></tr>
                <tr><td>hostname<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The hostname or IP address of the vSphere vCenter.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The password of the vSphere vCenter.</div></br>
    <div style="font-size: small;">aliases: pass, pwd<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Enter or exit maintenance mode</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify a timeout for the operation</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The username of the vSphere vCenter.</div></br>
    <div style="font-size: small;">aliases: user, admin<div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Allows connection when SSL certificates are not valid. Set to false when certificates are not trusted.</div>        </td></tr>
                <tr><td>vsan_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>ensureObjectAccessibility</li><li>evacuateAllData</li><li>noAction</li></ul></td>
        <td><div>Specify which VSAN compliant mode to enter</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Enter VSAN-Compliant Maintenance Mode
      local_action:
        module: vmware_maintenancemode
        hostname: vc_host
        username: vc_user
        password: vc_pass
        esxi_hostname: esxi.host.example
        vsan: ensureObjectAccessibility
        evacuate: yes
        timeout: 3600
        state: present

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
        <td> status </td>
        <td> Action taken </td>
        <td align=center>  </td>
        <td align=center> string </td>
        <td align=center> ENTER </td>
    </tr>
            <tr>
        <td> hostsystem </td>
        <td> Name of vim reference </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 'vim.HostSystem:host-236' </td>
    </tr>
            <tr>
        <td> hostname </td>
        <td> Name of host in vCenter </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> esxi.local.domain </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Tested on vSphere 5.5 and 6.0



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
