.. _clc_server_snapshot:


clc_server_snapshot - Create, Delete and Restore server snapshots in CenturyLink Cloud.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

An Ansible module to Create, Delete and Restore server snapshots in CenturyLink Cloud.


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
    <td>expiration_days<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>7</td>
        <td><ul></ul></td>
        <td><div>The number of days to keep the server snapshot before it expires.</div></td></tr>
            <tr>
    <td>server_ids<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The list of CLC server Ids.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>restore</li></ul></td>
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
    
    - name: Create server snapshot
      clc_server_snapshot:
        server_ids:
            - UC1TEST-SVR01
            - UC1TEST-SVR02
        expiration_days: 10
        wait: True
        state: present
    
    - name: Restore server snapshot
      clc_server_snapshot:
        server_ids:
            - UC1TEST-SVR01
            - UC1TEST-SVR02
        wait: True
        state: restore
    
    - name: Delete server snapshot
      clc_server_snapshot:
        server_ids:
            - UC1TEST-SVR01
            - UC1TEST-SVR02
        wait: True
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
        <td> The list of server ids that are changed </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> ['UC1TEST-SVR01', 'UC1TEST-SVR02'] </td>
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

