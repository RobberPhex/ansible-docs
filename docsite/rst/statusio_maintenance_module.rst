.. _statusio_maintenance:


statusio_maintenance - Create maintenance windows for your status.io dashboard
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Creates a maintenance window for status.io
Deletes a maintenance window for status.io




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
    <td>all_infrastructure_affected<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If it affects all components and containers</div></td></tr>
            <tr>
    <td>api_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Your unique API ID from status.io</div></td></tr>
            <tr>
    <td>api_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Your unique API Key from status.io</div></td></tr>
            <tr>
    <td>automation<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Automatically start and end the maintenance window</div></td></tr>
            <tr>
    <td>components<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The given name of your component (server name)</div></br>
        <div style="font-size: small;">aliases: component<div></td></tr>
            <tr>
    <td>containers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The given name of your container (data center)</div></br>
        <div style="font-size: small;">aliases: container<div></td></tr>
            <tr>
    <td>desc<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Created by Ansible</td>
        <td><ul></ul></td>
        <td><div>Message describing the maintenance window</div></td></tr>
            <tr>
    <td>maintenance_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The maintenance id number when deleting a maintenance window</div></td></tr>
            <tr>
    <td>maintenance_notify_1_hr<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Notify subscribers 1 hour before maintenance start time</div></td></tr>
            <tr>
    <td>maintenance_notify_24_hr<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Notify subscribers 24 hours before maintenance start time</div></td></tr>
            <tr>
    <td>maintenance_notify_72_hr<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Notify subscribers 72 hours before maintenance start time</div></td></tr>
            <tr>
    <td>maintenance_notify_now<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Notify subscribers now</div></td></tr>
            <tr>
    <td>minutes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>The length of time in UTC that the maintenance will run             (starting from playbook runtime)</div></td></tr>
            <tr>
    <td>start_date<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Date maintenance is expected to start (Month/Day/Year) (UTC)</div><div>End Date is worked out from start_date + minutes</div></td></tr>
            <tr>
    <td>start_time<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Time maintenance is expected to start (Hour:Minutes) (UTC)</div><div>End Time is worked out from start_time + minutes</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Desired state of the package.</div></td></tr>
            <tr>
    <td>statuspage<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Your unique StatusPage ID from status.io</div></td></tr>
            <tr>
    <td>title<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>A new maintenance window</td>
        <td><ul></ul></td>
        <td><div>A descriptive title for the maintenance window</div></td></tr>
            <tr>
    <td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https://api.status.io</td>
        <td><ul></ul></td>
        <td><div>Status.io API URL. A private apiary can be used instead.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a maintenance window for 10 minutes on server1.example.com, with
    automation to stop the maintenance.
    - statusio_maintenance:
          title: "Router Upgrade from ansible"
          desc: "Performing a Router Upgrade"
          components: "server1.example.com"
          api_id: "api_id"
          api_key: "api_key"
          statuspage: "statuspage_id"
          maintenance_notify_1_hr: true
          automation: true
    
    # Create a maintenance window for 60 minutes on multiple hosts
    - name: "Create maintenance window for server1 and server2"
      local_action:
        module: statusio_maintenance
        title: "Routine maintenance"
        desc: "Some security updates"
        components:
          - "server1.example.com
          - "server2.example.com"
        minutes: "60"
        api_id: "api_id"
        api_key: "api_key"
        statuspage: "statuspage_id"
        maintenance_notify_1_hr: true
        automation: true
    
    # Create a future maintenance window for 24 hours to all hosts inside the
    # Primary Data Center
    - statusio_maintenance:
          title: Data center downtime
          desc: Performing a Upgrade to our data center
          components: "Primary Data Center"
          api_id: "api_id"
          api_key: "api_key"
          statuspage: "statuspage_id"
          start_date: "01/01/2016"
          start_time: "12:00"
          minutes: 1440
    
    # Delete a maintenance window
    - statusio_maintenance:
         title: "Remove a maintenance window"
         maintenance_id: "561f90faf74bc94a4700087b"
         statuspage: "statuspage_id"
         api_id: "api_id"
         api_key: "api_key"
         state: absent
    


Notes
-----

.. note:: You can use the apiary API url (http://docs.statusio.apiary.io/) to capture API traffic
.. note:: Use start_date and start_time with minutes to set future maintenance window


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

