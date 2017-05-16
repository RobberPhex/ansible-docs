.. _pulp_repo:


pulp_repo - Add or remove Pulp repos from a remote host.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add or remove Pulp repos from a remote host.




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
                <tr><td>add_export_distributor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether or not to add the export distributor to new <code>rpm</code> repositories.</div>        </td></tr>
                <tr><td>feed<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Upstream feed URL to receive updates from.</div>        </td></tr>
                <tr><td>force_basic_auth<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>httplib2, the library used by the <span class='module'>uri</span> module only sends authentication information when a webservice responds to an initial request with a 401 status. Since some basic auth services do not properly send a 401, logins will fail. This option forces the sending of the Basic authentication header upon initial request.</div>        </td></tr>
                <tr><td>importer_ssl_ca_cert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>CA certificate string used to validate the feed source SSL certificate. This can be the file content or the path to the file.</div>        </td></tr>
                <tr><td>importer_ssl_client_cert<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Certificate used as the client certificate when synchronizing the repository. This is used to communicate authentication information to the feed source. The value to this option must be the full path to the certificate. The specified file may be the certificate itself or a single file containing both the certificate and private key. This can be the file content or the path to the file.</div>        </td></tr>
                <tr><td>importer_ssl_client_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Private key to the certificate specified in <em>importer_ssl_client_cert</em>, assuming it is not included in the certificate file itself. This can be the file content or the path to the file.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the repo to add or remove. This correlates to repo-id in Pulp.</div>        </td></tr>
                <tr><td>proxy_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Proxy url setting for the pulp repository importer. This is in the format scheme://host.</div>        </td></tr>
                <tr><td>proxy_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Proxy port setting for the pulp repository importer.</div>        </td></tr>
                <tr><td>publish_distributor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Distributor to use when state is <code>publish</code>. The default is to publish all distributors.</div>        </td></tr>
                <tr><td>pulp_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>http://127.0.0.1</td>
        <td></td>
        <td><div>URL of the pulp server to connect to.</div>        </td></tr>
                <tr><td>relative_url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Relative URL for the local repository.</div>        </td></tr>
                <tr><td>repo_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>rpm</td>
        <td></td>
        <td><div>Repo plugin type to use (i.e. <code>rpm</code>, <code>docker</code>).</div>        </td></tr>
                <tr><td>serve_http<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Make the repo available over HTTP.</div>        </td></tr>
                <tr><td>serve_https<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Make the repo available over HTTPS.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>sync</li><li>publish</li></ul></td>
        <td><div>The repo state. A state of <code>sync</code> will queue a sync of the repo. This is asynchronous but not delayed like a scheduled sync. A state of <code>publish</code> will use the repository's distributor to publish the content.</div>        </td></tr>
                <tr><td>url_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The password for use in HTTP basic authentication to the pulp API. If the <em>url_username</em> parameter is not specified, the <em>url_password</em> parameter will not be used.</div>        </td></tr>
                <tr><td>url_username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The username for use in HTTP basic authentication to the pulp API.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div>        </td></tr>
                <tr><td>wait_for_completion<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Wait for asynchronous tasks to complete before returning.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create a new repo with name 'my_repo'
      pulp_repo:
        name: my_repo
        relative_url: my/repo
        state: present
    
    - name: Create a repo with a feed and a relative URL
      pulp_repo:
        name: my_centos_updates
        repo_type: rpm
        feed: http://mirror.centos.org/centos/6/updates/x86_64/
        relative_url: centos/6/updates
        url_username: admin
        url_password: admin
        force_basic_auth: yes
        state: present
    
    - name: Remove a repo from the pulp server
      pulp_repo:
        name: my_old_repo
        repo_type: rpm
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
        <td> repo </td>
        <td> Name of the repo that the action was performed on. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> my_repo </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - This module can currently only create distributors and importers on rpm repositories. Contributions to support other repo types are welcome.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
