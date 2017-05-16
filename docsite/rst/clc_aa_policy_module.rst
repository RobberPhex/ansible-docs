.. _clc_aa_policy:


clc_aa_policy - Create or Delete Anti Affinity Policies at CenturyLink Cloud.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

An Ansible module to Create or Delete Anti Affinity Policies at CenturyLink Cloud.


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
    <td>location<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Datacenter in which the policy lives/should live.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the Anti Affinity Policy.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether to create or delete the policy.</div></td></tr>
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

    # Note - You must set the CLC_V2_API_USERNAME And CLC_V2_API_PASSWD Environment variables before running these examples
    
    ---
    - name: Create AA Policy
      hosts: localhost
      gather_facts: False
      connection: local
      tasks:
        - name: Create an Anti Affinity Policy
          clc_aa_policy:
            name: 'Hammer Time'
            location: 'UK3'
            state: present
          register: policy
    
        - name: debug
          debug: var=policy
    
    ---
    - name: Delete AA Policy
      hosts: localhost
      gather_facts: False
      connection: local
      tasks:
        - name: Delete an Anti Affinity Policy
          clc_aa_policy:
            name: 'Hammer Time'
            location: 'UK3'
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
        <td> The anti affinity policy information </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> {'name': 'test_aa_policy', 'location': 'UC1', 'links': [{'href': '/v2/antiAffinityPolicies/wfad/1a28dd0988984d87b9cd61fa8da15424', 'verbs': ['GET', 'DELETE', 'PUT'], 'rel': 'self'}, {'href': '/v2/datacenters/wfad/UC1', 'id': 'uc1', 'rel': 'location', 'name': 'UC1 - US West (Santa Clara)'}], 'id': '1a28dd0988984d87b9cd61fa8da15424'} </td>
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

