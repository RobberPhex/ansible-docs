.. _rax_scaling_group:


rax_scaling_group - Manipulate Rackspace Cloud Autoscale Groups
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.7

Manipulate Rackspace Cloud Autoscale Groups

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
    <td>api_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Rackspace API key (overrides <em>credentials</em>)</td>
    </tr>
            <tr>
    <td>config_drive</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Attach read-only configuration drive to server as label config-2 (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>cooldown</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The period of time, in seconds, that must pass before any scaling can occur after the previous scaling. Must be an integer between 0 and 86400 (24 hrs).</td>
    </tr>
            <tr>
    <td>credentials</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>File to find the Rackspace credentials in (ignored if <em>api_key</em> and <em>username</em> are provided)</td>
    </tr>
            <tr>
    <td>disk_config</td>
    <td>no</td>
    <td>auto</td>
        <td><ul><li>auto</li><li>manual</li></ul></td>
        <td>Disk partitioning strategy</td>
    </tr>
            <tr>
    <td>env</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Environment as configured in ~/.pyrax.cfg, see <a href='https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration'>https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration</a> (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>files</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Files to insert into the instance. Hash of <code>remotepath: localpath</code></td>
    </tr>
            <tr>
    <td>flavor</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>flavor to use for the instance</td>
    </tr>
            <tr>
    <td>image</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>image to use for the instance. Can be an <code>id</code>, <code>human_id</code> or <code>name</code></td>
    </tr>
            <tr>
    <td>key_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>key pair to use on the instance</td>
    </tr>
            <tr>
    <td>loadbalancers</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>List of load balancer <code>id</code> and <code>port</code> hashes</td>
    </tr>
            <tr>
    <td>max_entities</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The maximum number of entities that are allowed in the scaling group. Must be an integer between 0 and 1000.</td>
    </tr>
            <tr>
    <td>meta</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A hash of metadata to associate with the instance</td>
    </tr>
            <tr>
    <td>min_entities</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The minimum number of entities that are allowed in the scaling group. Must be an integer between 0 and 1000.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name to give the scaling group</td>
    </tr>
            <tr>
    <td>networks</td>
    <td>no</td>
    <td>['public', 'private']</td>
        <td><ul></ul></td>
        <td>The network to attach to the instances. If specified, you must include ALL networks including the public and private interfaces. Can be <code>id</code> or <code>label</code>.</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td>DFW</td>
        <td><ul></ul></td>
        <td>Region to create an instance in</td>
    </tr>
            <tr>
    <td>server_name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The base name for servers created by Autoscale</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Indicate desired state of the resource</td>
    </tr>
            <tr>
    <td>user_data</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Data to be uploaded to the servers config drive. This option implies <em>config_drive</em>. Can be a file path or a string (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>username</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Rackspace username (overrides <em>credentials</em>)</td>
    </tr>
            <tr>
    <td>verify_ssl</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Whether or not to require SSL validation of API endpoints (added in Ansible 1.5)</td>
    </tr>
        </table>


.. note:: Requires pyrax


Examples
--------

.. raw:: html

    <br/>


::

    ---
    - hosts: localhost
      gather_facts: false
      connection: local
      tasks:
        - rax_scaling_group:
            credentials: ~/.raxpub
            region: ORD
            cooldown: 300
            flavor: performance1-1
            image: bb02b1a3-bc77-4d17-ab5b-421d89850fca
            min_entities: 5
            max_entities: 10
            name: ASG Test
            server_name: asgtest
            loadbalancers:
                - id: 228385
                  port: 80
          register: asg

.. note:: The following environment variables can be used, ``RAX_USERNAME``, ``RAX_API_KEY``, ``RAX_CREDS_FILE``, ``RAX_CREDENTIALS``, ``RAX_REGION``.
.. note:: ``RAX_CREDENTIALS`` and ``RAX_CREDS_FILE`` points to a credentials file appropriate for pyrax. See https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#authenticating
.. note:: ``RAX_USERNAME`` and ``RAX_API_KEY`` obviate the use of a credentials file
.. note:: ``RAX_REGION`` defines a Rackspace Public Cloud region (DFW, ORD, LON, ...)


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

