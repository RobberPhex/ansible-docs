.. _avi_systemconfiguration:


avi_systemconfiguration - Module for setup of SystemConfiguration Avi RESTful Object
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module is used to configure SystemConfiguration object
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
                <tr><td>admin_auth_configuration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Adminauthconfiguration settings for systemconfiguration.</div>        </td></tr>
                <tr><td>controller<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>IP address or hostname of the controller. The default value is the environment variable <code>AVI_CONTROLLER</code>.</div>        </td></tr>
                <tr><td>dns_configuration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dnsconfiguration settings for systemconfiguration.</div>        </td></tr>
                <tr><td>dns_virtualservice_refs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dns virtualservices hosting fqdn records for applications across avi vantage.</div><div>If no virtualservices are provided, avi vantage will provide dns services for configured applications.</div><div>Switching back to avi vantage from dns virtualservices is not allowed.</div><div>It is a reference to an object of type virtualservice.</div>        </td></tr>
                <tr><td>docker_mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Boolean flag to set docker_mode.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as False.</div>        </td></tr>
                <tr><td>email_configuration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Emailconfiguration settings for systemconfiguration.</div>        </td></tr>
                <tr><td>global_tenant_config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Tenantconfiguration settings for systemconfiguration.</div>        </td></tr>
                <tr><td>linux_configuration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Linuxconfiguration settings for systemconfiguration.</div>        </td></tr>
                <tr><td>mgmt_ip_access_control<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Configure ip access control for controller to restrict open access.</div>        </td></tr>
                <tr><td>ntp_configuration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Ntpconfiguration settings for systemconfiguration.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password of Avi user in Avi controller. The default value is the environment variable <code>AVI_PASSWORD</code>.</div>        </td></tr>
                <tr><td>portal_configuration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Portalconfiguration settings for systemconfiguration.</div>        </td></tr>
                <tr><td>proxy_configuration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Proxyconfiguration settings for systemconfiguration.</div>        </td></tr>
                <tr><td>snmp_configuration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Snmpconfiguration settings for systemconfiguration.</div>        </td></tr>
                <tr><td>ssh_ciphers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Allowed ciphers list for ssh to the management interface on the controller and service engines.</div><div>If this is not specified, all the default ciphers are allowed.</div><div>Ssh -q cipher provides the list of default ciphers supported.</div>        </td></tr>
                <tr><td>ssh_hmacs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Allowed hmac list for ssh to the management interface on the controller and service engines.</div><div>If this is not specified, all the default hmacs are allowed.</div><div>Ssh -q mac provides the list of default hmacs supported.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>The state that should be applied on the entity.</div>        </td></tr>
                <tr><td>tech_support_uploader_configuration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Techsupportuploaderconfiguration settings for systemconfiguration.</div>        </td></tr>
                <tr><td>tenant<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>admin</td>
        <td></td>
        <td><div>Name of tenant used for all Avi API calls and context of object.</div>        </td></tr>
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

    - name: Example to create SystemConfiguration object
      avi_systemconfiguration:
        controller: 10.10.25.42
        username: admin
        password: something
        state: present
        name: sample_systemconfiguration

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
        <td> SystemConfiguration (api/systemconfiguration) object </td>
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
