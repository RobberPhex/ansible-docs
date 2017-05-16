.. _lxd_container:


lxd_container - Manage LXD Containers
+++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Management of LXD containers




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
    <td>architecture<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The archiecture for the container (e.g. "x86_64" or "i686"). See <a href='https://github.com/lxc/lxd/blob/master/doc/rest-api.md#post-1'>https://github.com/lxc/lxd/blob/master/doc/rest-api.md#post-1</a></div></td></tr>
            <tr>
    <td>cert_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>"{}/.config/lxc/client.crt" .format(os.environ["HOME"])</td>
        <td><ul></ul></td>
        <td><div>The client certificate file path.</div></td></tr>
            <tr>
    <td>config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The config for the container (e.g. {"limits.cpu": "2"}). See <a href='https://github.com/lxc/lxd/blob/master/doc/rest-api.md#post-1'>https://github.com/lxc/lxd/blob/master/doc/rest-api.md#post-1</a></div><div>If the container already exists and its "config" value in metadata obtained from GET /1.0/containers/&lt;name&gt; <a href='https://github.com/lxc/lxd/blob/master/doc/rest-api.md#10containersname'>https://github.com/lxc/lxd/blob/master/doc/rest-api.md#10containersname</a> are different, they this module tries to apply the configurations.</div><div>The key starts with 'volatile.' are ignored for this comparison.</div><div>Not all config values are supported to apply the existing container. Maybe you need to delete and recreate a container.</div></td></tr>
            <tr>
    <td>devices<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The devices for the container (e.g. { "rootfs": { "path": "/dev/kvm", "type": "unix-char" }). See <a href='https://github.com/lxc/lxd/blob/master/doc/rest-api.md#post-1'>https://github.com/lxc/lxd/blob/master/doc/rest-api.md#post-1</a></div></td></tr>
            <tr>
    <td>ephemeral<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether or not the container is ephemeral (e.g. true or false). See <a href='https://github.com/lxc/lxd/blob/master/doc/rest-api.md#post-1'>https://github.com/lxc/lxd/blob/master/doc/rest-api.md#post-1</a></div></td></tr>
            <tr>
    <td>force_stop<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If this is true, the <span class='module'>lxd_container</span> forces to stop the container when it stops or restarts the container.</div></td></tr>
            <tr>
    <td>key_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>"{}/.config/lxc/client.key" .format(os.environ["HOME"])</td>
        <td><ul></ul></td>
        <td><div>The client certificate key file path.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of a container.</div></td></tr>
            <tr>
    <td>source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The source for the container (e.g. { "type": "image", "mode": "pull", "server": "https://images.linuxcontainers.org", "protocol": "lxd", "alias": "ubuntu/xenial/amd64" }). See <a href='https://github.com/lxc/lxd/blob/master/doc/rest-api.md#post-1'>https://github.com/lxc/lxd/blob/master/doc/rest-api.md#post-1</a></div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>started</td>
        <td><ul><li>started</li><li>stopped</li><li>restarted</li><li>absent</li><li>frozen</li></ul></td>
        <td><div>Define the state of a container.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td><div>A timeout for changing the state of the container.</div><div>This is also used as a timeout for waiting until IPv4 addresses are set to the all network interfaces in the container after starting or restarting.</div></td></tr>
            <tr>
    <td>trust_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The client trusted password.</div><div>You need to set this password on the LXD server before running this module using the following command. lxc config set core.trust_password &lt;some random password&gt; See <a href='https://www.stgraber.org/2016/04/18/lxd-api-direct-interaction/'>https://www.stgraber.org/2016/04/18/lxd-api-direct-interaction/</a></div><div>If trust_password is set, this module send a request for authentication before sending any requests.</div></td></tr>
            <tr>
    <td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>unix:/var/lib/lxd/unix.socket</td>
        <td><ul></ul></td>
        <td><div>The unix domain socket path or the https URL for the LXD server.</div></td></tr>
            <tr>
    <td>wait_for_ipv4_addresses<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If this is true, the <span class='module'>lxd_container</span> waits until IPv4 addresses are set to the all network interfaces in the container after starting or restarting.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # An example for creating a Ubuntu container and install python
    - hosts: localhost
      connection: local
      tasks:
        - name: Create a started container
          lxd_container:
            name: mycontainer
            state: started
            source:
              type: image
              mode: pull
              server: https://images.linuxcontainers.org
              protocol: lxd
              alias: ubuntu/xenial/amd64
            profiles: ["default"]
            wait_for_ipv4_addresses: true
            timeout: 600
    
        - name: check python is installed in container
          delegate_to: mycontainer
          raw: dpkg -s python
          register: python_install_check
          failed_when: python_install_check.rc not in [0, 1]
          changed_when: false
    
        - name: install python in container
          delegate_to: mycontainer
          raw: apt-get install -y python
          when: python_install_check.rc == 1
    
    # An example for deleting a container
    - hosts: localhost
      connection: local
      tasks:
        - name: Delete a container
          lxd_container:
            name: mycontainer
            state: absent
    
    # An example for restarting a container
    - hosts: localhost
      connection: local
      tasks:
        - name: Restart a container
          lxd_container:
            name: mycontainer
            state: restarted
    
    # An example for restarting a container using https to connect to the LXD server
    - hosts: localhost
      connection: local
      tasks:
        - name: Restart a container
          lxd_container:
            url: https://127.0.0.1:8443
            # These cert_file and key_file values are equal to the default values.
            #cert_file: "{{ lookup('env', 'HOME') }}/.config/lxc/client.crt"
            #key_file: "{{ lookup('env', 'HOME') }}/.config/lxc/client.key"
            trust_password: mypassword
            name: mycontainer
            state: restarted
    
    # Note your container must be in the inventory for the below example.
    #
    # [containers]
    # mycontainer ansible_connection=lxd
    #
    - hosts:
        - mycontainer
      tasks:
        - name: copy /etc/hosts in the created container to localhost with name "mycontainer-hosts"
          fetch:
            src: /etc/hosts
            dest: /tmp/mycontainer-hosts
            flat: true

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
        <td> old_state </td>
        <td> The old state of the container </td>
        <td align=center> when state is started or restarted </td>
        <td align=center> string </td>
        <td align=center> stopped </td>
    </tr>
            <tr>
        <td> addresses </td>
        <td> Mapping from the network device name to a list of IPv4 addresses in the container </td>
        <td align=center> when state is started or restarted </td>
        <td align=center> object </td>
        <td align=center> {'eth0': ['10.155.92.191']} </td>
    </tr>
            <tr>
        <td> actions </td>
        <td> List of actions performed for the container. </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> ["create", "start"] </td>
    </tr>
            <tr>
        <td> logs </td>
        <td> The logs of requests and responses. </td>
        <td align=center> when ansible-playbook is invoked with -vvvv. </td>
        <td align=center> list </td>
        <td align=center> (too long to be placed here) </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Containers must have a unique name. If you attempt to create a container with a name that already existed in the users namespace the module will simply return as "unchanged".
.. note:: There are two ways to can run commands in containers, using the command module or using the ansible lxd connection plugin bundled in Ansible >= 2.1, the later requires python to be installed in the container which can be done with the command module.
.. note:: You can copy a file from the host to the container with the Ansible :ref:`copy <copy>` and :ref:`templater <templater>` module and the `lxd` connection plugin. See the example below.
.. note:: You can copy a file in the creatd container to the localhost with `command=lxc file pull container_name/dir/filename filename`. See the first example below.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

