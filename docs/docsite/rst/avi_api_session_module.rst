.. _avi_api_session:


avi_api_session - Avi API Module
++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module can be used for calling any resources defined in Avi REST API. https://avinetworks.com/
* This module is useful for invoking HTTP Patch methods and accessing resources that do not have an REST object associated with them.


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
                <tr><td>data<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>HTTP body in YAML or JSON format.</div>        </td></tr>
                <tr><td>http_method<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>get</li><li>put</li><li>post</li><li>patch</li><li>delete</li></ul></td>
        <td><div>Allowed HTTP methods for RESTful services and are supported by Avi Controller.</div>        </td></tr>
                <tr><td>params<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Query parameters passed to the HTTP API.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password of Avi user in Avi controller. The default value is the environment variable <code>AVI_PASSWORD</code>.</div>        </td></tr>
                <tr><td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path for Avi API resource. For example, <code>path: virtualservice</code> will translate to <code>api/virtualserivce</code>.</div>        </td></tr>
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
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Timeout (in seconds) for Avi API calls.</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Username used for accessing Avi controller. The default value is the environment variable <code>AVI_USERNAME</code>.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    
      - name: Get Pool Information using avi_api_session
        avi_api_session:
          controller: "{{ controller }}"
          username: "{{ username }}"
          password: "{{ password }}"
          http_method: get
          path: pool
          params:
            name: "{{ pool_name }}"
        register: pool_results
    
      - name: Patch Pool with list of servers
        avi_api_session:
          controller: "{{ controller }}"
          username: "{{ username }}"
          password: "{{ password }}"
          http_method: patch
          path: "{{ pool_path }}"
          data:
            add:
              servers:
                - ip:
                    addr: 10.10.10.10
                    type: V4
                - ip:
                    addr: 20.20.20.20
                    type: V4
        register: updated_pool
    
      - name: Fetch Pool metrics bandwidth and connections rate
        avi_api_session:
          controller: "{{ controller }}"
          username: "{{ username }}"
          password: "{{ password }}"
          http_method: get
          path: analytics/metrics/pool
          params:
            name: "{{ pool_name }}"
            metric_id: l4_server.avg_bandwidth,l4_server.avg_complete_conns
            step: 300
            limit: 10
        register: pool_metrics
    

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
        <td> Avi REST resource </td>
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
