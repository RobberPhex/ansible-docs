.. _clc_server:


clc_server - Create, Delete, Start and Stop servers in CenturyLink Cloud.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

An Ansible module to Create, Delete, Start and Stop servers in CenturyLink Cloud.


Requirements
------------

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
    <td>add_public_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>False</li><li>True</li></ul></td>
        <td><div>Whether to add a public ip to the server</div></td></tr>
            <tr>
    <td>additional_disks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The list of additional disks for the server</div></td></tr>
            <tr>
    <td>alert_policy_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The alert policy to assign to the server. This is mutually exclusive with 'alert_policy_name'.</div></td></tr>
            <tr>
    <td>alert_policy_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The alert policy to assign to the server. This is mutually exclusive with 'alert_policy_id'.</div></td></tr>
            <tr>
    <td>alias<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The account alias to provision the servers under.</div></td></tr>
            <tr>
    <td>anti_affinity_policy_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The anti-affinity policy to assign to the server. This is mutually exclusive with 'anti_affinity_policy_name'.</div></td></tr>
            <tr>
    <td>anti_affinity_policy_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The anti-affinity policy to assign to the server. This is mutually exclusive with 'anti_affinity_policy_id'.</div></td></tr>
            <tr>
    <td>configuration_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Only required for bare metal servers. Specifies the identifier for the specific configuration type of bare metal server to deploy.</div></td></tr>
            <tr>
    <td>count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>The number of servers to build (mutually exclusive with exact_count)</div></td></tr>
            <tr>
    <td>count_group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Required when exact_count is specified.  The Server Group use to determine how many severs to deploy.</div></td></tr>
            <tr>
    <td>cpu<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>How many CPUs to provision on the server</div></td></tr>
            <tr>
    <td>cpu_autoscale_policy_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The autoscale policy to assign to the server.</div></td></tr>
            <tr>
    <td>custom_fields<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The list of custom fields to set on the server.</div></td></tr>
            <tr>
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The description to set for the server.</div></td></tr>
            <tr>
    <td>exact_count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Run in idempotent mode.  Will insure that this exact number of servers are running in the provided group, creating and deleting them to reach that count.  Requires count_group to be set.</div></td></tr>
            <tr>
    <td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Default Group</td>
        <td><ul></ul></td>
        <td><div>The Server Group to create servers under.</div></td></tr>
            <tr>
    <td>ip_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The IP Address for the server. One is assigned if not provided.</div></td></tr>
            <tr>
    <td>location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The Datacenter to create servers in.</div></td></tr>
            <tr>
    <td>managed_os<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Whether to create the server as 'Managed' or not.</div></td></tr>
            <tr>
    <td>memory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>Memory in GB.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A 1 to 6 character identifier to use for the server. This is required when state is 'present'</div></td></tr>
            <tr>
    <td>network_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The network UUID on which to create servers.</div></td></tr>
            <tr>
    <td>os_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>redHat6_64Bit</li><li>centOS6_64Bit</li><li>windows2012R2Standard_64Bit</li><li>ubuntu14_64Bit</li></ul></td>
        <td><div>Only required for bare metal servers. Specifies the OS to provision with the bare metal server.</div></td></tr>
            <tr>
    <td>packages<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The list of blue print packages to run on the server after its created.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Password for the administrator / root user</div></td></tr>
            <tr>
    <td>primary_dns<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Primary DNS used by the server.</div></td></tr>
            <tr>
    <td>public_ip_ports<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of ports to allow on the firewall to the servers public ip, if add_public_ip is set to True.</div></td></tr>
            <tr>
    <td>public_ip_protocol<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>TCP</td>
        <td><ul><li>TCP</li><li>UDP</li><li>ICMP</li></ul></td>
        <td><div>The protocol to use for the public ip if add_public_ip is set to True.</div></td></tr>
            <tr>
    <td>secondary_dns<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Secondary DNS used by the server.</div></td></tr>
            <tr>
    <td>server_ids<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Required for started, stopped, and absent states. A list of server Ids to insure are started, stopped, or absent.</div></td></tr>
            <tr>
    <td>source_server_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The password for the source server if a clone is specified.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>started</li><li>stopped</li></ul></td>
        <td><div>The state to insure that the provided resources are in.</div></td></tr>
            <tr>
    <td>storage_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>standard</td>
        <td><ul><li>standard</li><li>hyperscale</li></ul></td>
        <td><div>The type of storage to attach to the server.</div></td></tr>
            <tr>
    <td>template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The template to use for server creation.  Will search for a template if a partial string is provided. This is required when state is 'present'</div></td></tr>
            <tr>
    <td>ttl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The time to live for the server in seconds.  The server will be deleted when this time expires.</div></td></tr>
            <tr>
    <td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>standard</td>
        <td><ul><li>standard</li><li>hyperscale</li><li>bareMetal</li></ul></td>
        <td><div>The type of server to create.</div></td></tr>
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
    
    - name: Provision a single Ubuntu Server
      clc_server:
        name: test
        template: ubuntu-14-64
        count: 1
        group: 'Default Group'
        state: present
    
    - name: Ensure 'Default Group' has exactly 5 servers
      clc_server:
        name: test
        template: ubuntu-14-64
        exact_count: 5
        count_group: 'Default Group'
        group: 'Default Group'
    
    - name: Stop a Server
      clc_server:
        server_ids: ['UC1ACCT-TEST01']
        state: stopped
    
    - name: Start a Server
      clc_server:
        server_ids: ['UC1ACCT-TEST01']
        state: started
    
    - name: Delete a Server
      clc_server:
        server_ids: ['UC1ACCT-TEST01']
        state: absent

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
        <td> The list of server ids that are created </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> ['UC1TEST-SVR01', 'UC1TEST-SVR02'] </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> A flag indicating if any change was made or not </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> partially_created_server_ids </td>
        <td> The list of server ids that are partially created </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> ['UC1TEST-SVR01', 'UC1TEST-SVR02'] </td>
    </tr>
            <tr>
        <td> servers </td>
        <td> The list of server objects returned from CLC </td>
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

