.. _profitbricks_volume:


profitbricks_volume - Create or destroy a volume.
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Allows you to create or remove a volume from a ProfitBricks datacenter. This module has a dependency on profitbricks >= 1.0.0


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
    <td>auto_increment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether or not to increment a single number in the name for created virtual machines.</div></td></tr>
            <tr>
    <td>bus<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>VIRTIO</td>
        <td><ul><li>IDE</li><li>VIRTIO</li></ul></td>
        <td><div>The bus type.</div></td></tr>
            <tr>
    <td>count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>The number of volumes you wish to create.</div></td></tr>
            <tr>
    <td>datacenter<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The datacenter in which to create the volumes.</div></td></tr>
            <tr>
    <td>disk_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>HDD</td>
        <td><ul></ul></td>
        <td><div>The disk type. Currently only HDD.</div></td></tr>
            <tr>
    <td>image<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The system image ID for the volume, e.g. a3eae284-a2fe-11e4-b187-5f1f641608c8. This can also be a snapshot image ID.</div></td></tr>
            <tr>
    <td>instance_ids<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>list of instance ids, currently only used when state='absent' to remove instances.</div></td></tr>
            <tr>
    <td>licence_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>UNKNOWN</td>
        <td><ul><li>LINUX</li><li>WINDOWS</li><li>UNKNOWN</li><li>OTHER</li></ul></td>
        <td><div>The licence type for the volume. This is used when the image is non-standard.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the volumes. You can enumerate the names using auto_increment.</div></td></tr>
            <tr>
    <td>size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>The size of the volume.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>create or terminate datacenters</div></td></tr>
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
        <td><div>wait for the datacenter to be created before returning</div></td></tr>
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

    
    # Create Multiple Volumes
    
    - profitbricks_volume:
        datacenter: Tardis One
        name: vol%02d
        count: 5
        auto_increment: yes
        wait_timeout: 500
        state: present
    
    # Remove Volumes
    
    - profitbricks_volume:
        datacenter: Tardis One
        instance_ids:
          - 'vol01'
          - 'vol02'
        wait_timeout: 500
        state: absent
    




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

