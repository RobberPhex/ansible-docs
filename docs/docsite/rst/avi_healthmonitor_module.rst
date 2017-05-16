.. _avi_healthmonitor:


avi_healthmonitor - Module for setup of HealthMonitor Avi RESTful Object
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module is used to configure HealthMonitor object
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
                <tr><td>dns_monitor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Healthmonitordns settings for healthmonitor.</div>        </td></tr>
                <tr><td>external_monitor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Healthmonitorexternal settings for healthmonitor.</div>        </td></tr>
                <tr><td>failed_checks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of continuous failed health checks before the server is marked down.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 2.</div>        </td></tr>
                <tr><td>http_monitor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Healthmonitorhttp settings for healthmonitor.</div>        </td></tr>
                <tr><td>https_monitor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Healthmonitorhttp settings for healthmonitor.</div>        </td></tr>
                <tr><td>monitor_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Use this port instead of the port defined for the server in the pool.</div><div>If the monitor succeeds to this port, the load balanced traffic will still be sent to the port of the server defined within the pool.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>A user friendly name for this health monitor.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password of Avi user in Avi controller. The default value is the environment variable <code>AVI_PASSWORD</code>.</div>        </td></tr>
                <tr><td>receive_timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A valid response from the server is expected within the receive timeout window.</div><div>This timeout must be less than the send interval.</div><div>If server status is regularly flapping up and down, consider increasing this value.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 4.</div>        </td></tr>
                <tr><td>send_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Frequency, in seconds, that monitors are sent to a server.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 10.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>absent</li><li>present</li></ul></td>
        <td><div>The state that should be applied on the entity.</div>        </td></tr>
                <tr><td>successful_checks<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Number of continuous successful health checks before server is marked up.</div><div>Default value when not specified in API or module is interpreted by Avi Controller as 2.</div>        </td></tr>
                <tr><td>tcp_monitor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Healthmonitortcp settings for healthmonitor.</div>        </td></tr>
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
        <td><div>Type of the health monitor.</div>        </td></tr>
                <tr><td>udp_monitor<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Healthmonitorudp settings for healthmonitor.</div>        </td></tr>
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
        <td><div>Uuid of the health monitor.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Create a HTTPS health monitor
      avi_healthmonitor:
        controller: 10.10.27.90
        username: admin
        password: AviNetworks123!
        https_monitor:
          http_request: HEAD / HTTP/1.0
          http_response_code:
            - HTTP_2XX
            - HTTP_3XX
        receive_timeout: 4
        failed_checks: 3
        send_interval: 10
        successful_checks: 3
        type: HEALTH_MONITOR_HTTPS
        name: MyWebsite-HTTPS

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
        <td> HealthMonitor (api/healthmonitor) object </td>
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
