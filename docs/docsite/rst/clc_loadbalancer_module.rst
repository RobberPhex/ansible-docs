.. _clc_loadbalancer:


clc_loadbalancer - Create, Delete shared loadbalancers in CenturyLink Cloud.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* An Ansible module to Create, Delete shared loadbalancers in CenturyLink Cloud.


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
                <tr><td>alias<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The alias of your CLC Account</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A description for the loadbalancer</div>        </td></tr>
                <tr><td>location<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The location of the datacenter where the load balancer resides in</div>        </td></tr>
                <tr><td>method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>leastConnection</li><li>roundRobin</li></ul></td>
        <td><div>-The balancing method for the load balancer pool</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the loadbalancer</div>        </td></tr>
                <tr><td>nodes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A list of nodes that needs to be added to the load balancer pool</div>        </td></tr>
                <tr><td>persistence<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>standard</li><li>sticky</li></ul></td>
        <td><div>The persistence method for the load balancer</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul><li>80</li><li>443</li></ul></td>
        <td><div>Port to configure on the public-facing side of the load balancer pool</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>port_absent</li><li>nodes_present</li><li>nodes_absent</li></ul></td>
        <td><div>Whether to create or delete the load balancer pool</div>        </td></tr>
                <tr><td>status<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>enabled</td>
        <td><ul><li>enabled</li><li>disabled</li></ul></td>
        <td><div>The status of the loadbalancer</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note - You must set the CLC_V2_API_USERNAME And CLC_V2_API_PASSWD Environment variables before running these examples
    - name: Create Loadbalancer
      hosts: localhost
      connection: local
      tasks:
        - name: Actually Create things
          clc_loadbalancer:
            name: test
            description: test
            alias: TEST
            location: WA1
            port: 443
            nodes:
              - ipAddress: 10.11.22.123
                privatePort: 80
            state: present
    
    - name: Add node to an existing loadbalancer pool
      hosts: localhost
      connection: local
      tasks:
        - name: Actually Create things
          clc_loadbalancer:
            name: test
            description: test
            alias: TEST
            location: WA1
            port: 443
            nodes:
              - ipAddress: 10.11.22.234
                privatePort: 80
            state: nodes_present
    
    - name: Remove node from an existing loadbalancer pool
      hosts: localhost
      connection: local
      tasks:
        - name: Actually Create things
          clc_loadbalancer:
            name: test
            description: test
            alias: TEST
            location: WA1
            port: 443
            nodes:
              - ipAddress: 10.11.22.234
                privatePort: 80
            state: nodes_absent
    
    - name: Delete LoadbalancerPool
      hosts: localhost
      connection: local
      tasks:
        - name: Actually Delete things
          clc_loadbalancer:
            name: test
            description: test
            alias: TEST
            location: WA1
            port: 443
            nodes:
              - ipAddress: 10.11.22.123
                privatePort: 80
            state: port_absent
    
    - name: Delete Loadbalancer
      hosts: localhost
      connection: local
      tasks:
        - name: Actually Delete things
          clc_loadbalancer:
            name: test
            description: test
            alias: TEST
            location: WA1
            port: 443
            nodes:
              - ipAddress: 10.11.22.123
                privatePort: 80
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
        <td> loadbalancer </td>
        <td> The load balancer result object from CLC </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> {'status': 'enabled', 'name': 'test-lb', 'links': [{'href': '/v2/sharedLoadBalancers/wfad/wa1/ab5b18cb81e94ab9925b61d1ca043fb5', 'verbs': ['GET', 'PUT', 'DELETE'], 'rel': 'self'}, {'href': '/v2/sharedLoadBalancers/wfad/wa1/ab5b18cb81e94ab9925b61d1ca043fb5/pools', 'verbs': ['GET', 'POST'], 'rel': 'pools'}], 'pools': [], 'ipAddress': '66.150.174.197', 'id': 'ab5b18cb81e94ab9925b61d1ca043fb5', 'description': 'test-lb'} </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - To use this module, it is required to set the below environment variables which enables access to the Centurylink Cloud - CLC_V2_API_USERNAME, the account login id for the centurylink cloud - CLC_V2_API_PASSWORD, the account password for the centurylink cloud
    - Alternatively, the module accepts the API token and account alias. The API token can be generated using the CLC account login and password via the HTTP api call @ https://api.ctl.io/v2/authentication/login - CLC_V2_API_TOKEN, the API token generated from https://api.ctl.io/v2/authentication/login - CLC_ACCT_ALIAS, the account alias associated with the centurylink cloud
    - Users can set CLC_V2_API_URL to specify an endpoint for pointing to a different CLC environment.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
