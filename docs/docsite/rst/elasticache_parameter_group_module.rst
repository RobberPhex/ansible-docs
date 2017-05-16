.. _elasticache_parameter_group:


elasticache_parameter_group - Manage cache security groups in Amazon Elasticache.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage cache security groups in Amazon Elasticache.
* Returns information about the specified cache cluster.




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
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A user-specified description for the cache parameter group.</div>        </td></tr>
                <tr><td>group_family<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>memcached1.4</li><li>redis2.6</li><li>redis2.8</li><li>redis3.2</li></ul></td>
        <td><div>The name of the cache parameter group family that the cache parameter group can be used with.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>A user-specified name for the cache parameter group.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>reset</li></ul></td>
        <td><div>Idempotent actions that will create/modify, destroy, or reset a cache parameter group as needed.</div>        </td></tr>
                <tr><td>values<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>A user-specified list of parameters to reset or modify for the cache parameter group.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note: None of these examples set aws_access_key, aws_secret_key, or region.
    # It is assumed that their matching environment variables are set.
    ---
    - hosts: localhost
      connection: local
      tasks:
        - name: 'Create a test parameter group'
          elasticache_parameter_group:
            name: 'test-param-group'
            group_family: 'redis3.2'
            description: 'This is a cache parameter group'
            state: 'present'
        - name: 'Modify a test parameter group'
          elasticache_parameter_group:
            name: 'test-param-group'
            values:
              - ['activerehashing', 'yes']
              - ['client-output-buffer-limit-normal-hard-limit', 4]
            state: 'present'
        - name: 'Reset all modifiable parameters for the test parameter group'
          elasticache_parameter_group:
            name: 'test-param-group'
            state: reset
        - name: 'Delete a test parameter group'
          elasticache_parameter_group:
            name: 'test-param-group'
            state: 'absent'

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
        <td> elasticache </td>
        <td> cache parameter group information and response metadata </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'cache_parameter_group': {'cache_parameter_group_family': 'redis3.2', 'description': 'initial description', 'cache_parameter_group_name': 'test-please-delete'}, 'response_metadata': {'retry_attempts': 0, 'http_status_code': 200, 'http_headers': {'date': 'Mon, 06 Feb 2017 22:14:08 GMT', 'x-amzn-requestid': '947291f9-ecb9-11e6-85bd-3baa4eca2cc1', 'content-length': '562', 'content-type': 'text/xml'}, 'request_id': '947291f9-ecb9-11e6-85bd-3baa4eca2cc1'}} </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> if the cache parameter group has changed </td>
        <td align=center> always </td>
        <td align=center> bool </td>
        <td align=center> {'changed': True} </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
