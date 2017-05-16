.. _elasticache:


elasticache - Manage cache clusters in Amazon Elasticache.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage cache clusters in Amazon Elasticache.
Returns information about the specified cache cluster.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * boto


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
    <td>aws_access_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS access key. If not set then the value of the AWS_ACCESS_KEY_ID, AWS_ACCESS_KEY or EC2_ACCESS_KEY environment variable is used.</div></br>
        <div style="font-size: small;">aliases: ec2_access_key, access_key<div></td></tr>
            <tr>
    <td>aws_secret_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS secret key. If not set then the value of the AWS_SECRET_ACCESS_KEY, AWS_SECRET_KEY, or EC2_SECRET_KEY environment variable is used.</div></br>
        <div style="font-size: small;">aliases: ec2_secret_key, secret_key<div></td></tr>
            <tr>
    <td>cache_engine_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The version number of the cache engine</div></td></tr>
            <tr>
    <td>cache_parameter_group<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the cache parameter group to associate with this cache cluster. If this argument is omitted, the default cache parameter group for the specified engine will be used.</div></br>
        <div style="font-size: small;">aliases: parameter_group<div></td></tr>
            <tr>
    <td>cache_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The port number on which each of the cache nodes will accept connections</div></td></tr>
            <tr>
    <td>cache_security_groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A list of cache security group names to associate with this cache cluster. Must be an empty list if inside a vpc</div></td></tr>
            <tr>
    <td>cache_subnet_group<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The subnet group name to associate with. Only use if inside a vpc. Required if inside a vpc</div></td></tr>
            <tr>
    <td>ec2_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Url to use to connect to EC2 or your Eucalyptus cloud (by default the module will use EC2 endpoints).  Ignored for modules where region is required.  Must be specified for all other modules if region is not used. If not set then the value of the EC2_URL environment variable, if any, is used.</div></td></tr>
            <tr>
    <td>engine<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>memcached</td>
        <td><ul><li>redis</li><li>memcached</li></ul></td>
        <td><div>Name of the cache engine to be used.</div></td></tr>
            <tr>
    <td>hard_modify<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether to destroy and recreate an existing cache cluster if necessary in order to modify its state</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The cache cluster identifier</div></td></tr>
            <tr>
    <td>node_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cache.m1.small</td>
        <td><ul></ul></td>
        <td><div>The compute and memory capacity of the nodes in the cache cluster</div></td></tr>
            <tr>
    <td>num_nodes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The initial number of cache nodes that the cache cluster will have. Required when state=present.</div></td></tr>
            <tr>
    <td>profile<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>uses a boto profile. Only works with boto &gt;= 2.24.0</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The AWS region to use. If not specified then the value of the AWS_REGION or EC2_REGION environment variable, if any, is used. See <a href='http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region'>http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region</a></div></br>
        <div style="font-size: small;">aliases: aws_region, ec2_region<div></td></tr>
            <tr>
    <td>security_group_ids<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A list of vpc security group names to associate with this cache cluster. Only use if inside a vpc</div></td></tr>
            <tr>
    <td>security_token<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>AWS STS security token. If not set then the value of the AWS_SECURITY_TOKEN or EC2_SECURITY_TOKEN environment variable is used.</div></br>
        <div style="font-size: small;">aliases: access_token<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>rebooted</li></ul></td>
        <td><div><code>absent</code> or <code>present</code> are idempotent actions that will create or destroy a cache cluster as needed. <code>rebooted</code> will reboot the cluster, resulting in a momentary outage.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>When set to "no", SSL certificates will not be validated for boto versions &gt;= 2.6.0.</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Wait for cache cluster result before returning</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The EC2 Availability Zone in which the cache cluster will be created</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note: None of these examples set aws_access_key, aws_secret_key, or region.
    # It is assumed that their matching environment variables are set.
    
    # Basic example
    - elasticache:
        name: "test-please-delete"
        state: present
        engine: memcached
        cache_engine_version: 1.4.14
        node_type: cache.m1.small
        num_nodes: 1
        cache_port: 11211
        cache_security_groups:
          - default
        zone: us-east-1d
    
    
    # Ensure cache cluster is gone
    - elasticache:
        name: "test-please-delete"
        state: absent
    
    # Reboot cache cluster
    - elasticache:
        name: "test-please-delete"
        state: rebooted
    


Notes
-----

.. note:: If parameters are not set within the module, the following environment variables can be used in decreasing order of precedence ``AWS_URL`` or ``EC2_URL``, ``AWS_ACCESS_KEY_ID`` or ``AWS_ACCESS_KEY`` or ``EC2_ACCESS_KEY``, ``AWS_SECRET_ACCESS_KEY`` or ``AWS_SECRET_KEY`` or ``EC2_SECRET_KEY``, ``AWS_SECURITY_TOKEN`` or ``EC2_SECURITY_TOKEN``, ``AWS_REGION`` or ``EC2_REGION``
.. note:: Ansible uses the boto configuration file (typically ~/.boto) if no credentials are provided. See http://boto.readthedocs.org/en/latest/boto_config_tut.html
.. note:: ``AWS_REGION`` or ``EC2_REGION`` can be typically be used to specify the AWS region, when required, but this can also be configured in the boto config file


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

