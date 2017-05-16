.. _rax_scaling_group:


rax_scaling_group - Manipulate Rackspace Cloud Autoscale Groups
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.7


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manipulate Rackspace Cloud Autoscale Groups


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * pyrax


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
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Rackspace API key, overrides <em>credentials</em>.</div></br>
    <div style="font-size: small;">aliases: password<div>        </td></tr>
                <tr><td>config_drive<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Attach read-only configuration drive to server as label config-2</div>        </td></tr>
                <tr><td>cooldown<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The period of time, in seconds, that must pass before any scaling can occur after the previous scaling. Must be an integer between 0 and 86400 (24 hrs).</div>        </td></tr>
                <tr><td>credentials<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>File to find the Rackspace credentials in. Ignored if <em>api_key</em> and <em>username</em> are provided.</div></br>
    <div style="font-size: small;">aliases: creds_file<div>        </td></tr>
                <tr><td>disk_config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>auto</td>
        <td><ul><li>auto</li><li>manual</li></ul></td>
        <td><div>Disk partitioning strategy</div>        </td></tr>
                <tr><td>env<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Environment as configured in <em>~/.pyrax.cfg</em>, see <a href='https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration'>https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration</a>.</div>        </td></tr>
                <tr><td>files<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Files to insert into the instance. Hash of <code>remotepath: localpath</code></div>        </td></tr>
                <tr><td>flavor<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>flavor to use for the instance</div>        </td></tr>
                <tr><td>image<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>image to use for the instance. Can be an <code>id</code>, <code>human_id</code> or <code>name</code></div>        </td></tr>
                <tr><td>key_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>key pair to use on the instance</div>        </td></tr>
                <tr><td>loadbalancers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of load balancer <code>id</code> and <code>port</code> hashes</div>        </td></tr>
                <tr><td>max_entities<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The maximum number of entities that are allowed in the scaling group. Must be an integer between 0 and 1000.</div>        </td></tr>
                <tr><td>meta<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A hash of metadata to associate with the instance</div>        </td></tr>
                <tr><td>min_entities<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The minimum number of entities that are allowed in the scaling group. Must be an integer between 0 and 1000.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name to give the scaling group</div>        </td></tr>
                <tr><td>networks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>[u'public', u'private']</td>
        <td></td>
        <td><div>The network to attach to the instances. If specified, you must include ALL networks including the public and private interfaces. Can be <code>id</code> or <code>label</code>.</div>        </td></tr>
                <tr><td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>DFW</td>
        <td></td>
        <td><div>Region to create an instance in.</div>        </td></tr>
                <tr><td>server_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The base name for servers created by Autoscale</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource</div>        </td></tr>
                <tr><td>user_data<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Data to be uploaded to the servers config drive. This option implies <em>config_drive</em>. Can be a file path or a string</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Rackspace username, overrides <em>credentials</em>.</div>        </td></tr>
                <tr><td>verify_ssl<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether or not to require SSL validation of API endpoints.</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>wait for the scaling group to finish provisioning the minimum amount of servers</div>        </td></tr>
                <tr><td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td></td>
        <td><div>how long before wait gives up, in seconds</div>        </td></tr>
        </table>
    </br>



Examples
--------

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


Notes
-----

.. note::
    - The following environment variables can be used, ``RAX_USERNAME``, ``RAX_API_KEY``, ``RAX_CREDS_FILE``, ``RAX_CREDENTIALS``, ``RAX_REGION``.
    - ``RAX_CREDENTIALS`` and ``RAX_CREDS_FILE`` points to a credentials file appropriate for pyrax. See https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#authenticating
    - ``RAX_USERNAME`` and ``RAX_API_KEY`` obviate the use of a credentials file
    - ``RAX_REGION`` defines a Rackspace Public Cloud region (DFW, ORD, LON, ...)



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
