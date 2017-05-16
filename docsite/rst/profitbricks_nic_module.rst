.. _profitbricks_nic:


profitbricks_nic - Create or Remove a NIC.
++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module allows you to create or restore a volume snapshot. This module has a dependency on profitbricks >= 1.0.0


Requirements
------------

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
            <tr>
    <td>datacenter<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The datacenter in which to operate.</div></td></tr>
            <tr>
    <td>lan<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The LAN to place the NIC on. You can pass a LAN that doesn't exist and it will be created. Required on create.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name or ID of the NIC. This is only required on deletes, but not on create.</div></td></tr>
            <tr>
    <td>server<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The server name or ID.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource</div></td></tr>
            <tr>
    <td>subscription_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>THe ProfitBricks password. Overrides the PB_PASSWORD environement variable.</div></td></tr>
            <tr>
    <td>subscription_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The ProfitBricks username. Overrides the PB_SUBSCRIPTION_ID environement variable.</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>wait for the operation to complete before returning</div></td></tr>
            <tr>
    <td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>600</td>
        <td><ul></ul></td>
        <td><div>how long before wait gives up, in seconds</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    # Create a NIC
    - profitbricks_nic:
        datacenter: Tardis One
        server: node002
        lan: 2
        wait_timeout: 500
        state: present
    
    # Remove a NIC
    - profitbricks_nic:
        datacenter: Tardis One
        server: node002
        name: 7341c2454f
        wait_timeout: 500
        state: absent
    




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

