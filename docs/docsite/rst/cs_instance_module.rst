.. _cs_instance:


cs_instance - Manages instances and virtual machines on Apache CloudStack based clouds.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Deploy, start, update, scale, restart, restore, stop and destroy instances.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * cs >= 0.6.10


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
                <tr><td>account<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Account the instance is related to.</div>        </td></tr>
                <tr><td>affinity_groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Affinity groups names to be applied to the new instance.</div></br>
    <div style="font-size: small;">aliases: affinity_group<div>        </td></tr>
                <tr><td>api_http_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>get</td>
        <td><ul><li>get</li><li>post</li></ul></td>
        <td><div>HTTP method used.</div>        </td></tr>
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>API key of the CloudStack API.</div>        </td></tr>
                <tr><td>api_region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cloudstack</td>
        <td></td>
        <td><div>Name of the ini section in the <code>cloustack.ini</code> file.</div>        </td></tr>
                <tr><td>api_secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Secret key of the CloudStack API.</div>        </td></tr>
                <tr><td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>HTTP timeout.</div>        </td></tr>
                <tr><td>api_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>URL of the CloudStack API e.g. https://cloud.example.com/client/api.</div>        </td></tr>
                <tr><td>cpu<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The number of CPUs to allocate to the instance, used with custom service offerings</div>        </td></tr>
                <tr><td>cpu_speed<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The clock speed/shares allocated to the instance, used with custom service offerings</div>        </td></tr>
                <tr><td>disk_offering<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the disk offering to be used.</div>        </td></tr>
                <tr><td>disk_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Disk size in GByte required if deploying instance from ISO.</div>        </td></tr>
                <tr><td>display_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Custom display name of the instances.</div><div>Display name will be set to <code>name</code> if not specified.</div><div>Either <code>name</code> or <code>display_name</code> is required.</div>        </td></tr>
                <tr><td>domain<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Domain the instance is related to.</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Force stop/start the instance if required to apply changes, otherwise a running instance will not be changed.</div>        </td></tr>
                <tr><td>group<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Group in where the new instance should be in.</div>        </td></tr>
                <tr><td>hypervisor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>KVM</li><li>VMware</li><li>BareMetal</li><li>XenServer</li><li>LXC</li><li>HyperV</li><li>UCS</li><li>OVM</li></ul></td>
        <td><div>Name the hypervisor to be used for creating the new instance.</div><div>Relevant when using <code>state=present</code>, but only considered if not set on ISO/template.</div><div>If not set or found on ISO/template, first found hypervisor will be used.</div>        </td></tr>
                <tr><td>ip6_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>IPv6 address for default instance's network.</div>        </td></tr>
                <tr><td>ip_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>IPv4 address for default instance's network during creation.</div>        </td></tr>
                <tr><td>ip_to_networks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of mappings in the form {'network': NetworkName, 'ip': 1.2.3.4}</div><div>Mutually exclusive with <code>networks</code> option.</div></br>
    <div style="font-size: small;">aliases: ip_to_network<div>        </td></tr>
                <tr><td>iso<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name or id of the ISO to be used for creating the new instance.</div><div>Required when using <code>state=present</code>.</div><div>Mutually exclusive with <code>template</code> option.</div>        </td></tr>
                <tr><td>keyboard<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>de</li><li>de-ch</li><li>es</li><li>fi</li><li>fr</li><li>fr-be</li><li>fr-ch</li><li>is</li><li>it</li><li>jp</li><li>nl-be</li><li>no</li><li>pt</li><li>uk</li><li>us</li></ul></td>
        <td><div>Keyboard device type for the instance.</div>        </td></tr>
                <tr><td>memory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The memory allocated to the instance, used with custom service offerings</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Host name of the instance. <code>name</code> can only contain ASCII letters.</div><div>Name will be generated (UUID) by CloudStack if not specified and can not be changed afterwards.</div><div>Either <code>name</code> or <code>display_name</code> is required.</div>        </td></tr>
                <tr><td>networks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of networks to use for the new instance.</div></br>
    <div style="font-size: small;">aliases: network<div>        </td></tr>
                <tr><td>poll_async<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Poll async jobs until job has finished.</div>        </td></tr>
                <tr><td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the project the instance to be deployed in.</div>        </td></tr>
                <tr><td>root_disk_size<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Root disk size in GByte required if deploying instance with KVM hypervisor and want resize the root disk size at startup (need CloudStack &gt;= 4.4, cloud-initramfs-growroot installed and enabled in the template)</div>        </td></tr>
                <tr><td>security_groups<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of security groups the instance to be applied to.</div></br>
    <div style="font-size: small;">aliases: security_group<div>        </td></tr>
                <tr><td>service_offering<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name or id of the service offering of the new instance.</div><div>If not set, first found service offering is used.</div>        </td></tr>
                <tr><td>ssh_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the SSH key to be deployed on the new instance.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>deployed</li><li>started</li><li>stopped</li><li>restarted</li><li>restored</li><li>destroyed</li><li>expunged</li><li>present</li><li>absent</li></ul></td>
        <td><div>State of the instance.</div>        </td></tr>
                <tr><td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of tags. Tags are a list of dictionaries having keys <code>key</code> and <code>value</code>.</div><div>If you want to delete all tags, set a empty list e.g. <code>tags: []</code>.</div></br>
    <div style="font-size: small;">aliases: tag<div>        </td></tr>
                <tr><td>template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name or id of the template to be used for creating the new instance.</div><div>Required when using <code>state=present</code>.</div><div>Mutually exclusive with <code>ISO</code> option.</div>        </td></tr>
                <tr><td>template_filter<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td>executable</td>
        <td><ul><li>featured</li><li>self</li><li>selfexecutable</li><li>sharedexecutable</li><li>executable</li><li>community</li></ul></td>
        <td><div>Name of the filter used to search for the template or iso.</div><div>Used for params <code>iso</code> or <code>template</code> on <code>state=present</code>.</div></br>
    <div style="font-size: small;">aliases: iso_filter<div>        </td></tr>
                <tr><td>user_data<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Optional data (ASCII) that can be sent to the instance upon a successful deployment.</div><div>The data will be automatically base64 encoded.</div><div>Consider switching to HTTP_POST by using <code>CLOUDSTACK_METHOD=post</code> to increase the HTTP_GET size limit of 2KB to 32 KB.</div>        </td></tr>
                <tr><td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the zone in which the instance should be deployed.</div><div>If not set, default zone is used.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a instance from an ISO
    # NOTE: Names of offerings and ISOs depending on the CloudStack configuration.
    - cs_instance:
        name: web-vm-1
        iso: Linux Debian 7 64-bit
        hypervisor: VMware
        project: Integration
        zone: ch-zrh-ix-01
        service_offering: 1cpu_1gb
        disk_offering: PerfPlus Storage
        disk_size: 20
        networks:
          - Server Integration
          - Sync Integration
          - Storage Integration
      delegate_to: localhost
    
    # For changing a running instance, use the 'force' parameter
    - cs_instance:
        name: web-vm-1
        display_name: web-vm-01.example.com
        iso: Linux Debian 7 64-bit
        service_offering: 2cpu_2gb
        force: yes
      delegate_to: localhost
    
    # Create or update a instance on Exoscale's public cloud using display_name.
    # Note: user_data can be used to kickstart the instance using cloud-init yaml config.
    - cs_instance:
        display_name: web-vm-1
        template: Linux Debian 7 64-bit
        service_offering: Tiny
        ssh_key: john@example.com
        tags:
          - key: admin
            value: john
          - key: foo
            value: bar
        user_data: |
            #cloud-config
            packages:
              - nginx
      delegate_to: localhost
    
    # Create an instance with multiple interfaces specifying the IP addresses
    - cs_instance:
        name: web-vm-1
        template: Linux Debian 7 64-bit
        service_offering: Tiny
        ip_to_networks:
          - network: NetworkA
            ip: 10.1.1.1
          - network: NetworkB
            ip: 192.0.2.1
      delegate_to: localhost
    
    # Ensure an instance is stopped
    - cs_instance:
        name: web-vm-1
        state: stopped
      delegate_to: localhost
    
    # Ensure an instance is running
    - cs_instance:
        name: web-vm-1
        state: started
      delegate_to: localhost
    
    # Remove an instance
    - cs_instance:
        name: web-vm-1
        state: absent
      delegate_to: localhost

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
        <td> domain </td>
        <td> Domain the instance is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example domain </td>
    </tr>
            <tr>
        <td> tags </td>
        <td> List of resource tags associated with the instance. </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> [ { "key": "foo", "value": "bar" } ] </td>
    </tr>
            <tr>
        <td> ssh_key </td>
        <td> Name of SSH key deployed to instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> key@work </td>
    </tr>
            <tr>
        <td> public_ip </td>
        <td> Public IP address with instance via static NAT rule. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 1.2.3.4 </td>
    </tr>
            <tr>
        <td> display_name </td>
        <td> Display name of the instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> web-01 </td>
    </tr>
            <tr>
        <td> service_offering </td>
        <td> Name of the service offering the instance has. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2cpu_2gb </td>
    </tr>
            <tr>
        <td> password </td>
        <td> The password of the instance if exists. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Ge2oe7Do </td>
    </tr>
            <tr>
        <td> id </td>
        <td> UUID of the instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 04589590-ac63-4ffc-93f5-b698b8ac38b6 </td>
    </tr>
            <tr>
        <td> security_groups </td>
        <td> Security groups the instance is in. </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> [ "default" ] </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name of the instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> web-01 </td>
    </tr>
            <tr>
        <td> project </td>
        <td> Name of project the instance is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Production </td>
    </tr>
            <tr>
        <td> account </td>
        <td> Account the instance is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example account </td>
    </tr>
            <tr>
        <td> group </td>
        <td> Group name of the instance is related. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> web </td>
    </tr>
            <tr>
        <td> password_enabled </td>
        <td> True if password setting is enabled. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> zone </td>
        <td> Name of zone the instance is in. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ch-gva-2 </td>
    </tr>
            <tr>
        <td> created </td>
        <td> Date of the instance was created. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2014-12-01T14:57:57+0100 </td>
    </tr>
            <tr>
        <td> hypervisor </td>
        <td> Hypervisor related to this instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> KVM </td>
    </tr>
            <tr>
        <td> default_ip </td>
        <td> Default IP address of the instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 10.23.37.42 </td>
    </tr>
            <tr>
        <td> instance_name </td>
        <td> Internal name of the instance (ROOT admin only). </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> i-44-3992-VM </td>
    </tr>
            <tr>
        <td> state </td>
        <td> State of the instance. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Running </td>
    </tr>
            <tr>
        <td> iso </td>
        <td> Name of ISO the instance was deployed with. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Debian-8-64bit </td>
    </tr>
            <tr>
        <td> template </td>
        <td> Name of template the instance was deployed with. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Debian-8-64bit </td>
    </tr>
            <tr>
        <td> affinity_groups </td>
        <td> Affinity groups the instance is in. </td>
        <td align=center> success </td>
        <td align=center> list </td>
        <td align=center> [ "webservers" ] </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Ansible uses the ``cs`` library's configuration method if credentials are not provided by the arguments ``api_url``, ``api_key``, ``api_secret``. Configuration is read from several locations, in the following order. - The ``CLOUDSTACK_ENDPOINT``, ``CLOUDSTACK_KEY``, ``CLOUDSTACK_SECRET`` and ``CLOUDSTACK_METHOD``. ``CLOUDSTACK_TIMEOUT`` environment variables. - A ``CLOUDSTACK_CONFIG`` environment variable pointing to an ``.ini`` file, - A ``cloudstack.ini`` file in the current working directory. - A ``.cloudstack.ini`` file in the users home directory. Optionally multiple credentials and endpoints can be specified using ini sections in ``cloudstack.ini``. Use the argument ``api_region`` to select the section name, default section is ``cloudstack``. See https://github.com/exoscale/cs for more information.
    - A detailed guide about cloudstack modules can be found on http://docs.ansible.com/ansible/guide_cloudstack.html
    - This module supports check mode.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
