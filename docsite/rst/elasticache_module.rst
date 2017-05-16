.. _elasticache:


elasticache - Manage cache clusters in Amazon Elasticache.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

Manage cache clusters in Amazon Elasticache.
Returns information about the specified cache cluster.

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
    <td>aws_access_key</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>AWS access key. If not set then the value of the AWS_ACCESS_KEY environment variable is used.</td>
    </tr>
            <tr>
    <td>aws_secret_key</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>AWS secret key. If not set then the value of the AWS_SECRET_KEY environment variable is used.</td>
    </tr>
            <tr>
    <td>cache_engine_version</td>
    <td>no</td>
    <td>1.4.14</td>
        <td><ul></ul></td>
        <td>The version number of the cache engine</td>
    </tr>
            <tr>
    <td>cache_port</td>
    <td>no</td>
    <td>11211</td>
        <td><ul></ul></td>
        <td>The port number on which each of the cache nodes will accept connections</td>
    </tr>
            <tr>
    <td>cache_security_groups</td>
    <td>no</td>
    <td>['default']</td>
        <td><ul></ul></td>
        <td>A list of cache security group names to associate with this cache cluster</td>
    </tr>
            <tr>
    <td>engine</td>
    <td>no</td>
    <td>memcached</td>
        <td><ul></ul></td>
        <td>Name of the cache engine to be used (memcached or redis)</td>
    </tr>
            <tr>
    <td>hard_modify</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Whether to destroy and recreate an existing cache cluster if necessary in order to modify its state</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The cache cluster identifier</td>
    </tr>
            <tr>
    <td>node_type</td>
    <td>no</td>
    <td>cache.m1.small</td>
        <td><ul></ul></td>
        <td>The compute and memory capacity of the nodes in the cache cluster</td>
    </tr>
            <tr>
    <td>num_nodes</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The initial number of cache nodes that the cache cluster will have</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The AWS region to use. If not specified then the value of the EC2_REGION environment variable, if any, is used.</td>
    </tr>
            <tr>
    <td>security_group_ids</td>
    <td>no</td>
    <td>['default']</td>
        <td><ul></ul></td>
        <td>A list of vpc security group names to associate with this cache cluster. Only use if inside a vpc (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li><li>rebooted</li></ul></td>
        <td><code>absent</code> or <code>present</code> are idempotent actions that will create or destroy a cache cluster as needed. <code>rebooted</code> will reboot the cluster, resulting in a momentary outage.</td>
    </tr>
            <tr>
    <td>wait</td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Wait for cache cluster result before returning</td>
    </tr>
            <tr>
    <td>zone</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>The EC2 Availability Zone in which the cache cluster will be created</td>
    </tr>
        </table>


.. note:: Requires boto


Examples
--------

.. raw:: html

    <br/>


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
    



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

