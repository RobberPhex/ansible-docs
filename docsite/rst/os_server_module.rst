.. _os_server:


os_server - Create/Delete Compute Instances from OpenStack
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create or Remove compute instances from OpenStack.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * python >= 2.7
  * shade


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
    <td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>How long should the socket layer wait before timing out for API calls. If this is omitted, nothing will be passed to the requests library.</div></td></tr>
            <tr>
    <td>auth<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Dictionary containing auth information as needed by the cloud's auth plugin strategy. For the default <em>password</em> plugin, this would contain <em>auth_url</em>, <em>username</em>, <em>password</em>, <em>project_name</em> and any information about domains if the cloud supports them. For other plugins, this param will need to contain whatever parameters that auth plugin requires. This parameter is not needed if a named cloud is provided or OpenStack OS_* environment variables are present.</div></td></tr>
            <tr>
    <td>auth_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>password</td>
        <td><ul></ul></td>
        <td><div>Name of the auth plugin to use. If the cloud uses something other than password authentication, the name of the plugin should be indicated here and the contents of the <em>auth</em> parameter should be updated accordingly.</div></td></tr>
            <tr>
    <td>auto_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul></ul></td>
        <td><div>Ensure instance has public ip however the cloud wants to do that</div></br>
        <div style="font-size: small;">aliases: auto_floating_ip, public_ip<div></td></tr>
            <tr>
    <td>availability_zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the availability zone.</div></td></tr>
            <tr>
    <td>boot_from_volume<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Should the instance boot from a persistent volume created based on the image given. Mututally exclusive with boot_volume.</div></td></tr>
            <tr>
    <td>boot_volume<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Volume name or id to use as the volume to boot from. Implies boot_from_volume. Mutually exclusive with image and boot_from_volume.</div></br>
        <div style="font-size: small;">aliases: root_volume<div></td></tr>
            <tr>
    <td>cacert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A path to a CA Cert bundle that can be used as part of verifying SSL API requests.</div></td></tr>
            <tr>
    <td>cert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A path to a client certificate to use as part of the SSL transaction</div></td></tr>
            <tr>
    <td>cloud<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Named cloud to operate against. Provides default values for <em>auth</em> and <em>auth_type</em>. This parameter is not needed if <em>auth</em> is provided or if OpenStack OS_* environment variables are present.</div></td></tr>
            <tr>
    <td>config_drive<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul></ul></td>
        <td><div>Whether to boot the server with config drive enabled</div></td></tr>
            <tr>
    <td>delete_fip<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>When <em>state</em> is absent and this option is true, any floating IP associated with the instance will be deleted along with the instance.</div></td></tr>
            <tr>
    <td>endpoint_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>public</td>
        <td><ul><li>public</li><li>internal</li><li>admin</li></ul></td>
        <td><div>Endpoint URL type to fetch from the service catalog.</div></td></tr>
            <tr>
    <td>flavor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>The name or id of the flavor in which the new instance has to be created. Mutually exclusive with flavor_ram</div></td></tr>
            <tr>
    <td>flavor_include<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Text to use to filter flavor names, for the case, such as Rackspace, where there are multiple flavors that have the same ram count. flavor_include is a positive match filter - it must exist in the flavor name.</div></td></tr>
            <tr>
    <td>flavor_ram<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td><div>The minimum amount of ram in MB that the flavor in which the new instance has to be created must have. Mutually exclusive with flavor.</div></td></tr>
            <tr>
    <td>floating_ip_pools<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Name of floating IP pool from which to choose a floating IP</div></td></tr>
            <tr>
    <td>floating_ips<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>list of valid floating IPs that pre-exist to assign to this node</div></td></tr>
            <tr>
    <td>image<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name or id of the base image to boot.</div></td></tr>
            <tr>
    <td>image_exclude<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Text to use to filter image names, for the case, such as HP, where there are multiple image names matching the common identifying portions. image_exclude is a negative match filter - it is text that may not exist in the image name. Defaults to "(deprecated)"</div></td></tr>
            <tr>
    <td>key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A path to a client key to use as part of the SSL transaction</div></td></tr>
            <tr>
    <td>key_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The key pair name to be used when creating a instance</div></td></tr>
            <tr>
    <td>meta<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A list of key value pairs that should be provided as a metadata to the new instance or a string containing a list of key-value pairs. Eg:  meta: "key1=value1,key2=value2"</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name that has to be given to the instance</div></td></tr>
            <tr>
    <td>network<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Name or ID of a network to attach this instance to. A simpler version of the nics parameter, only one of network or nics should be supplied.</div></td></tr>
            <tr>
    <td>nics<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A list of networks to which the instance's interface should be attached. Networks may be referenced by net-id/net-name/port-id or port-name.</div><div>Also this accepts a string containing a list of (net/port)-(id/name) Eg: nics: "net-id=uuid-1,port-name=myport" Only one of network or nics should be supplied.</div></td></tr>
            <tr>
    <td>region_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the region.</div></td></tr>
            <tr>
    <td>reuse_ips<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>When <em>auto_ip</em> is true and this option is true, the <em>auto_ip</em> code will attempt to re-use unassigned floating ips in the project before creating a new one. It is important to note that it is impossible to safely do this concurrently, so if your use case involves concurrent server creation, it is highly recommended to set this to false and to delete the floating ip associated with a server when the server is deleted using <em>delete_fip</em>.</div></td></tr>
            <tr>
    <td>scheduler_hints<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Arbitrary key/value pairs to the scheduler for custom use</div></td></tr>
            <tr>
    <td>security_groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Names of the security groups to which the instance should be added. This may be a YAML list or a comma separated string.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Should the resource be present or absent.</div></td></tr>
            <tr>
    <td>terminate_volume<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If true, delete volume when deleting instance (if booted from volume)</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>180</td>
        <td><ul></ul></td>
        <td><div>How long should ansible wait for the requested resource.</div></td></tr>
            <tr>
    <td>userdata<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Opaque blob of data which is made available to the instance</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Whether or not SSL API requests should be verified.</div></br>
        <div style="font-size: small;">aliases: verify<div></td></tr>
            <tr>
    <td>volume_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The size of the volume to create in GB if booting from volume based on an image.</div></td></tr>
            <tr>
    <td>volumes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of preexisting volumes names or ids to attach to the instance</div></td></tr>
            <tr>
    <td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Should ansible wait until the requested resource is complete.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Creates a new instance and attaches to a network and passes metadata to
    # the instance
    - os_server:
           state: present
           auth:
             auth_url: https://region-b.geo-1.identity.hpcloudsvc.com:35357/v2.0/
             username: admin
             password: admin
             project_name: admin
           name: vm1
           image: 4f905f38-e52a-43d2-b6ec-754a13ffb529
           key_name: ansible_key
           timeout: 200
           flavor: 4
           nics:
             - net-id: 34605f38-e52a-25d2-b6ec-754a13ffb723
             - net-name: another_network
           meta:
             hostname: test1
             group: uge_master
    
    # Creates a new instance in HP Cloud AE1 region availability zone az2 and
    # automatically assigns a floating IP
    - name: launch a compute instance
      hosts: localhost
      tasks:
      - name: launch an instance
        os_server:
          state: present
          auth:
            auth_url: https://region-b.geo-1.identity.hpcloudsvc.com:35357/v2.0/
            username: username
            password: Equality7-2521
            project_name: username-project1
          name: vm1
          region_name: region-b.geo-1
          availability_zone: az2
          image: 9302692b-b787-4b52-a3a6-daebb79cb498
          key_name: test
          timeout: 200
          flavor: 101
          security_groups: default
          auto_ip: yes
    
    # Creates a new instance in named cloud mordred availability zone az2
    # and assigns a pre-known floating IP
    - name: launch a compute instance
      hosts: localhost
      tasks:
      - name: launch an instance
        os_server:
          state: present
          cloud: mordred
          name: vm1
          availability_zone: az2
          image: 9302692b-b787-4b52-a3a6-daebb79cb498
          key_name: test
          timeout: 200
          flavor: 101
          floating_ips:
            - 12.34.56.79
    
    # Creates a new instance with 4G of RAM on Ubuntu Trusty, ignoring
    # deprecated images
    - name: launch a compute instance
      hosts: localhost
      tasks:
      - name: launch an instance
        os_server:
          name: vm1
          state: present
          cloud: mordred
          region_name: region-b.geo-1
          image: Ubuntu Server 14.04
          image_exclude: deprecated
          flavor_ram: 4096
    
    # Creates a new instance with 4G of RAM on Ubuntu Trusty on a Performance node
    - name: launch a compute instance
      hosts: localhost
      tasks:
      - name: launch an instance
        os_server:
          name: vm1
          cloud: rax-dfw
          state: present
          image: Ubuntu 14.04 LTS (Trusty Tahr) (PVHVM)
          flavor_ram: 4096
          flavor_include: Performance
    
    # Creates a new instance and attaches to multiple network
    - name: launch a compute instance
      hosts: localhost
      tasks:
      - name: launch an instance with a string
        os_server:
          auth:
             auth_url: https://region-b.geo-1.identity.hpcloudsvc.com:35357/v2.0/
             username: admin
             password: admin
             project_name: admin
           name: vm1
           image: 4f905f38-e52a-43d2-b6ec-754a13ffb529
           key_name: ansible_key
           timeout: 200
           flavor: 4
           nics: "net-id=4cb08b20-62fe-11e5-9d70-feff819cdc9f,net-id=542f0430-62fe-11e5-9d70-feff819cdc9f..."
    
    # Creates a new instance and attaches to a network and passes metadata to
    # the instance
    - os_server:
           state: present
           auth:
             auth_url: https://region-b.geo-1.identity.hpcloudsvc.com:35357/v2.0/
             username: admin
             password: admin
             project_name: admin
           name: vm1
           image: 4f905f38-e52a-43d2-b6ec-754a13ffb529
           key_name: ansible_key
           timeout: 200
           flavor: 4
           nics:
             - net-id: 34605f38-e52a-25d2-b6ec-754a13ffb723
             - net-name: another_network
           meta: "hostname=test1,group=uge_master"
    
    # Creates a new instance and attaches to a specific network
    - os_server:
           state: present
           auth:
             auth_url: https://region-b.geo-1.identity.hpcloudsvc.com:35357/v2.0/
             username: admin
             password: admin
             project_name: admin
           name: vm1
           image: 4f905f38-e52a-43d2-b6ec-754a13ffb529
           key_name: ansible_key
           timeout: 200
           flavor: 4
           network: another_network
    
    # Creates a new instance with 4G of RAM on a 75G Ubuntu Trusty volume
    - name: launch a compute instance
      hosts: localhost
      tasks:
      - name: launch an instance
        os_server:
          name: vm1
          state: present
          cloud: mordred
          region_name: ams01
          image: Ubuntu Server 14.04
          flavor_ram: 4096
          boot_from_volume: True
          volume_size: 75
    
    # Creates a new instance with 2 volumes attached
    - name: launch a compute instance
      hosts: localhost
      tasks:
      - name: launch an instance
        os_server:
          name: vm1
          state: present
          cloud: mordred
          region_name: ams01
          image: Ubuntu Server 14.04
          flavor_ram: 4096
          volumes:
          - photos
          - music


Notes
-----

.. note:: The standard OpenStack environment variables, such as ``OS_USERNAME`` may be used instead of providing explicit values.
.. note:: Auth information is driven by os-client-config, which means that values can come from a yaml config file in /etc/ansible/openstack.yaml, /etc/openstack/clouds.yaml or ~/.config/openstack/clouds.yaml, then from standard environment variables, then finally by explicit parameters in plays. More information can be found at http://docs.openstack.org/developer/os-client-config


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

