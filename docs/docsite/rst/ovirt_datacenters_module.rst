.. _ovirt_datacenters:


ovirt_datacenters - Module to manage data centers in oVirt
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Module to manage data centers in oVirt


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
        <td><div>Comment of the data center.</div>        </td></tr>
                <tr><td>compatibility_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Compatibility version of the data center.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Description of the data center.</div>        </td></tr>
                <tr><td>fetch_nested<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>If <em>True</em> the module will fetch additional data from the API.</div><div>It will fetch IDs of the VMs disks, snapshots, etc. User can configure to fetch other attributes of the nested entities by specifying <code>nested_attributes</code>.</div>        </td></tr>
                <tr><td>local<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div><em>True</em> if the data center should be local, <em>False</em> if should be shared.</div><div>Default value is set by engine.</div>        </td></tr>
                <tr><td>mac_pool<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>MAC pool to be used by this datacenter.</div><div>IMPORTANT: This option is deprecated in oVirt 4.1. You should use <code>mac_pool</code> in <code>ovirt_clusters</code> module, as MAC pools are set per cluster since 4.1.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the the data center to manage.</div>        </td></tr>
                <tr><td>nested_attributes<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies list of the attributes which should be fetched from the API.</div><div>This parameter apply only when <code>fetch_nested</code> is <em>true</em>.</div>        </td></tr>
                <tr><td>poll_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3</td>
        <td></td>
        <td><div>Number of the seconds the module waits until another poll request on entity status is sent.</div>        </td></tr>
                <tr><td>quota_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>disabled</li><li>audit</li><li>enabled</li></ul></td>
        <td><div>Quota mode of the data center. One of <em>disabled</em>, <em>audit</em> or <em>enabled</em></div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Should the data center be present or absent</div>        </td></tr>
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
    
    # Create datacenter
    - ovirt_datacenters:
        name: mydatacenter
        local: True
        compatibility_version: 4.0
        quota_mode: enabled
    
    # Remove datacenter
    - ovirt_datacenters:
        state: absent
        name: mydatacenter

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
        <td> id </td>
        <td> ID of the managed datacenter </td>
        <td align=center> On success if datacenter is found. </td>
        <td align=center> str </td>
        <td align=center> 7de90f31-222c-436c-a1ca-7e655bd5b60c </td>
    </tr>
            <tr>
        <td> data_center </td>
        <td> Dictionary of all the datacenter attributes. Datacenter attributes can be found on your oVirt instance at following url: https://ovirt.example.com/ovirt-engine/api/model#types/datacenter. </td>
        <td align=center> On success if datacenter is found. </td>
        <td align=center>  </td>
        <td align=center>  </td>
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
