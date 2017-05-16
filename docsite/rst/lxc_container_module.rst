.. _lxc_container:


lxc_container - Manage LXC Containers
+++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.8.0

Management of LXC containers

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
    <td>archive</td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td>Create an archive of a container. This will create a tarball of the running container.</td>
    </tr>
            <tr>
    <td>archive_compression</td>
    <td>no</td>
    <td>gzip</td>
        <td><ul><li>gzip</li><li>bzip2</li><li>none</li></ul></td>
        <td>Type of compression to use when creating an archive of a running container.</td>
    </tr>
            <tr>
    <td>archive_path</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Path the save the archived container. If the path does not exist the archive method will attempt to create it.</td>
    </tr>
            <tr>
    <td>backing_store</td>
    <td>no</td>
    <td>dir</td>
        <td><ul><li>dir</li><li>lvm</li><li>loop</li><li>btrfs</li></ul></td>
        <td>Backend storage type for the container.</td>
    </tr>
            <tr>
    <td>config</td>
    <td>no</td>
    <td>/etc/lxc/default.conf</td>
        <td><ul></ul></td>
        <td>Path to the LXC configuration file.</td>
    </tr>
            <tr>
    <td>container_command</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Run a command within a container.</td>
    </tr>
            <tr>
    <td>container_config</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>list of 'key=value' options to use when configuring a container.</td>
    </tr>
            <tr>
    <td>container_log</td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td>Enable a container log for host actions to the container.</td>
    </tr>
            <tr>
    <td>container_log_level</td>
    <td>no</td>
    <td>INFO</td>
        <td><ul><li>INFO</li><li>ERROR</li><li>DEBUG</li></ul></td>
        <td>Set the log level for a container where *container_log* was set.</td>
    </tr>
            <tr>
    <td>directory</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Place rootfs directory under DIR.</td>
    </tr>
            <tr>
    <td>fs_size</td>
    <td>no</td>
    <td>5G</td>
        <td><ul></ul></td>
        <td>File system Size.</td>
    </tr>
            <tr>
    <td>fs_type</td>
    <td>no</td>
    <td>ext4</td>
        <td><ul></ul></td>
        <td>Create fstype TYPE.</td>
    </tr>
            <tr>
    <td>lv_name</td>
    <td>no</td>
    <td>$CONTAINER_NAME</td>
        <td><ul></ul></td>
        <td>Name of the logical volume, defaults to the container name.</td>
    </tr>
            <tr>
    <td>lxc_path</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Place container under PATH</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of a container.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>started</td>
        <td><ul><li>started</li><li>stopped</li><li>restarted</li><li>absent</li><li>frozen</li></ul></td>
        <td>Start a container right after it's created.</td>
    </tr>
            <tr>
    <td>template</td>
    <td>no</td>
    <td>ubuntu</td>
        <td><ul></ul></td>
        <td>Name of the template to use within an LXC create.</td>
    </tr>
            <tr>
    <td>template_options</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Template options when building the container.</td>
    </tr>
            <tr>
    <td>thinpool</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Use LVM thin pool called TP.</td>
    </tr>
            <tr>
    <td>vg_name</td>
    <td>no</td>
    <td>lxc</td>
        <td><ul></ul></td>
        <td>If Backend store is lvm, specify the name of the volume group.</td>
    </tr>
            <tr>
    <td>zfs_root</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Create zfs under given zfsroot.</td>
    </tr>
        </table>


.. note:: Requires lxc >= 1.0


.. note:: Requires python2-lxc >= 0.1


Examples
--------

.. raw:: html

    <br/>


::

    - name: Create a started container
      lxc_container:
        name: test-container-started
        container_log: true
        template: ubuntu
        state: started
        template_options: --release trusty
    
    - name: Create a stopped container
      lxc_container:
        name: test-container-stopped
        container_log: true
        template: ubuntu
        state: stopped
        template_options: --release trusty
    
    - name: Create a frozen container
      lxc_container:
        name: test-container-frozen
        container_log: true
        template: ubuntu
        state: frozen
        template_options: --release trusty
        container_command: |
          echo 'hello world.' | tee /opt/started-frozen
    
    # Create filesystem container, configure it, and archive it, and start it.
    - name: Create filesystem container
      lxc_container:
        name: test-container-config
        container_log: true
        template: ubuntu
        state: started
        archive: true
        archive_compression: none
        container_config:
          - "lxc.aa_profile=unconfined"
          - "lxc.cgroup.devices.allow=a *:* rmw"
        template_options: --release trusty
    
    # Create an lvm container, run a complex command in it, add additional
    # configuration to it, create an archive of it, and finally leave the container
    # in a frozen state. The container archive will be compressed using bzip2
    - name: Create an lvm container
      lxc_container:
        name: test-container-lvm
        container_log: true
        template: ubuntu
        state: frozen
        backing_store: lvm
        template_options: --release trusty
        container_command: |
          apt-get update
          apt-get install -y vim lxc-dev
          echo 'hello world.' | tee /opt/started
          if [[ -f "/opt/started" ]]; then
              echo 'hello world.' | tee /opt/found-started
          fi
        container_config:
          - "lxc.aa_profile=unconfined"
          - "lxc.cgroup.devices.allow=a *:* rmw"
        archive: true
        archive_compression: bzip2
      register: lvm_container_info
    
    - name: Debug info on container "test-container-lvm"
      debug: var=lvm_container_info
    
    - name: Get information on a given container.
      lxc_container:
        name: test-container-config
      register: config_container_info
    
    - name: debug info on container "test-container"
      debug: var=config_container_info
    
    - name: Run a command in a container and ensure its in a "stopped" state.
      lxc_container:
        name: test-container-started
        state: stopped
        container_command: |
          echo 'hello world.' | tee /opt/stopped
    
    - name: Run a command in a container and ensure its it in a "frozen" state.
      lxc_container:
        name: test-container-stopped
        state: frozen
        container_command: |
          echo 'hello world.' | tee /opt/frozen
    
    - name: Start a container.
      lxc_container:
        name: test-container-stopped
        state: started
    
    - name: Run a command in a container and then restart it.
      lxc_container:
        name: test-container-started
        state: restarted
        container_command: |
          echo 'hello world.' | tee /opt/restarted
    
    - name: Run a complex command within a "running" container.
      lxc_container:
        name: test-container-started
        container_command: |
          apt-get update
          apt-get install -y curl wget vim apache2
          echo 'hello world.' | tee /opt/started
          if [[ -f "/opt/started" ]]; then
              echo 'hello world.' | tee /opt/found-started
          fi
    
    # Create an archive of an existing container, save the archive to a defined
    # path and then destroy it.
    - name: Archive container
      lxc_container:
        name: test-container-started
        state: absent
        archive: true
        archive_path: /opt/archives
    
    - name: Destroy a container.
      lxc_container:
        name: "{{ item }}"
        state: absent
      with_items:
        - test-container-stopped
        - test-container-started
        - test-container-frozen
        - test-container-lvm
        - test-container-config

.. note:: Containers must have a unique name. If you attempt to create a container with a name that already exists in the users namespace the module will simply return as "unchanged".
.. note:: The "container_command" can be used with any state except "absent". If used with state "stopped" the container will be "started", the command executed, and then the container "stopped" again. Likewise if the state is "stopped" and the container does not exist it will be first created, "started", the command executed, and then "stopped". If you use a "|" in the variable you can use common script formatting within the variable iteself The "container_command" option will always execute as BASH. When using "container_command" a log file is created in the /tmp/ directory which contains both stdout and stderr of any command executed.
.. note:: If "archive" is **true** the system will attempt to create a compressed tarball of the running container. The "archive" option supports LVM backed containers and will create a snapshot of the running container when creating the archive.
.. note:: If your distro does not have a package for "python2-lxc", which is a requirement for this module, it can be installed from source at "https://github.com/lxc/python2-lxc"


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

