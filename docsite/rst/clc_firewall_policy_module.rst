.. _clc_firewall_policy:


clc_firewall_policy - Create/delete/update firewall policies
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create or delete or update firewall polices on Centurylink Cloud


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
    <td>destination<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The list of destination addresses for traffic on the terminating firewall. This is required when state is 'present'</div></td></tr>
            <tr>
    <td>destination_account_alias<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>CLC alias for the destination account</div></td></tr>
            <tr>
    <td>enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Whether the firewall policy is enabled or disabled</div></td></tr>
            <tr>
    <td>firewall_policy_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Id of the firewall policy. This is required to update or delete an existing firewall policy</div></td></tr>
            <tr>
    <td>location<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Target datacenter for the firewall policy</div></td></tr>
            <tr>
    <td>ports<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>any</li><li>icmp</li><li>TCP/123</li><li>UDP/123</li><li>TCP/123-456</li><li>UDP/123-456</li></ul></td>
        <td><div>The list of ports associated with the policy. TCP and UDP can take in single ports or port ranges.</div></td></tr>
            <tr>
    <td>source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The list  of source addresses for traffic on the originating firewall. This is required when state is 'present"</div></td></tr>
            <tr>
    <td>source_account_alias<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>CLC alias for the source account</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether to create or delete the firewall policy</div></td></tr>
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

    ---
    - name: Create Firewall Policy
      hosts: localhost
      gather_facts: False
      connection: local
      tasks:
        - name: Create / Verify an Firewall Policy at CenturyLink Cloud
          clc_firewall:
            source_account_alias: WFAD
            location: VA1
            state: present
            source: 10.128.216.0/24
            destination: 10.128.216.0/24
            ports: Any
            destination_account_alias: WFAD
    
    ---
    - name: Delete Firewall Policy
      hosts: localhost
      gather_facts: False
      connection: local
      tasks:
        - name: Delete an Firewall Policy at CenturyLink Cloud
          clc_firewall:
            source_account_alias: WFAD
            location: VA1
            state: absent
            firewall_policy_id: 'c62105233d7a4231bd2e91b9c791e43e1'

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
        <td> firewall_policy </td>
        <td> The fire wall policy information </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> {'status': 'active', 'links': [{'href': 'http://api.ctl.io/v2-experimental/firewallPolicies/wfad/uc1/fc36f1bfd47242e488a9c44346438c05', 'verbs': ['GET', 'PUT', 'DELETE'], 'rel': 'self'}], 'destination': ['10.1.1.0/24', '10.2.2.0/24'], 'enabled': True, 'ports': ['any'], 'source': ['10.1.1.0/24', '10.2.2.0/24'], 'destinationAccount': 'wfad', 'id': 'fc36f1bfd47242e488a9c44346438c05'} </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> A flag indicating if any change was made or not </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> firewall_policy_id </td>
        <td> The fire wall policy id </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> fc36f1bfd47242e488a9c44346438c05 </td>
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

