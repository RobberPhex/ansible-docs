.. _nginx_status_facts:


nginx_status_facts - Retrieve nginx status facts.
+++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Gathers facts from nginx from an URL having ``stub_status`` enabled.




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
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>HTTP connection timeout in seconds.</div>        </td></tr>
                <tr><td>url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>URL of the nginx status.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Gather status facts from nginx on localhost
    - name: get current http stats
      nginx_status_facts:
        url: http://localhost/nginx_status
    
    # Gather status facts from nginx on localhost with a custom timeout of 20 seconds
    - name: get current http stats
      nginx_status_facts:
        url: http://localhost/nginx_status
        timeout: 20

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
        <td> nginx_status_facts.requests </td>
        <td> The total number of client requests. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 144332345 </td>
    </tr>
            <tr>
        <td> nginx_status_facts.data </td>
        <td> HTTP response as is. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Active connections: 2340 server accepts handled requests 81769947 81769947 144332345 Reading: 0 Writing: 241 Waiting: 2092  </td>
    </tr>
            <tr>
        <td> nginx_status_facts.writing </td>
        <td> The current number of connections where nginx is writing the response back to the client. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 241 </td>
    </tr>
            <tr>
        <td> nginx_status_facts.reading </td>
        <td> The current number of connections where nginx is reading the request header. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 0 </td>
    </tr>
            <tr>
        <td> nginx_status_facts.waiting </td>
        <td> The current number of idle client connections waiting for a request. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 2092 </td>
    </tr>
            <tr>
        <td> nginx_status_facts.active_connections </td>
        <td> Active connections. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 2340 </td>
    </tr>
            <tr>
        <td> nginx_status_facts.accepts </td>
        <td> The total number of accepted client connections. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 81769947 </td>
    </tr>
            <tr>
        <td> nginx_status_facts.handled </td>
        <td> The total number of handled connections. Generally, the parameter value is the same as accepts unless some resource limits have been reached. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 81769947 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - See http://nginx.org/en/docs/http/ngx_http_stub_status_module.html for more information.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
