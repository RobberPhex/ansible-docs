.. _nagios:


nagios - Perform common tasks in Nagios related to downtime and notifications.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The ``nagios`` module has two basic functions: scheduling downtime and toggling alerts for services or hosts.
* All actions require the *host* parameter to be given explicitly. In playbooks you can use the ``{{inventory_hostname}}`` variable to refer to the host the playbook is currently running on.
* You can specify multiple services at once by separating them with commas, .e.g., ``services=httpd,nfs,puppet``.
* When specifying what service to handle there is a special service value, *host*, which will handle alerts/downtime for the *host itself*, e.g., ``service=host``. This keyword may not be given with other services at the same time. *Setting alerts/downtime for a host does not affect alerts/downtime for any of the services running on it.* To schedule downtime for all services on particular host use keyword "all", e.g., ``service=all``.
* When using the ``nagios`` module you will need to specify your Nagios server using the ``delegate_to`` parameter.




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
                <tr><td>action<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>downtime</li><li>delete_downtime</li><li>enable_alerts</li><li>disable_alerts</li><li>silence</li><li>unsilence</li><li>silence_nagios</li><li>unsilence_nagios</li><li>command</li><li>servicegroup_service_downtime</li><li>servicegroup_host_downtime</li></ul></td>
        <td><div>Action to take.</div><div>servicegroup options were added in 2.0.</div><div>delete_downtime options were added in 2.2.</div>        </td></tr>
                <tr><td>author<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Ansible</td>
        <td></td>
        <td><div>Author to leave downtime comments as. Only usable with the <code>downtime</code> action.</div>        </td></tr>
                <tr><td>cmdfile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>auto-detected</td>
        <td></td>
        <td><div>Path to the nagios <em>command file</em> (FIFO pipe). Only required if auto-detection fails.</div>        </td></tr>
                <tr><td>command<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The raw command to send to nagios, which should not include the submitted time header or the line-feed <b>Required</b> option when using the <code>command</code> action.</div>        </td></tr>
                <tr><td>comment<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>Scheduling downtime</td>
        <td></td>
        <td><div>Comment for <code>downtime</code> action.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Host to operate on in Nagios.</div>        </td></tr>
                <tr><td>minutes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30</td>
        <td></td>
        <td><div>Minutes to schedule downtime for.</div><div>Only usable with the <code>downtime</code> action.</div>        </td></tr>
                <tr><td>servicegroup<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The Servicegroup we want to set downtimes/alerts for. <b>Required</b> option when using the <code>servicegroup_service_downtime</code> amd <code>servicegroup_host_downtime</code>.</div>        </td></tr>
                <tr><td>services<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>What to manage downtime/alerts for. Separate multiple services with commas. <code>service</code> is an alias for <code>services</code>. <b>Required</b> option when using the <code>downtime</code>, <code>enable_alerts</code>, and <code>disable_alerts</code> actions.</div></br>
    <div style="font-size: small;">aliases: service<div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # set 30 minutes of apache downtime
    - nagios:
        action: downtime
        minutes: 30
        service: httpd
        host: '{{ inventory_hostname }}'
    
    # schedule an hour of HOST downtime
    - nagios:
        action: downtime
        minutes: 60
        service: host
        host: '{{ inventory_hostname }}'
    
    # schedule an hour of HOST downtime, with a comment describing the reason
    - nagios:
        action: downtime
        minutes: 60
        service: host
        host: '{{ inventory_hostname }}'
        comment: Rebuilding machine
    
    # schedule downtime for ALL services on HOST
    - nagios:
        action: downtime
        minutes: 45
        service: all
        host: '{{ inventory_hostname }}'
    
    # schedule downtime for a few services
    - nagios:
        action: downtime
        services: frob,foobar,qeuz
        host: '{{ inventory_hostname }}'
    
    # set 30 minutes downtime for all services in servicegroup foo
    - nagios:
        action: servicegroup_service_downtime
        minutes: 30
        servicegroup: foo
        host: '{{ inventory_hostname }}'
    
    # set 30 minutes downtime for all host in servicegroup foo
    - nagios:
        action: servicegroup_host_downtime
        minutes: 30
        servicegroup: foo
        host: '{{ inventory_hostname }}'
    
    # delete all downtime for a given host
    - nagios:
        action: delete_downtime
        host: '{{ inventory_hostname }}'
        service: all
    
    # delete all downtime for HOST with a particular comment
    - nagios:
        action: delete_downtime
        host: '{{ inventory_hostname }}'
        service: host
        comment: Planned maintenance
    
    # enable SMART disk alerts
    - nagios:
        action: enable_alerts
        service: smart
        host: '{{ inventory_hostname }}'
    
    # "two services at once: disable httpd and nfs alerts"
    - nagios:
        action: disable_alerts
        service: httpd,nfs
        host: '{{ inventory_hostname }}'
    
    # disable HOST alerts
    - nagios:
        action: disable_alerts
        service: host
        host: '{{ inventory_hostname }}'
    
    # silence ALL alerts
    - nagios:
        action: silence
        host: '{{ inventory_hostname }}'
    
    # unsilence all alerts
    - nagios:
        action: unsilence
        host: '{{ inventory_hostname }}'
    
    # SHUT UP NAGIOS
    - nagios:
        action: silence_nagios
    
    # ANNOY ME NAGIOS
    - nagios:
        action: unsilence_nagios
    
    # command something
    - nagios:
        action: command
        command: DISABLE_FAILURE_PREDICTION





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
