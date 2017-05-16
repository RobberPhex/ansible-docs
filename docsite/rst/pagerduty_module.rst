.. _pagerduty:


pagerduty - Create PagerDuty maintenance windows
++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module will let you create PagerDuty maintenance windows


Requirements
------------

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
            <tr>
    <td>desc<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Created by Ansible</td>
        <td><ul></ul></td>
        <td><div>Short description of maintenance window.</div></td></tr>
            <tr>
    <td>hours<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>Length of maintenance window in hours.</div></td></tr>
            <tr>
    <td>minutes<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Maintenance window in minutes (this is added to the hours).</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>PagerDuty unique subdomain.</div></td></tr>
            <tr>
    <td>passwd<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>PagerDuty user password.</div></td></tr>
            <tr>
    <td>requester_id<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>ID of user making the request. Only needed when using a token and creating a maintenance_window.</div></td></tr>
            <tr>
    <td>service<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A comma separated list of PagerDuty service IDs.</div></br>
        <div style="font-size: small;">aliases: services<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>running</li><li>started</li><li>ongoing</li><li>absent</li></ul></td>
        <td><div>Create a maintenance window or get a list of ongoing windows.</div></td></tr>
            <tr>
    <td>token<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A pagerduty token, generated on the pagerduty site. Can be used instead of user/passwd combination.</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>PagerDuty user ID.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5.1)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # List ongoing maintenance windows using a user/passwd
    - pagerduty: name=companyabc user=example@example.com passwd=password123 state=ongoing
    
    # List ongoing maintenance windows using a token
    - pagerduty: name=companyabc token=xxxxxxxxxxxxxx state=ongoing
    
    # Create a 1 hour maintenance window for service FOO123, using a user/passwd
    - pagerduty: name=companyabc
                 user=example@example.com
                 passwd=password123
                 state=running
                 service=FOO123
    
    # Create a 5 minute maintenance window for service FOO123, using a token
    - pagerduty: name=companyabc
                 token=xxxxxxxxxxxxxx
                 hours=0
                 minutes=5
                 state=running
                 service=FOO123
    
    
    # Create a 4 hour maintenance window for service FOO123 with the description "deployment".
    - pagerduty: name=companyabc
                 user=example@example.com
                 passwd=password123
                 state=running
                 service=FOO123
                 hours=4
                 desc=deployment
      register: pd_window
    
    # Delete the previous maintenance window
    - pagerduty: name=companyabc
                 user=example@example.com
                 passwd=password123
                 state=absent
                 service={{ pd_window.result.maintenance_window.id }}




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

