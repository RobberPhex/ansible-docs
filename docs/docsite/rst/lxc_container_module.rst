.. _lxc_container:


lxc_container - Manage LXC Containers
+++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.8.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Management of LXC containers


Requirements (on host that executes module)
-------------------------------------------

  * lxc >= 1.0 # OS package
  * python >= 2.6 # OS Package
  * lxc-python2 >= 0.1 # PIP Package from https://github.com/lxc/python2-lxc


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
                <tr><td>archive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Create an archive of a container. This will create a tarball of the running container.</div>        </td></tr>
                <tr><td>archive_compression<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>gzip</td>
        <td><ul><li>gzip</li><li>bzip2</li><li>none</li></ul></td>
        <td><div>Type of compression to use when creating an archive of a running container.</div>        </td></tr>
                <tr><td>archive_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path the save the archived container. If the path does not exist the archive method will attempt to create it.</div>        </td></tr>
                <tr><td>backing_store<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>dir</td>
        <td><ul><li>dir</li><li>lvm</li><li>loop</li><li>btrfs</li><li>overlayfs</li><li>zfs</li></ul></td>
        <td><div>Backend storage type for the container.</div>        </td></tr>
                <tr><td>clone_name<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the new cloned server. This is only used when state is clone.</div>        </td></tr>
                <tr><td>clone_snapshot<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Create a snapshot a container when cloning. This is not supported by all container storage backends. Enabling this may fail if the backing store does not support snapshots.</div>        </td></tr>
                <tr><td>config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to the LXC configuration file.</div>        </td></tr>
                <tr><td>container_command<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Run a command within a container.</div>        </td></tr>
                <tr><td>container_config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>list of 'key=value' options to use when configuring a container.</div>        </td></tr>
                <tr><td>container_log<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Enable a container log for host actions to the container.</div>        </td></tr>
                <tr><td>container_log_level<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>INFO</td>
        <td><ul><li>INFO</li><li>ERROR</li><li>DEBUG</li></ul></td>
        <td><div>Set the log level for a container where *container_log* was set.</div>        </td></tr>
                <tr><td>directory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Place rootfs directory under DIR.</div>        </td></tr>
                <tr><td>fs_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5G</td>
        <td></td>
        <td><div>File system Size.</div>        </td></tr>
                <tr><td>fs_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ext4</td>
        <td></td>
        <td><div>Create fstype TYPE.</div>        </td></tr>
                <tr><td>lv_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>$CONTAINER_NAME</td>
        <td></td>
        <td><div>Name of the logical volume, defaults to the container name.</div>        </td></tr>
                <tr><td>lxc_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Place container under PATH</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of a container.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>started</td>
        <td><ul><li>started</li><li>stopped</li><li>restarted</li><li>absent</li><li>frozen</li></ul></td>
        <td><div>Define the state of a container. If you clone a container using `clone_name` the newly cloned container created in a stopped state. The running container will be stopped while the clone operation is happening and upon completion of the clone the original container state will be restored.</div>        </td></tr>
                <tr><td>template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ubuntu</td>
        <td></td>
        <td><div>Name of the template to use within an LXC create.</div>        </td></tr>
                <tr><td>template_options<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Template options when building the container.</div>        </td></tr>
                <tr><td>thinpool<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Use LVM thin pool called TP.</div>        </td></tr>
                <tr><td>vg_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>lxc</td>
        <td></td>
        <td><div>If Backend store is lvm, specify the name of the volume group.</div>        </td></tr>
                <tr><td>zfs_root<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Create zfs under given zfsroot.</div>        </td></tr>
        </table>
    </br>



Examples
--------

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
        backing_store: dir
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
    - name: Create a frozen lvm container
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
      debug:
        var: lvm_container_info
    
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
    
    - name: Start a container
      lxc_container:
        name: test-container-stopped
        state: started
    
    - name: Run a command in a container and then restart it
      lxc_container:
        name: test-container-started
        state: restarted
        container_command: |
          echo 'hello world.' | tee /opt/restarted
    
    - name: Run a complex command within a "running" container
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
    
    # Create a container using overlayfs, create an archive of it, create a
    # snapshot clone of the container and and finally leave the container
    # in a frozen state. The container archive will be compressed using gzip.
    - name: Create an overlayfs container archive and clone it
      lxc_container:
        name: test-container-overlayfs
        container_log: true
        template: ubuntu
        state: started
        backing_store: overlayfs
        template_options: --release trusty
        clone_snapshot: true
        clone_name: test-container-overlayfs-clone-snapshot
        archive: true
        archive_compression: gzip
      register: clone_container_info
    
    - name: debug info on container "test-container"
      debug:
        var: clone_container_info
    
    - name: Clone a container using snapshot
      lxc_container:
        name: test-container-overlayfs-clone-snapshot
        backing_store: overlayfs
        clone_name: test-container-overlayfs-clone-snapshot2
        clone_snapshot: true
    
    - name: Create a new container and clone it
      lxc_container:
        name: test-container-new-archive
        backing_store: dir
        clone_name: test-container-new-archive-clone
    
    - name: Archive and clone a container then destroy it
      lxc_container:
        name: test-container-new-archive
        state: absent
        clone_name: test-container-new-archive-destroyed-clone
        archive: true
        archive_compression: gzip
    
    - name: Start a cloned container.
      lxc_container:
        name: test-container-new-archive-destroyed-clone
        state: started
    
    - name: Destroy a container
      lxc_container:
        name: '{{ item }}'
        state: absent
      with_items:
        - test-container-stopped
        - test-container-started
        - test-container-frozen
        - test-container-lvm
        - test-container-config
        - test-container-overlayfs
        - test-container-overlayfs-clone
        - test-container-overlayfs-clone-snapshot
        - test-container-overlayfs-clone-snapshot2
        - test-container-new-archive
        - test-container-new-archive-clone
        - test-container-new-archive-destroyed-clone

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
        <td> lxc_container </td>
        <td> container information </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Containers must have a unique name. If you attempt to create a container with a name that already exists in the users namespace the module will simply return as "unchanged".
    - The "container_command" can be used with any state except "absent". If used with state "stopped" the container will be "started", the command executed, and then the container "stopped" again. Likewise if the state is "stopped" and the container does not exist it will be first created, "started", the command executed, and then "stopped". If you use a "|" in the variable you can use common script formatting within the variable iteself The "container_command" option will always execute as BASH. When using "container_command" a log file is created in the /tmp/ directory which contains both stdout and stderr of any command executed.
    - If "archive" is **true** the system will attempt to create a compressed tarball of the running container. The "archive" option supports LVM backed containers and will create a snapshot of the running container when creating the archive.
    - If your distro does not have a package for "python2-lxc", which is a requirement for this module, it can be installed from source at "https://github.com/lxc/python2-lxc" or installed via pip using the package name lxc-python2.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
