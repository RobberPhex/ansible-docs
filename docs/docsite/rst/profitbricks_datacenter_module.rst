.. _profitbricks_datacenter:


profitbricks_datacenter - Create or destroy a ProfitBricks Virtual Datacenter.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This is a simple module that supports creating or removing vDCs. A vDC is required before you can create servers. This module has a dependency on profitbricks >= 1.0.0


Requirements (on host that executes module)
-------------------------------------------

  * profitbricks


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
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The description of the virtual datacenter.</div>        </td></tr>
                <tr><td>location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>us/las</td>
        <td><ul><li>us/las</li><li>de/fra</li><li>de/fkb</li></ul></td>
        <td><div>The datacenter location.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the virtual datacenter.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>create or terminate datacenters</div>        </td></tr>
                <tr><td>subscription_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>THe ProfitBricks password. Overrides the PB_PASSWORD environment variable.</div>        </td></tr>
                <tr><td>subscription_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The ProfitBricks username. Overrides the PB_SUBSCRIPTION_ID environment variable.</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>wait for the datacenter to be created before returning</div>        </td></tr>
                <tr><td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>600</td>
        <td></td>
        <td><div>how long before wait gives up, in seconds</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    # Create a Datacenter
    - profitbricks_datacenter:
        datacenter: Tardis One
        wait_timeout: 500
    
    # Destroy a Datacenter. This will remove all servers, volumes, and other objects in the datacenter.
    - profitbricks_datacenter:
        datacenter: Tardis One
        wait_timeout: 500
        state: absent
    





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
