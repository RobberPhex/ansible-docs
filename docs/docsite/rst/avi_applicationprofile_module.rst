.. _avi_applicationprofile:


avi_applicationprofile - Module for setup of ApplicationProfile Avi RESTful Object
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module is used to configure ApplicationProfile object
* more examples at https://github.com/avinetworks/devops


Requirements (on host that executes module)
-------------------------------------------

  * avisdk


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
                <tr><td>controller<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>IP address or hostname of the controller. The default value is the environment variable <code>AVI_CONTROLLER</code>.</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>User defined description for the object.</div>        </td></tr>
                <tr><td>dns_service_profile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies various dns service related controls for virtual service.</div>        </td></tr>
                <tr><td>dos_rl_profile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies various security related controls for virtual service.</div>        </td></tr>
                <tr><td>http_profile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the http application proxy profile parameters.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the application profile.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password of Avi user in Avi controller. The default value is the environment variable <code>AVI_PASSWORD</code>.</div>        </td></tr>
                <tr><td>preserve_client_ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies if client ip needs to be preserved for backend connection.</div><div>Not compatible with connection multiplexing.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>The state that should be applied on the entity.</div>        </td></tr>
                <tr><td>tcp_app_profile<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specifies the tcp application proxy profile parameters.</div>        </td></tr>
                <tr><td>tenant<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>admin</td>
        <td></td>
        <td><div>Name of tenant used for all Avi API calls and context of object.</div>        </td></tr>
                <tr><td>tenant_ref<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>It is a reference to an object of type tenant.</div>        </td></tr>
                <tr><td>tenant_uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>UUID of tenant used for all Avi API calls and context of object.</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Specifies which application layer proxy is enabled for the virtual service.</div>        </td></tr>
                <tr><td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Avi controller URL of the object.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Username used for accessing Avi controller. The default value is the environment variable <code>AVI_USERNAME</code>.</div>        </td></tr>
                <tr><td>uuid<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Uuid of the application profile.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

      - name: Create an Application Profile for HTTP application enabled for SSL traffic
        avi_applicationprofile:
          controller: ''
          username: ''
          password: ''
          http_profile:
            cache_config:
              age_header: true
              aggressive: false
              date_header: true
              default_expire: 600
              enabled: false
              heuristic_expire: false
              max_cache_size: 0
              max_object_size: 4194304
              mime_types_group_refs:
              - admin:System-Cacheable-Resource-Types
              min_object_size: 100
              query_cacheable: false
              xcache_header: true
            client_body_timeout: 0
            client_header_timeout: 10000
            client_max_body_size: 0
            client_max_header_size: 12
            client_max_request_size: 48
            compression_profile:
              compressible_content_ref: admin:System-Compressible-Content-Types
              compression: false
              remove_accept_encoding_header: true
              type: AUTO_COMPRESSION
            connection_multiplexing_enabled: true
            hsts_enabled: false
            hsts_max_age: 365
            http_to_https: false
            httponly_enabled: false
            keepalive_header: false
            keepalive_timeout: 30000
            max_bad_rps_cip: 0
            max_bad_rps_cip_uri: 0
            max_bad_rps_uri: 0
            max_rps_cip: 0
            max_rps_cip_uri: 0
            max_rps_unknown_cip: 0
            max_rps_unknown_uri: 0
            max_rps_uri: 0
            post_accept_timeout: 30000
            secure_cookie_enabled: false
            server_side_redirect_to_https: false
            spdy_enabled: false
            spdy_fwd_proxy_mode: false
            ssl_client_certificate_mode: SSL_CLIENT_CERTIFICATE_NONE
            ssl_everywhere_enabled: false
            websockets_enabled: true
            x_forwarded_proto_enabled: false
            xff_alternate_name: X-Forwarded-For
            xff_enabled: true
          name: System-HTTP
          tenant_ref: admin
          type: APPLICATION_PROFILE_TYPE_HTTP

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
        <td> obj </td>
        <td> ApplicationProfile (api/applicationprofile) object </td>
        <td align=center> success, changed </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
