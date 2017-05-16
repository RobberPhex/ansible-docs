.. _clc_group:


clc_group - Create/delete Server Groups at Centurylink Cloud
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create or delete Server Groups at Centurylink Centurylink Cloud


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
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A description of the Server Group</div></td></tr>
            <tr>
    <td>location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Datacenter to create the group in. If location is not provided, the group gets created in the default datacenter associated with the account</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the Server Group</div></td></tr>
            <tr>
    <td>parent<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The parent group of the server group. If parent is not provided, it creates the group at top level.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether to create or delete the group</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Whether to wait for the tasks to finish before returning.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    # Create a Server Group
    
    ---
    - name: Create Server Group
      hosts: localhost
      gather_facts: False
      connection: local
      tasks:
        - name: Create / Verify a Server Group at CenturyLink Cloud
          clc_group:
            name: 'My Cool Server Group'
            parent: 'Default Group'
            state: present
          register: clc
    
        - name: debug
          debug: var=clc
    
    # Delete a Server Group
    
    ---
    - name: Delete Server Group
      hosts: localhost
      gather_facts: False
      connection: local
      tasks:
        - name: Delete / Verify Absent a Server Group at CenturyLink Cloud
          clc_group:
            name: 'My Cool Server Group'
            parent: 'Default Group'
            state: absent
          register: clc
    
        - name: debug
          debug: var=clc
    

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
        <td> group </td>
        <td> The group information </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> {'status': 'active', 'description': 'test group', 'links': [{'href': '/v2/groups/wfad', 'verbs': ['POST'], 'rel': 'createGroup'}, {'href': '/v2/servers/wfad', 'verbs': ['POST'], 'rel': 'createServer'}, {'href': '/v2/groups/wfad/bb5f12a3c6044ae4ad0a03e73ae12cd1', 'verbs': ['GET', 'PATCH', 'DELETE'], 'rel': 'self'}, {'href': '/v2/groups/wfad/086ac1dfe0b6411989e8d1b77c4065f0', 'id': '086ac1dfe0b6411989e8d1b77c4065f0', 'rel': 'parentGroup'}, {'href': '/v2/groups/wfad/bb5f12a3c6044ae4ad0a03e73ae12cd1/defaults', 'verbs': ['GET', 'POST'], 'rel': 'defaults'}, {'href': '/v2/groups/wfad/bb5f12a3c6044ae4ad0a03e73ae12cd1/billing', 'rel': 'billing'}, {'href': '/v2/groups/wfad/bb5f12a3c6044ae4ad0a03e73ae12cd1/archive', 'rel': 'archiveGroupAction'}, {'href': '/v2/groups/wfad/bb5f12a3c6044ae4ad0a03e73ae12cd1/statistics', 'rel': 'statistics'}, {'href': '/v2/groups/wfad/bb5f12a3c6044ae4ad0a03e73ae12cd1/upcomingScheduledActivities', 'rel': 'upcomingScheduledActivities'}, {'href': '/v2/groups/wfad/bb5f12a3c6044ae4ad0a03e73ae12cd1/horizontalAutoscalePolicy', 'verbs': ['GET', 'PUT', 'DELETE'], 'rel': 'horizontalAutoscalePolicyMapping'}, {'href': '/v2/groups/wfad/bb5f12a3c6044ae4ad0a03e73ae12cd1/scheduledActivities', 'verbs': ['GET', 'POST'], 'rel': 'scheduledActivities'}], 'changeInfo': {'modifiedBy': 'service.wfad', 'modifiedDate': '2015-07-29T18:52:47Z', 'createdBy': 'service.wfad', 'createdDate': '2015-07-29T18:52:47Z'}, 'locationId': 'UC1', 'groups': [], 'customFields': [], 'type': 'default', 'id': 'bb5f12a3c6044ae4ad0a03e73ae12cd1', 'name': 'test group'} </td>
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

