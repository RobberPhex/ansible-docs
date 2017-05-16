.. _clc_alert_policy:


clc_alert_policy - Create or Delete Alert Policies at CenturyLink Cloud.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

An Ansible module to Create or Delete Alert Policies at CenturyLink Cloud.


Requirements (on host that executes module)
-------------------------------------------

  * python = 2.7
  * requests >= 2.5.0
  * clc-sdk


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
    <td>alert_recipients<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A list of recipient email ids to notify the alert. This is required for state 'present'</div></td></tr>
            <tr>
    <td>alias<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The alias of your CLC Account</div></td></tr>
            <tr>
    <td>duration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The length of time in minutes that the condition must exceed the threshold. This is required for state 'present'</div></td></tr>
            <tr>
    <td>id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The alert policy id. This is mutually exclusive with name</div></td></tr>
            <tr>
    <td>metric<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>cpu</li><li>memory</li><li>disk</li></ul></td>
        <td><div>The metric on which to measure the condition that will trigger the alert. This is required for state 'present'</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the alert policy. This is mutually exclusive with id</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether to create or delete the policy.</div></td></tr>
            <tr>
    <td>threshold<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The threshold that will trigger the alert when the metric equals or exceeds it. This is required for state 'present' This number represents a percentage and must be a value between 5.0 - 95.0 that is a multiple of 5.0</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note - You must set the CLC_V2_API_USERNAME And CLC_V2_API_PASSWD Environment variables before running these examples
    
    ---
    - name: Create Alert Policy Example
      hosts: localhost
      gather_facts: False
      connection: local
      tasks:
        - name: Create an Alert Policy for disk above 80% for 5 minutes
          clc_alert_policy:
            alias: wfad
            name: 'alert for disk > 80%'
            alert_recipients:
                - test1@centurylink.com
                - test2@centurylink.com
            metric: 'disk'
            duration: '00:05:00'
            threshold: 80
            state: present
          register: policy
    
        - name: debug
          debug: var=policy
    
    ---
    - name: Delete Alert Policy Example
      hosts: localhost
      gather_facts: False
      connection: local
      tasks:
        - name: Delete an Alert Policy
          clc_alert_policy:
            alias: wfad
            name: 'alert for disk > 80%'
            state: absent
          register: policy
    
        - name: debug
          debug: var=policy

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
        <td> policy </td>
        <td> The alert policy information </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> {'name': 'test_alert', 'actions': [{'action': 'email', 'settings': {'recipients': ['user1@domain.com', 'user1@domain.com']}}], 'id': 'ba54ac54a60d4a4f1ed6d48c1ce240a7', 'links': [{'href': '/v2/alertPolicies/alias/ba54ac54a60d4a4fb1d6d48c1ce240a7', 'verbs': ['GET', 'DELETE', 'PUT'], 'rel': 'self'}], 'triggers': [{'duration': '00:05:00', 'threshold': 80.0, 'metric': 'disk'}]} </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> A flag indicating if any change was made or not </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: To use this module, it is required to set the below environment variables which enables access to the Centurylink Cloud - CLC_V2_API_USERNAME, the account login id for the centurylink cloud - CLC_V2_API_PASSWORD, the account password for the centurylink cloud
.. note:: Alternatively, the module accepts the API token and account alias. The API token can be generated using the CLC account login and password via the HTTP api call @ https://api.ctl.io/v2/authentication/login - CLC_V2_API_TOKEN, the API token generated from https://api.ctl.io/v2/authentication/login - CLC_ACCT_ALIAS, the account alias associated with the centurylink cloud
.. note:: Users can set CLC_V2_API_URL to specify an endpoint for pointing to a different CLC environment.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

