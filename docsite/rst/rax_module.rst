.. _rax:


rax - create / delete an instance in Rackspace Public Cloud
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

creates / deletes a Rackspace Public Cloud instance and optionally waits for it to be 'running'.


Requirements
------------

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
            <tr>
    <td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Rackspace API key (overrides <em>credentials</em>)</div></br>
        <div style="font-size: small;">aliases: password<div></td></tr>
            <tr>
    <td>auth_endpoint<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>https://identity.api.rackspacecloud.com/v2.0/</td>
        <td><ul></ul></td>
        <td><div>The URI of the authentication service</div></td></tr>
            <tr>
    <td>auto_increment<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether or not to increment a single number with the name of the created servers. Only applicable when used with the <em>group</em> attribute or meta key.</div></td></tr>
            <tr>
    <td>boot_from_volume<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether or not to boot the instance from a Cloud Block Storage volume. If <code>yes</code> and <em>image</em> is specified a new volume will be created at boot time. <em>boot_volume_size</em> is required with <em>image</em> to create a new volume at boot time.</div></td></tr>
            <tr>
    <td>boot_volume<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Cloud Block Storage ID or Name to use as the boot volume of the instance</div></td></tr>
            <tr>
    <td>boot_volume_size<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>100</td>
        <td><ul></ul></td>
        <td><div>Size of the volume to create in Gigabytes. This is only required with <em>image</em> and <em>boot_from_volume</em>.</div></td></tr>
            <tr>
    <td>boot_volume_terminate<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether the <em>boot_volume</em> or newly created volume from <em>image</em> will be terminated when the server is terminated</div></td></tr>
            <tr>
    <td>config_drive<br/><div style="font-size: small;"> (added in 1.7)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Attach read-only configuration drive to server as label config-2</div></td></tr>
            <tr>
    <td>count<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>number of instances to launch</div></td></tr>
            <tr>
    <td>count_offset<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>number count to start at</div></td></tr>
            <tr>
    <td>credentials<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>File to find the Rackspace credentials in (ignored if <em>api_key</em> and <em>username</em> are provided)</div></br>
        <div style="font-size: small;">aliases: creds_file<div></td></tr>
            <tr>
    <td>disk_config<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td>auto</td>
        <td><ul><li>auto</li><li>manual</li></ul></td>
        <td><div>Disk partitioning strategy</div></td></tr>
            <tr>
    <td>env<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Environment as configured in ~/.pyrax.cfg, see <a href='https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration'>https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration</a></div></td></tr>
            <tr>
    <td>exact_count<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Explicitly ensure an exact count of instances, used with state=active/present. If specified as <code>yes</code> and <em>count</em> is less than the servers matched, servers will be deleted to match the count. If the number of matched servers is fewer than specified in <em>count</em> additional servers will be added.</div></td></tr>
            <tr>
    <td>extra_client_args<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A hash of key/value pairs to be used when creating the cloudservers client. This is considered an advanced option, use it wisely and with caution.</div></td></tr>
            <tr>
    <td>extra_create_args<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A hash of key/value pairs to be used when creating a new server. This is considered an advanced option, use it wisely and with caution.</div></td></tr>
            <tr>
    <td>files<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Files to insert into the instance. remotefilename:localcontent</div></td></tr>
            <tr>
    <td>flavor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>flavor to use for the instance</div></td></tr>
            <tr>
    <td>group<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>host group to assign to server, is also used for idempotent operations to ensure a specific number of instances</div></td></tr>
            <tr>
    <td>identity_type<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>rackspace</td>
        <td><ul></ul></td>
        <td><div>Authentication machanism to use, such as rackspace or keystone</div></td></tr>
            <tr>
    <td>image<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>image to use for the instance. Can be an <code>id</code>, <code>human_id</code> or <code>name</code>. With <em>boot_from_volume</em>, a Cloud Block Storage volume will be created with this image</div></td></tr>
            <tr>
    <td>instance_ids<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>list of instance ids, currently only used when state='absent' to remove instances</div></td></tr>
            <tr>
    <td>key_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>key pair to use on the instance</div></br>
        <div style="font-size: small;">aliases: keypair<div></td></tr>
            <tr>
    <td>meta<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A hash of metadata to associate with the instance</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name to give the instance</div></td></tr>
            <tr>
    <td>networks<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td>[u'public', u'private']</td>
        <td><ul></ul></td>
        <td><div>The network to attach to the instances. If specified, you must include ALL networks including the public and private interfaces. Can be <code>id</code> or <code>label</code>.</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>DFW</td>
        <td><ul></ul></td>
        <td><div>Region to create an instance in</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the resource</div></td></tr>
            <tr>
    <td>tenant_id<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The tenant ID used for authentication</div></td></tr>
            <tr>
    <td>tenant_name<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The tenant name used for authentication</div></td></tr>
            <tr>
    <td>user_data<br/><div style="font-size: small;"> (added in 1.7)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Data to be uploaded to the servers config drive. This option implies <em>config_drive</em>. Can be a file path or a string</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Rackspace username (overrides <em>credentials</em>)</div></td></tr>
            <tr>
    <td>verify_ssl<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether or not to require SSL validation of API endpoints</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>wait for the instance to be in state 'running' before returning</div></td></tr>
            <tr>
    <td>wait_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td><div>how long before wait gives up, in seconds</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Build a Cloud Server
      gather_facts: False
      tasks:
        - name: Server build request
          local_action:
            module: rax
            credentials: ~/.raxpub
            name: rax-test1
            flavor: 5
            image: b11d9567-e412-4255-96b9-bd63ab23bcfe
            key_name: my_rackspace_key
            files:
              /root/test.txt: /home/localuser/test.txt
            wait: yes
            state: present
            networks:
              - private
              - public
          register: rax
    
    - name: Build an exact count of cloud servers with incremented names
      hosts: local
      gather_facts: False
      tasks:
        - name: Server build requests
          local_action:
            module: rax
            credentials: ~/.raxpub
            name: test%03d.example.org
            flavor: performance1-1
            image: ubuntu-1204-lts-precise-pangolin
            state: present
            count: 10
            count_offset: 10
            exact_count: yes
            group: test
            wait: yes
          register: rax


Notes
-----

.. note:: *exact_count* can be "destructive" if the number of running servers in the *group* is larger than that specified in *count*. In such a case, the *state* is effectively set to ``absent`` and the extra servers are deleted. In the case of deletion, the returned data structure will have ``action`` set to ``delete``, and the oldest servers in the group will be deleted.
.. note:: The following environment variables can be used, ``RAX_USERNAME``, ``RAX_API_KEY``, ``RAX_CREDS_FILE``, ``RAX_CREDENTIALS``, ``RAX_REGION``.
.. note:: ``RAX_CREDENTIALS`` and ``RAX_CREDS_FILE`` points to a credentials file appropriate for pyrax. See https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#authenticating
.. note:: ``RAX_USERNAME`` and ``RAX_API_KEY`` obviate the use of a credentials file
.. note:: ``RAX_REGION`` defines a Rackspace Public Cloud region (DFW, ORD, LON, ...)


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

