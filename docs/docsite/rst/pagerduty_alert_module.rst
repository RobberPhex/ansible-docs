.. _pagerduty_alert:


pagerduty_alert - Trigger, acknowledge or resolve PagerDuty incidents
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.9


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module will let you trigger, acknowledge or resolve a PagerDuty incident by sending events


Requirements (on host that executes module)
-------------------------------------------

  * PagerDuty API access


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
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The pagerduty API key (readonly access), generated on the pagerduty site.</div>        </td></tr>
                <tr><td>client<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of the monitoring client that is triggering this event.</div>        </td></tr>
                <tr><td>client_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The URL of the monitoring client that is triggering this event.</div>        </td></tr>
                <tr><td>desc<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Created via Ansible</td>
        <td></td>
        <td><div>For <code>triggered</code> <em>state</em> - Required. Short description of the problem that led to this trigger. This field (or a truncated version) will be used when generating phone calls, SMS messages and alert emails. It will also appear on the incidents tables in the PagerDuty UI. The maximum length is 1024 characters.</div><div>For <code>acknowledged</code> or <code>resolved</code> <em>state</em> - Text that will appear in the incident's log associated with this event.</div>        </td></tr>
                <tr><td>incident_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Identifies the incident to which this <em>state</em> should be applied.</div><div>For <code>triggered</code> <em>state</em> - If there's no open (i.e. unresolved) incident with this key, a new one will be created. If there's already an open incident with a matching key, this event will be appended to that incident's log. The event key provides an easy way to "de-dup" problem reports.</div><div>For <code>acknowledged</code> or <code>resolved</code> <em>state</em> - This should be the incident_key you received back when the incident was first opened by a trigger event. Acknowledge events referencing resolved or nonexistent incidents will be discarded.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>PagerDuty unique subdomain.</div>        </td></tr>
                <tr><td>service_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The GUID of one of your "Generic API" services.</div><div>This is the "service key" listed on a Generic API's service detail page.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>triggered</li><li>acknowledged</li><li>resolved</li></ul></td>
        <td><div>Type of event to be sent.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Trigger an incident with just the basic options
    - pagerduty_alert:
        name: companyabc
        service_key: xxx
        api_key: yourapikey
        state: triggered
        desc: problem that led to this trigger
    
    # Trigger an incident with more options
    - pagerduty_alert:
        service_key: xxx
        api_key: yourapikey
        state: triggered
        desc: problem that led to this trigger
        incident_key: somekey
        client: Sample Monitoring Service
        client_url: http://service.example.com
    
    # Acknowledge an incident based on incident_key
    - pagerduty_alert:
        service_key: xxx
        api_key: yourapikey
        state: acknowledged
        incident_key: somekey
        desc: "some text for incident's log"
    
    # Resolve an incident based on incident_key
    - pagerduty_alert:
        service_key: xxx
        api_key: yourapikey
        state: resolved
        incident_key: somekey
        desc: "some text for incident's log"





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
