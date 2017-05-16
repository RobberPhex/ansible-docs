.. _win_uri:


win_uri - Interacts with webservices.
+++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Interacts with HTTP and HTTPS web services and supports Digest, Basic and WSSE HTTP authentication mechanisms.




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
            <tr>
    <td>body<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The body of the HTTP request/response to the web service.</div></td></tr>
            <tr>
    <td>content_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Sets the "Content-Type" header.</div></td></tr>
            <tr>
    <td>headers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Key Value pairs for headers. Example "Host: www.somesite.com"</div></td></tr>
            <tr>
    <td>method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>GET</td>
        <td><ul><li>GET</li><li>POST</li><li>PUT</li><li>HEAD</li><li>DELETE</li><li>OPTIONS</li><li>PATCH</li><li>TRACE</li><li>CONNECT</li><li>REFRESH</li></ul></td>
        <td><div>The HTTP Method of the request or response.</div></td></tr>
            <tr>
    <td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>HTTP or HTTPS URL in the form of (http|https)://host.domain:port/path</div></td></tr>
            <tr>
    <td>use_basic_parsing<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>This module relies upon 'Invoke-WebRequest', which by default uses the Internet Explorer Engine to parse a webpage. There's an edge-case where if a user hasn't run IE before, this will fail. The only advantage to using the Internet Explorer praser is that you can traverse the DOM in a powershell script. That isn't useful for Ansible, so by default we toggle 'UseBasicParsing'. However, you can toggle that off here.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Send a GET request and store the output:
    ---
    - name: Perform a GET and Store Output
      win_uri:
        url: http://www.somesite.com/myendpoint
      register: http_output
    
    # Set a HOST header to hit an internal webserver:
    ---
    - name: Hit a Specific Host on the Server
      win_uri:
        url: http://my.internal.server.com
        method: GET
        headers:
          host: "www.somesite.com"
    
    # Do a HEAD request on an endpoint
    ---
    - name: Perform a HEAD on an Endpoint
      win_uri:
        url: http://www.somesite.com
        method: HEAD
    
    # Post a body to an endpoint
    ---
    - name: POST a Body to an Endpoint
      win_uri:
        url: http://www.somesite.com
        method: POST
        body: "{ 'some': 'json' }"

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
        <td> url </td>
        <td> The Target URL </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> https://www.ansible.com </td>
    </tr>
            <tr>
        <td> status_code </td>
        <td> The HTTP Status Code of the response. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 200 </td>
    </tr>
            <tr>
        <td> use_basic_parsing </td>
        <td> The state of the "use_basic_parsing" flag. </td>
        <td align=center> always </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> raw_content </td>
        <td> The raw content of the HTTP response. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> HTTP/1.1 200 OK X-XSS-Protection: 1; mode=block X-Frame-Options: SAMEORIGIN Alternate-Protocol: 443:quic,p=1 Alt-Svc: quic="www.google.com:443"; ma=2592000; v="30,29,28,27,26,25",quic=":443"; ma=2... </td>
    </tr>
            <tr>
        <td> headers </td>
        <td> The Headers of the response. </td>
        <td align=center> success </td>
        <td align=center> dict </td>
        <td align=center> {'Content-Type': 'application/json'} </td>
    </tr>
            <tr>
        <td> content_type </td>
        <td> The "content-type" header used. </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> application/json </td>
    </tr>
            <tr>
        <td> raw_content_length </td>
        <td> The byte size of the response. </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 54447 </td>
    </tr>
            <tr>
        <td> status_description </td>
        <td> A summery of the status. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> method </td>
        <td> The HTTP method used. </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> GET </td>
    </tr>
        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

