.. _ovirt_storage_domains:


ovirt_storage_domains - Module to manage storage domains in oVirt
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Module to manage storage domains in oVirt


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
                <tr><td>auth<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Dictionary with values needed to create HTTP/HTTPS connection to oVirt:</div><div><code>username</code>[<em>required</em>] - The name of the user, something like <em>admin@internal</em>. Default value is set by <em>OVIRT_USERNAME</em> environment variable.</div><div><code>password</code>[<em>required</em>] - The password of the user. Default value is set by <em>OVIRT_PASSWORD</em> environment variable.</div><div><code>url</code>[<em>required</em>] - A string containing the base URL of the server, usually something like `<em>https://server.example.com/ovirt-engine/api</em>`. Default value is set by <em>OVIRT_URL</em> environment variable.</div><div><code>token</code> - Token to be used instead of login with username/password. Default value is set by <em>OVIRT_TOKEN</em> environment variable.</div><div><code>insecure</code> - A boolean flag that indicates if the server TLS certificate and host name should be checked.</div><div><code>ca_file</code> - A PEM file containing the trusted CA certificates. The certificate presented by the server will be verified using these CA certificates. If `<code>ca_file</code>` parameter is not set, system wide CA certificate store is used. Default value is set by <em>OVIRT_CAFILE</em> environment variable.</div><div><code>kerberos</code> - A boolean flag indicating if Kerberos authentication should be used instead of the default basic authentication.</div>        </td></tr>
                <tr><td>comment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Comment of the storage domain.</div>        </td></tr>
                <tr><td>data_center<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Data center name where storage domain should be attached.</div><div>This parameter isn't idempotent, it's not possible to change data center of storage domain.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Description of the storage domain.</div>        </td></tr>
                <tr><td>destroy<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Logical remove of the storage domain. If <em>true</em> retains the storage domain's data for import.</div><div>This parameter is relevant only when <code>state</code> is <em>absent</em>.</div>        </td></tr>
                <tr><td>domain_function<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>data</td>
        <td><ul><li>data</li><li>iso</li><li>export</li></ul></td>
        <td><div>Function of the storage domain.</div><div>This parameter isn't idempotent, it's not possible to change domain function of storage domain.</div></br>
    <div style="font-size: small;">aliases: type<div>        </td></tr>
                <tr><td>fcp<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dictionary with values for fibre channel storage type:</div><div><code>address</code> - Address of the fibre channel storage server.</div><div><code>port</code> - Port of the fibre channel storage server.</div><div><code>lun_id</code> - LUN id.</div><div>Note that these parameters are not idempotent.</div>        </td></tr>
                <tr><td>fetch_nested<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> the module will fetch additional data from the API.</div><div>It will fetch IDs of the VMs disks, snapshots, etc. User can configure to fetch other attributes of the nested entities by specifying <code>nested_attributes</code>.</div>        </td></tr>
                <tr><td>format<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> storage domain will be formatted after removing it from oVirt.</div><div>This parameter is relevant only when <code>state</code> is <em>absent</em>.</div>        </td></tr>
                <tr><td>glusterfs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dictionary with values for GlusterFS storage type:</div><div><code>address</code> - Address of the Gluster server. E.g.: myserver.mydomain.com</div><div><code>path</code> - Path of the mount point. E.g.: /path/to/my/data</div><div><code>mount_options</code> - Option which will be passed when mounting storage.</div><div>Note that these parameters are not idempotent.</div>        </td></tr>
                <tr><td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Host to be used to mount storage.</div>        </td></tr>
                <tr><td>iscsi<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dictionary with values for iSCSI storage type:</div><div><code>address</code> - Address of the iSCSI storage server.</div><div><code>port</code> - Port of the iSCSI storage server.</div><div><code>target</code> - The target IQN for the storage device.</div><div><code>lun_id</code> - LUN id.</div><div><code>username</code> - A CHAP user name for logging into a target.</div><div><code>password</code> - A CHAP password for logging into a target.</div><div><code>override_luns</code> - If <em>True</em> ISCSI storage domain luns will be overriden before adding.</div><div>Note that these parameters are not idempotent.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Name of the the storage domain to manage.</div>        </td></tr>
                <tr><td>nested_attributes<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies list of the attributes which should be fetched from the API.</div><div>This parameter apply only when <code>fetch_nested</code> is <em>true</em>.</div>        </td></tr>
                <tr><td>nfs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dictionary with values for NFS storage type:</div><div><code>address</code> - Address of the NFS server. E.g.: myserver.mydomain.com</div><div><code>path</code> - Path of the mount point. E.g.: /path/to/my/data</div><div><code>version</code> - NFS version. One of: <em>auto</em>, <em>v3</em>, <em>v4</em> or <em>v4_1</em>.</div><div><code>timeout</code> - The time in tenths of a second to wait for a response before retrying NFS requests. Range 0 to 65535.</div><div><code>retrans</code> - The number of times to retry a request before attempting further recovery actions. Range 0 to 65535.</div><div>Note that these parameters are not idempotent.</div>        </td></tr>
                <tr><td>poll_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3</td>
        <td></td>
        <td><div>Number of the seconds the module waits until another poll request on entity status is sent.</div>        </td></tr>
                <tr><td>posixfs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dictionary with values for PosixFS storage type:</div><div><code>path</code> - Path of the mount point. E.g.: /path/to/my/data</div><div><code>vfs_type</code> - Virtual File System type.</div><div><code>mount_options</code> - Option which will be passed when mounting storage.</div><div>Note that these parameters are not idempotent.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>maintenance</li><li>unattached</li></ul></td>
        <td><div>Should the storage domain be present/absent/maintenance/unattached</div>        </td></tr>
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
    
    # Add data NFS storage domain
    - ovirt_storage_domains:
        name: data_nfs
        host: myhost
        data_center: mydatacenter
        nfs:
          address: 10.34.63.199
          path: /path/data
    
    # Add data iSCSI storage domain:
    - ovirt_storage_domains:
        name: data_iscsi
        host: myhost
        data_center: mydatacenter
        iscsi:
          target: iqn.2016-08-09.domain-01:nickname
          lun_id: 1IET_000d0002
          address: 10.34.63.204
    
    # Add data glusterfs storage domain
    -  ovirt_storage_domains:
        name: glusterfs_1
        host: myhost
        data_center: mydatacenter
        glusterfs:
          address: 10.10.10.10
          path: /path/data
    
    # Import export NFS storage domain:
    - ovirt_storage_domains:
        domain_function: export
        host: myhost
        data_center: mydatacenter
        nfs:
          address: 10.34.63.199
          path: /path/export
    
    # Create ISO NFS storage domain
    - ovirt_storage_domains:
        name: myiso
        domain_function: iso
        host: myhost
        data_center: mydatacenter
        nfs:
          address: 10.34.63.199
          path: /path/iso
    
    # Remove storage domain
    - ovirt_storage_domains:
        state: absent
        name: mystorage_domain
        format: true

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
        <td> storage_domain </td>
        <td> Dictionary of all the storage domain attributes. Storage domain attributes can be found on your oVirt instance at following url: https://ovirt.example.com/ovirt-engine/api/model#types/storage_domain. </td>
        <td align=center> On success if storage domain is found. </td>
        <td align=center>  </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> id </td>
        <td> ID of the storage domain which is managed </td>
        <td align=center> On success if storage domain is found. </td>
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
