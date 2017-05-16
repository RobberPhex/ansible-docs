.. _openvswitch_db:


openvswitch_db - Configure open vswitch database.
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Set column values in record in database table.


Requirements
------------

  * ovs-vsctl >= 2.3.3


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
    <td>column<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Identifies the column in the record.</div></td></tr>
            <tr>
    <td>key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Identifies the key in the record column</div></td></tr>
            <tr>
    <td>record<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Identifies the recoard in the table.</div></td></tr>
            <tr>
    <td>table<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Identifies the table in the database.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5</td>
        <td><ul></ul></td>
        <td><div>How long to wait for ovs-vswitchd to respond</div></td></tr>
            <tr>
    <td>value<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Expected value for the table, record, column and key.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Increase the maximum idle time to 50 seconds before pruning unused kernel
    # rules.
    - openvswitch_db: table=open_vswitch record=. col=other_config key=max-idle
                      value=50000
    
    # Disable in band copy
    - openvswitch_db: table=Bridge record=br-int col=other_config
                      key=disable-in-band value=true




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

