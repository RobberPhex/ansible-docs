.. _clc_modify_server:


clc_modify_server - modify servers in CenturyLink Cloud.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

An Ansible module to modify servers in CenturyLink Cloud.


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
    <td>alert_policy_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The alert policy id to be associated to the server. This is mutually exclusive with 'alert_policy_name'</div></td></tr>
            <tr>
    <td>alert_policy_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The alert policy name to be associated to the server. This is mutually exclusive with 'alert_policy_id'</div></td></tr>
            <tr>
    <td>anti_affinity_policy_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The anti affinity policy id to be set for a hyper scale server. This is mutually exclusive with 'anti_affinity_policy_name'</div></td></tr>
            <tr>
    <td>anti_affinity_policy_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The anti affinity policy name to be set for a hyper scale server. This is mutually exclusive with 'anti_affinity_policy_id'</div></td></tr>
            <tr>
    <td>cpu<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>How many CPUs to update on the server</div></td></tr>
            <tr>
    <td>memory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Memory (in GB) to set to the server.</div></td></tr>
            <tr>
    <td>server_ids<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of server Ids to modify.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>The state to insure that the provided resources are in.</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Whether to wait for the provisioning tasks to finish before returning.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note - You must set the CLC_V2_API_USERNAME And CLC_V2_API_PASSWD Environment variables before running these examples
    
    - name: set the cpu count to 4 on a server
      clc_modify_server:
        server_ids:
            - UC1TESTSVR01
            - UC1TESTSVR02
        cpu: 4
        state: present
    
    - name: set the memory to 8GB on a server
      clc_modify_server:
        server_ids:
            - UC1TESTSVR01
            - UC1TESTSVR02
        memory: 8
        state: present
    
    - name: set the anti affinity policy on a server
      clc_modify_server:
        server_ids:
            - UC1TESTSVR01
            - UC1TESTSVR02
        anti_affinity_policy_name: 'aa_policy'
        state: present
    
    - name: remove the anti affinity policy on a server
      clc_modify_server:
        server_ids:
            - UC1TESTSVR01
            - UC1TESTSVR02
        anti_affinity_policy_name: 'aa_policy'
        state: absent
    
    - name: add the alert policy on a server
      clc_modify_server:
        server_ids:
            - UC1TESTSVR01
            - UC1TESTSVR02
        alert_policy_name: 'alert_policy'
        state: present
    
    - name: remove the alert policy on a server
      clc_modify_server:
        server_ids:
            - UC1TESTSVR01
            - UC1TESTSVR02
        alert_policy_name: 'alert_policy'
        state: absent
    
    - name: set the memory to 16GB and cpu to 8 core on a lust if servers
      clc_modify_server:
        server_ids:
            - UC1TESTSVR01
            - UC1TESTSVR02
        cpu: 8
        memory: 16
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
        <td> server_ids </td>
        <td> The list of server ids that are changed </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> ['UC1TEST-SVR01', 'UC1TEST-SVR02'] </td>
    </tr>
            <tr>
        <td> servers </td>
        <td> The list of server objects that are changed </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> [{'status': 'active', 'description': 'test-server', 'changeInfo': {'modifiedBy': 'service.wfad', 'modifiedDate': 1438196820, 'createdBy': 'service.wfad', 'createdDate': 1438196820}, 'ipaddress': '10.120.45.23', 'storageType': 'standard', 'type': 'standard', 'isTemplate': False, 'links': [{'href': '/v2/servers/wfad/test-server', 'id': 'test-server', 'rel': 'self', 'verbs': ['GET', 'PATCH', 'DELETE']}, {'href': '/v2/groups/wfad/086ac1dfe0b6411989e8d1b77c4065f0', 'id': '086ac1dfe0b6411989e8d1b77c4065f0', 'rel': 'group'}, {'href': '/v2/accounts/wfad', 'id': 'wfad', 'rel': 'account'}, {'href': '/v2/billing/wfad/serverPricing/test-server', 'rel': 'billing'}, {'href': '/v2/servers/wfad/test-server/publicIPAddresses', 'verbs': ['POST'], 'rel': 'publicIPAddresses'}, {'href': '/v2/servers/wfad/test-server/credentials', 'rel': 'credentials'}, {'href': '/v2/servers/wfad/test-server/statistics', 'rel': 'statistics'}, {'href': '/v2/servers/wfad/510ec21ae82d4dc89d28479753bf736a/upcomingScheduledActivities', 'rel': 'upcomingScheduledActivities'}, {'href': '/v2/servers/wfad/510ec21ae82d4dc89d28479753bf736a/scheduledActivities', 'verbs': ['GET', 'POST'], 'rel': 'scheduledActivities'}, {'href': '/v2/servers/wfad/test-server/capabilities', 'rel': 'capabilities'}, {'href': '/v2/servers/wfad/test-server/alertPolicies', 'verbs': ['POST'], 'rel': 'alertPolicyMappings'}, {'href': '/v2/servers/wfad/test-server/antiAffinityPolicy', 'verbs': ['PUT', 'DELETE'], 'rel': 'antiAffinityPolicyMapping'}, {'href': '/v2/servers/wfad/test-server/cpuAutoscalePolicy', 'verbs': ['PUT', 'DELETE'], 'rel': 'cpuAutoscalePolicyMapping'}], 'id': 'test-server', 'locationId': 'UC1', 'details': {'hostName': '', 'powerState': 'started', 'ipAddresses': [{'internal': '10.1.1.1'}], 'disks': [{'partitionPaths': [], 'id': '0:0', 'sizeGB': 1}, {'partitionPaths': [], 'id': '0:1', 'sizeGB': 2}, {'partitionPaths': [], 'id': '0:2', 'sizeGB': 14}], 'diskCount': 3, 'snapshots': [], 'memoryMB': 1024, 'alertPolicies': [], 'memoryGB': 1, 'storageGB': 17, 'customFields': [], 'cpu': 1, 'inMaintenanceMode': False, 'partitions': []}, 'osType': 'Ubuntu 14 64-bit', 'os': 'ubuntu14_64Bit', 'groupId': '086ac1dfe0b6411989e8d1b77c4065f0', 'name': 'test-server'}] </td>
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

