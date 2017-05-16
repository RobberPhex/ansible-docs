.. _cs_template:


cs_template - Manages templates on Apache CloudStack based clouds.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Register a template from URL, create a template from a ROOT volume of a stopped VM or its snapshot, extract and delete templates.


Requirements
------------

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
            <tr>
    <td>api_http_method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>get</td>
        <td><ul><li>get</li><li>post</li></ul></td>
        <td><div>HTTP method used.</div></td></tr>
            <tr>
    <td>api_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>API key of the CloudStack API.</div></td></tr>
            <tr>
    <td>api_region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>cloudstack</td>
        <td><ul></ul></td>
        <td><div>Name of the ini section in the <code>cloustack.ini</code> file.</div></td></tr>
            <tr>
    <td>api_secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Secret key of the CloudStack API.</div></td></tr>
            <tr>
    <td>api_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>HTTP timeout.</div></td></tr>
            <tr>
    <td>api_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>URL of the CloudStack API e.g. https://cloud.example.com/client/api.</div></td></tr>
            <tr>
    <td>bits<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>64</td>
        <td><ul></ul></td>
        <td><div>32 or 64 bits support.</div></td></tr>
            <tr>
    <td>checksum<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The MD5 checksum value of this template.</div><div>If set, we search by checksum instead of name.</div></td></tr>
            <tr>
    <td>cross_zones<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether the template should be syned across zones.</div><div>Only used if <code>state</code> is present.</div></td></tr>
            <tr>
    <td>details<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Template details in key/value pairs.</div></td></tr>
            <tr>
    <td>display_text<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Display text of the template.</div></td></tr>
            <tr>
    <td>format<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>QCOW2</li><li>RAW</li><li>VHD</li><li>OVA</li></ul></td>
        <td><div>The format for the template.</div><div>Relevant when using <code>state=present</code>.</div></td></tr>
            <tr>
    <td>hypervisor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>none</td>
        <td><ul><li>KVM</li><li>VMware</li><li>BareMetal</li><li>XenServer</li><li>LXC</li><li>HyperV</li><li>UCS</li><li>OVM</li></ul></td>
        <td><div>Name the hypervisor to be used for creating the new template.</div><div>Relevant when using <code>state=present</code>.</div></td></tr>
            <tr>
    <td>is_dynamically_scalable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Register the template having XS/VMWare tools installed in order to support dynamic scaling of VM CPU/memory.</div><div>Only used if <code>state</code> is present.</div></td></tr>
            <tr>
    <td>is_extractable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>True if the template or its derivatives are extractable.</div></td></tr>
            <tr>
    <td>is_featured<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Register the template to be featured.</div><div>Only used if <code>state</code> is present.</div></td></tr>
            <tr>
    <td>is_public<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Register the template to be publicly available to all users.</div><div>Only used if <code>state</code> is present.</div></td></tr>
            <tr>
    <td>is_ready<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>This flag is used for searching existing templates.</div><div>If set to <code>true</code>, it will only list template ready for deployment e.g. successfully downloaded and installed.</div><div>Recommended to set it to <code>false</code>.</div></td></tr>
            <tr>
    <td>is_routing<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>True if the template type is routing i.e., if template is used to deploy router.</div><div>Only considered if <code>url</code> is used.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the template.</div></td></tr>
            <tr>
    <td>os_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>OS type that best represents the OS of this template.</div></td></tr>
            <tr>
    <td>password_enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>True if the template supports the password reset feature.</div></td></tr>
            <tr>
    <td>poll_async<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Poll async jobs until job has finished.</div></td></tr>
            <tr>
    <td>project<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the project the template to be registered in.</div></td></tr>
            <tr>
    <td>requires_hvm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>true if this template requires HVM.</div></td></tr>
            <tr>
    <td>snapshot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the snapshot, created from the VM ROOT volume, the template will be created from.</div><div><code>vm</code> is required together with this argument.</div></td></tr>
            <tr>
    <td>sshkey_enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>True if the template supports the sshkey upload feature.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>extacted</li></ul></td>
        <td><div>State of the template.</div></td></tr>
            <tr>
    <td>template_filter<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>self</td>
        <td><ul><li>featured</li><li>self</li><li>selfexecutable</li><li>sharedexecutable</li><li>executable</li><li>community</li></ul></td>
        <td><div>Name of the filter used to search for the template.</div></td></tr>
            <tr>
    <td>template_tag<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the tag for this template.</div></td></tr>
            <tr>
    <td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>URL of where the template is hosted on <code>state=present</code>.</div><div>URL to which the template would be extracted on <code>state=extracted</code>.</div><div>Mutually exclusive with <code>vm</code>.</div></td></tr>
            <tr>
    <td>vm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>VM name the template will be created from its volume or alternatively from a snapshot.</div><div>VM must be in stopped state if created from its volume.</div><div>Mutually exclusive with <code>url</code>.</div></td></tr>
            <tr>
    <td>zone<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the zone you wish the template to be registered or deleted from.</div><div>If not specified, first found zone will be used.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Register a systemvm template
    - local_action:
        module: cs_template
        name: systemvm-vmware-4.5
        url: "http://packages.shapeblue.com/systemvmtemplate/4.5/systemvm64template-4.5-vmware.ova"
        hypervisor: VMware
        format: OVA
        cross_zones: yes
        os_type: Debian GNU/Linux 7(64-bit)
    
    # Create a template from a stopped virtual machine's volume
    - local_action:
        module: cs_template
        name: debian-base-template
        vm: debian-base-vm
        os_type: Debian GNU/Linux 7(64-bit)
        zone: tokio-ix
        password_enabled: yes
        is_public: yes
    
    # Create a template from a virtual machine's root volume snapshot
    - local_action:
        module: cs_template
        name: debian-base-template
        vm: debian-base-vm
        snapshot: ROOT-233_2015061509114
        os_type: Debian GNU/Linux 7(64-bit)
        zone: tokio-ix
        password_enabled: yes
        is_public: yes
    
    # Remove a template
    - local_action:
        module: cs_template
        name: systemvm-4.2
        state: absent

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
        <td> status </td>
        <td> Status of the template. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Download Complete </td>
    </tr>
            <tr>
        <td> is_featured </td>
        <td> True if the template is featured. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> format </td>
        <td> Format of the template. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> OVA </td>
    </tr>
            <tr>
        <td> domain </td>
        <td> Domain the template is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example domain </td>
    </tr>
            <tr>
        <td> is_extractable </td>
        <td> True if the template is extractable. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> is_public </td>
        <td> True if the template is public. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> id </td>
        <td> UUID of the template. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> a6f7a5fc-43f8-11e5-a151-feff819cdc9f </td>
    </tr>
            <tr>
        <td> tags </td>
        <td> List of resource tags associated with the template. </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> [ { "key": "foo", "value": "bar" } ] </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name of the template. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Debian 7 64-bit </td>
    </tr>
            <tr>
        <td> display_text </td>
        <td> Display text of the template. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Debian 7.7 64-bit minimal 2015-03-19 </td>
    </tr>
            <tr>
        <td> project </td>
        <td> Name of project the template is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Production </td>
    </tr>
            <tr>
        <td> account </td>
        <td> Account the template is related to. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example account </td>
    </tr>
            <tr>
        <td> password_enabled </td>
        <td> True if the reset password feature is enabled, false otherwise. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> zone </td>
        <td> Name of zone the template is registered in. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> zuerich </td>
    </tr>
            <tr>
        <td> created </td>
        <td> Date of registering. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2015-03-29T14:57:06+0200 </td>
    </tr>
            <tr>
        <td> url </td>
        <td> Url to which the template is extracted to </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> http://1.2.3.4/userdata/eb307f13-4aca-45e8-b157-a414a14e6b04.ova </td>
    </tr>
            <tr>
        <td> hypervisor </td>
        <td> Hypervisor related to this template. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> VMware </td>
    </tr>
            <tr>
        <td> sshkey_enabled </td>
        <td> true if template is sshkey enabled, false otherwise. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> cross_zones </td>
        <td> true if the template is managed across all zones, false otherwise. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> False </td>
    </tr>
            <tr>
        <td> template_type </td>
        <td> Type of the template. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> USER </td>
    </tr>
            <tr>
        <td> state </td>
        <td> State of the extracted template </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> DOWNLOAD_URL_CREATED </td>
    </tr>
            <tr>
        <td> is_ready </td>
        <td> True if the template is ready to be deployed from. </td>
        <td align=center> success </td>
        <td align=center> boolean </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> mode </td>
        <td> Mode of extraction </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> http_download </td>
    </tr>
            <tr>
        <td> checksum </td>
        <td> MD5 checksum of the template. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 0b31bccccb048d20b551f70830bb7ad0 </td>
    </tr>
            <tr>
        <td> os_type </td>
        <td> Typo of the OS. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> CentOS 6.5 (64-bit) </td>
    </tr>
            <tr>
        <td> template_tag </td>
        <td> Template tag related to this template. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> special </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note:: Ansible uses the ``cs`` library's configuration method if credentials are not provided by the arguments ``api_url``, ``api_key``, ``api_secret``. Configuration is read from several locations, in the following order. - The ``CLOUDSTACK_ENDPOINT``, ``CLOUDSTACK_KEY``, ``CLOUDSTACK_SECRET`` and ``CLOUDSTACK_METHOD``. ``CLOUDSTACK_TIMEOUT`` environment variables. - A ``CLOUDSTACK_CONFIG`` environment variable pointing to an ``.ini`` file, - A ``cloudstack.ini`` file in the current working directory. - A ``.cloudstack.ini`` file in the users home directory. Optionally multiple credentials and endpoints can be specified using ini sections in ``cloudstack.ini``. Use the argument ``api_region`` to select the section name, default section is ``cloudstack``. See https://github.com/exoscale/cs for more information.
.. note:: This module supports check mode.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

