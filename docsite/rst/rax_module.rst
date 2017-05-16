.. _rax:


rax - create / delete an instance in Rackspace Public Cloud
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

creates / deletes a Rackspace Public Cloud instance and optionally waits for it to be 'running'.

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
    <td>auth_endpoint</td>
    <td>no</td>
    <td>https://identity.api.rackspacecloud.com/v2.0/</td>
        <td><ul></ul></td>
        <td>The URI of the authentication service (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>auto_increment</td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Whether or not to increment a single number with the name of the created servers. Only applicable when used with the <em>group</em> attribute or meta key. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>config_drive</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Attach read-only configuration drive to server as label config-2 (added in Ansible 1.7)</td>
    </tr>
            <tr>
    <td>count</td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td>number of instances to launch (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>count_offset</td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td>number count to start at (added in Ansible 1.4)</td>
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
        <td>Disk partitioning strategy (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>env</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Environment as configured in ~/.pyrax.cfg, see <a href='https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration'>https://github.com/rackspace/pyrax/blob/master/docs/getting_started.md#pyrax-configuration</a> (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>exact_count</td>
    <td>no</td>
    <td></td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Explicitly ensure an exact count of instances, used with state=active/present. If specified as <code>yes</code> and <em>count</em> is less than the servers matched, servers will be deleted to match the count. If the number of matched servers is fewer than specified in <em>count</em> additional servers will be added. (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>extra_client_args</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A hash of key/value pairs to be used when creating the cloudservers client. This is considered an advanced option, use it wisely and with caution. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>extra_create_args</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A hash of key/value pairs to be used when creating a new server. This is considered an advanced option, use it wisely and with caution. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>files</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Files to insert into the instance. remotefilename:localcontent</td>
    </tr>
            <tr>
    <td>flavor</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>flavor to use for the instance</td>
    </tr>
            <tr>
    <td>group</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>host group to assign to server, is also used for idempotent operations to ensure a specific number of instances (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>identity_type</td>
    <td>no</td>
    <td>rackspace</td>
        <td><ul></ul></td>
        <td>Authentication machanism to use, such as rackspace or keystone (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>image</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>image to use for the instance. Can be an <code>id</code>, <code>human_id</code> or <code>name</code></td>
    </tr>
            <tr>
    <td>instance_ids</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>list of instance ids, currently only used when state='absent' to remove instances (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>key_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>key pair to use on the instance</td>
    </tr>
            <tr>
    <td>meta</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A hash of metadata to associate with the instance</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name to give the instance</td>
    </tr>
            <tr>
    <td>networks</td>
    <td>no</td>
    <td>['public', 'private']</td>
        <td><ul></ul></td>
        <td>The network to attach to the instances. If specified, you must include ALL networks including the public and private interfaces. Can be <code>id</code> or <code>label</code>. (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>region</td>
    <td>no</td>
    <td>DFW</td>
        <td><ul></ul></td>
        <td>Region to create an instance in</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Indicate desired state of the resource</td>
    </tr>
            <tr>
    <td>tenant_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The tenant ID used for authentication (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>tenant_name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The tenant name used for authentication (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>user_data</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Data to be uploaded to the servers config drive. This option implies <em>config_drive</em>. Can be a file path or a string (added in Ansible 1.7)</td>
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
            <tr>
    <td>wait</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>wait for the instance to be in state 'running' before returning</td>
    </tr>
            <tr>
    <td>wait_timeout</td>
    <td>no</td>
    <td>300</td>
        <td><ul></ul></td>
        <td>how long before wait gives up, in seconds</td>
    </tr>
        </table>


.. note:: Requires pyrax


Examples
--------

.. raw:: html

    <br/>


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

.. note:: *exact_count* can be "destructive" if the number of running servers in the *group* is larger than that specified in *count*. In such a case, the *state* is effectively set to ``absent`` and the extra servers are deleted. In the case of deletion, the returned data structure will have ``action`` set to ``delete``, and the oldest servers in the group will be deleted.
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

