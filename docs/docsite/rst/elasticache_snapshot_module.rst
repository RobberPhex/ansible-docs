.. _elasticache_snapshot:


elasticache_snapshot - Manage cache snapshots in Amazon Elasticache.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage cache snapshots in Amazon Elasticache.
* Returns information about the specified snapshot.




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
                <tr><td>bucket<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The s3 bucket to which the snapshot is exported</div>        </td></tr>
                <tr><td>cluster_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of an existing cache cluster in the replication group to make the snapshot.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the snapshot we want to create, copy, delete</div>        </td></tr>
                <tr><td>replication_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of the existing replication group to make the snapshot.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>copy</li></ul></td>
        <td><div>Actions that will create, destroy, or copy a snapshot.</div>        </td></tr>
                <tr><td>target<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of a snapshot copy</div>        </td></tr>
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
        - name: 'Create a snapshot'
          elasticache_snapshot:
            name: 'test-snapshot'
            state: 'present'
            cluster_id: '{{ cluster }}'
            replication_id: '{{ replication }}'

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
        <td> changed </td>
        <td> if a snapshot has been created, deleted, or copied </td>
        <td align=center> always </td>
        <td align=center> bool </td>
        <td align=center> {'changed': True} </td>
    </tr>
            <tr>
        <td> snapshot </td>
        <td> snapshot data </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'engine': 'redis', 'cache_cluster_create_time': datetime.datetime(2017, 2, 1, 17, 43, 58, 261000), 'cache_cluster_id': 'test-please-delete', 'snapshot_name': 'deletesnapshot', 'node_snapshots': {'cache_size': None, 'cache_node_id': 1, 'cache_node_create_time': datetime.datetime(2017, 2, 1, 17, 43, 58, 261000)}, 'preferred_availability_zone': 'us-east-1d', 'auto_minor_version_upgrade': True, 'cache_subnet_group_name': 'default', 'port': 11211, 'num_cache_nodes': 1, 'snapshot_window': '10:00-11:00', 'engine_version': '3.2.4', 'cache_parameter_group_name': 'default.redis3.2', 'snapshot_retention_limit': 0, 'preferred_maintenance_window': 'wed:03:00-wed:04:00', 'cache_node_type': 'cache.m1.small', 'vpc_id': 'vpc-c248fda4', 'snapshot_source': 'manual', 'snapshot_status': 'creating'} </td>
    </tr>
            <tr>
        <td> response_metadata </td>
        <td> response metadata about the snapshot </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center> {'retry_attempts': 0, 'http_status_code': 200, 'http_headers': {'date': 'Tue, 07 Feb 2017 16:43:04 GMT', 'x-amzn-requestid': '7f436dea-ed54-11e6-a04c-ab2372a1f14d', 'content-length': 1490, 'content-type': 'text/xml'}, 'request_id': '7f436dea-ed54-11e6-a04c-ab2372a1f14d'} </td>
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
