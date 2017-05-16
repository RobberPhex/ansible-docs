.. _ovirt_hosts:


ovirt_hosts - Module to manage hosts in oVirt
+++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Module to manage hosts in oVirt


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.7
  * ovirt-engine-sdk-python >= 4.0.0


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
                <tr><td>address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Host address. It can be either FQDN (preferred) or IP address.</div>        </td></tr>
                <tr><td>auth<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Dictionary with values needed to create HTTP/HTTPS connection to oVirt:</div><div><code>username</code>[<em>required</em>] - The name of the user, something like <em>admin@internal</em>. Default value is set by <em>OVIRT_USERNAME</em> environment variable.</div><div><code>password</code>[<em>required</em>] - The password of the user. Default value is set by <em>OVIRT_PASSWORD</em> environment variable.</div><div><code>url</code>[<em>required</em>] - A string containing the base URL of the server, usually something like `<em>https://server.example.com/ovirt-engine/api</em>`. Default value is set by <em>OVIRT_URL</em> environment variable.</div><div><code>token</code> - Token to be used instead of login with username/password. Default value is set by <em>OVIRT_TOKEN</em> environment variable.</div><div><code>insecure</code> - A boolean flag that indicates if the server TLS certificate and host name should be checked.</div><div><code>ca_file</code> - A PEM file containing the trusted CA certificates. The certificate presented by the server will be verified using these CA certificates. If `<code>ca_file</code>` parameter is not set, system wide CA certificate store is used. Default value is set by <em>OVIRT_CAFILE</em> environment variable.</div><div><code>kerberos</code> - A boolean flag indicating if Kerberos authentication should be used instead of the default basic authentication.</div>        </td></tr>
                <tr><td>cluster<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the cluster, where host should be created.</div>        </td></tr>
                <tr><td>comment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Description of the host.</div>        </td></tr>
                <tr><td>fetch_nested<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> the module will fetch additional data from the API.</div><div>It will fetch IDs of the VMs disks, snapshots, etc. User can configure to fetch other attributes of the nested entities by specifying <code>nested_attributes</code>.</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If True host will be forcibly moved to desired state.</div>        </td></tr>
                <tr><td>hosted_engine<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>deploy</em> it means this host should deploy also hosted engine components.</div><div>If <em>undeploy</em> it means this host should un-deploy hosted engine components and this host will not function as part of the High Availability cluster.</div>        </td></tr>
                <tr><td>kdump_integration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>enabled</td>
        <td><ul><li>enabled</li><li>disabled</li></ul></td>
        <td><div>Specify if host will have enabled Kdump integration.</div>        </td></tr>
                <tr><td>kernel_params<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of kernel boot parameters.</div><div>Following are most common kernel parameters used for host:</div><div>Hostdev Passthrough &amp; SR-IOV: intel_iommu=on</div><div>Nested Virtualization: kvm-intel.nested=1</div><div>Unsafe Interrupts: vfio_iommu_type1.allow_unsafe_interrupts=1</div><div>PCI Reallocation: pci=realloc</div><div><code>Note:</code></div><div>Modifying kernel boot parameters settings can lead to a host boot failure. Please consult the product documentation before doing any changes.</div><div>Kernel boot parameters changes require host deploy and restart. The host needs to be <em>reinstalled</em> suceesfully and then to be <em>rebooted</em> for kernel boot parameters to be applied.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the the host to manage.</div>        </td></tr>
                <tr><td>nested_attributes<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies list of the attributes which should be fetched from the API.</div><div>This parameter apply only when <code>fetch_nested</code> is <em>true</em>.</div>        </td></tr>
                <tr><td>override_display<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Override the display address of all VMs on this host with specified address.</div>        </td></tr>
                <tr><td>override_iptables<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If True host iptables will be overridden by host deploy script.</div><div>Note that <code>override_iptables</code> is <em>false</em> by default in oVirt.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password of the root. It's required in case <code>public_key</code> is set to <em>False</em>.</div>        </td></tr>
                <tr><td>poll_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3</td>
        <td></td>
        <td><div>Number of the seconds the module waits until another poll request on entity status is sent.</div>        </td></tr>
                <tr><td>public_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div><em>True</em> if the public key should be used to authenticate to host.</div><div>It's required in case <code>password</code> is not set.</div></br>
    <div style="font-size: small;">aliases: ssh_public_key<div>        </td></tr>
                <tr><td>spm_priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>SPM priority of the host. Integer value from 1 to 10, where higher number means higher priority.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>maintenance</li><li>upgraded</li><li>started</li><li>restarted</li><li>stopped</li><li>reinstalled</li></ul></td>
        <td><div>State which should a host to be in after successful completion.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>180</td>
        <td></td>
        <td><div>The amount of time in seconds the module should wait for the instance to get into desired state.</div>        </td></tr>
                <tr><td>wait<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div><em>True</em> if the module should wait for the entity to get into desired state.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Examples don't contain auth parameter for simplicity,
    # look at ovirt_auth module to see how to reuse authentication:
    
    # Add host with username/password supporting SR-IOV.
    # Note that override_iptables is false by default in oVirt:
    - ovirt_hosts:
        cluster: Default
        name: myhost
        address: 10.34.61.145
        password: secret
        override_iptables: true
        kernel_params:
          - intel_iommu=on
    
    # Add host using public key
    - ovirt_hosts:
        public_key: true
        cluster: Default
        name: myhost2
        address: 10.34.61.145
        override_iptables: true
    
    # Deploy hosted engine host
    - ovirt_hosts:
        cluster: Default
        name: myhost2
        password: secret
        address: 10.34.61.145
        override_iptables: true
        hosted_engine: deploy
    
    # Maintenance
    - ovirt_hosts:
        state: maintenance
        name: myhost
    
    # Restart host using power management:
    - ovirt_hosts:
        state: restarted
        name: myhost
    
    # Upgrade host
    - ovirt_hosts:
        state: upgraded
        name: myhost
    
    # Reinstall host using public key
    - ovirt_hosts:
        state: reinstalled
        name: myhost
        public_key: true
    
    # Remove host
    - ovirt_hosts:
        state: absent
        name: myhost
        force: True

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
        <td> host </td>
        <td> Dictionary of all the host attributes. Host attributes can be found on your oVirt instance at following url: https://ovirt.example.com/ovirt-engine/api/model#types/host. </td>
        <td align=center> On success if host is found. </td>
        <td align=center>  </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> id </td>
        <td> ID of the host which is managed </td>
        <td align=center> On success if host is found. </td>
        <td align=center> str </td>
        <td align=center> 7de90f31-222c-436c-a1ca-7e655bd5b60c </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - In order to use this module you have to install oVirt Python SDK. To ensure it's installed with correct version you can create the following task: *pip: name=ovirt-engine-sdk-python version=4.0.0*



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
