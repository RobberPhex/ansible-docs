.. _avi_sslprofile:


avi_sslprofile - Module for setup of SSLProfile Avi RESTful Object
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module is used to configure SSLProfile object
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
                <tr><td>accepted_ciphers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Ciphers suites represented as defined by <a href='http://www.openssl.org/docs/apps/ciphers.html'>http://www.openssl.org/docs/apps/ciphers.html</a>.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as AES:3DES:RC4.</div>        </td></tr>
                <tr><td>accepted_versions<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Set of versions accepted by the server.</div>        </td></tr>
                <tr><td>cipher_enums<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Cipher_enums of sslprofile.</div>        </td></tr>
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
                <tr><td>dhparam<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dh parameters used in ssl.</div><div>At this time, it is not configurable and is set to 2048 bits.</div>        </td></tr>
                <tr><td>enable_ssl_session_reuse<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enable ssl session re-use.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as True.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the object.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password of Avi user in Avi controller. The default value is the environment variable <code>AVI_PASSWORD</code>.</div>        </td></tr>
                <tr><td>prefer_client_cipher_ordering<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Prefer the ssl cipher ordering presented by the client during the ssl handshake over the one specified in the ssl profile.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>send_close_notify<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Send 'close notify' alert message for a clean shutdown of the ssl connection.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as True.</div>        </td></tr>
                <tr><td>ssl_rating<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Sslrating settings for sslprofile.</div>        </td></tr>
                <tr><td>ssl_session_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The amount of time before an ssl session expires.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 86400.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>The state that should be applied on the entity.</div>        </td></tr>
                <tr><td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of tag.</div>        </td></tr>
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
        <td><div>Unique object identifier of the object.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

      - name: Create SSL profile with list of allowed ciphers
        avi_sslprofile:
          controller: ''
          username: ''
          password: ''
          accepted_ciphers: >
            ECDHE-ECDSA-AES128-GCM-SHA256:ECDHE-ECDSA-AES128-SHA:ECDHE-ECDSA-AES256-SHA:
            ECDHE-ECDSA-AES256-GCM-SHA384:ECDHE-ECDSA-AES128-SHA256:ECDHE-ECDSA-AES256-SHA384:
            AES128-GCM-SHA256:AES256-GCM-SHA384:AES128-SHA256:AES256-SHA256:AES128-SHA:
            AES256-SHA:DES-CBC3-SHA:ECDHE-RSA-AES128-SHA:ECDHE-RSA-AES256-SHA384:
            ECDHE-RSA-AES128-SHA256:ECDHE-RSA-AES256-GCM-SHA384:ECDHE-RSA-AES128-GCM-SHA256:ECDHE-RSA-AES256-SHA
          accepted_versions:
          - type: SSL_VERSION_TLS1
          - type: SSL_VERSION_TLS1_1
          - type: SSL_VERSION_TLS1_2
          cipher_enums:
          - TLS_ECDHE_ECDSA_WITH_AES_128_GCM_SHA256
          - TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA
          - TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA
          - TLS_ECDHE_ECDSA_WITH_AES_256_GCM_SHA384
          - TLS_ECDHE_ECDSA_WITH_AES_128_CBC_SHA256
          - TLS_ECDHE_ECDSA_WITH_AES_256_CBC_SHA384
          - TLS_RSA_WITH_AES_128_GCM_SHA256
          - TLS_RSA_WITH_AES_256_GCM_SHA384
          - TLS_RSA_WITH_AES_128_CBC_SHA256
          - TLS_RSA_WITH_AES_256_CBC_SHA256
          - TLS_RSA_WITH_AES_128_CBC_SHA
          - TLS_RSA_WITH_AES_256_CBC_SHA
          - TLS_RSA_WITH_3DES_EDE_CBC_SHA
          - TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA
          - TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA384
          - TLS_ECDHE_RSA_WITH_AES_128_CBC_SHA256
          - TLS_ECDHE_RSA_WITH_AES_256_GCM_SHA384
          - TLS_ECDHE_RSA_WITH_AES_128_GCM_SHA256
          - TLS_ECDHE_RSA_WITH_AES_256_CBC_SHA
          name: PFS-BOTH-RSA-EC
          send_close_notify: true
          ssl_rating:
            compatibility_rating: SSL_SCORE_EXCELLENT
            performance_rating: SSL_SCORE_EXCELLENT
            security_score: '100.0'
          tenant_ref: Demo

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
        <td> SSLProfile (api/sslprofile) object </td>
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
