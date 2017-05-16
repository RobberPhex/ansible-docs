.. _uri:


uri - Interacts with webservices
++++++++++++++++++++++++++++++++



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
    <td>HEADER_<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Any parameter starting with "HEADER_" is a sent with your request as a header. For example, HEADER_Content-Type="application/json" would send the header "Content-Type" along with your request with a value of "application/json". This option is deprecated as of <code>2.1</code> and may be removed in a future release. Use <em>headers</em> instead.</div></td></tr>
            <tr>
    <td>body<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The body of the http request/response to the web service. If <code>body_format</code> is set to 'json' it will take an already formatted JSON string or convert a data structure into JSON.</div></td></tr>
            <tr>
    <td>body_format<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>raw</td>
        <td><ul><li>raw</li><li>json</li></ul></td>
        <td><div>The serialization format of the body. When set to json, encodes the body argument, if needed, and automatically sets the Content-Type header accordingly.</div></td></tr>
            <tr>
    <td>creates<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a filename, when it already exists, this step will not be run.</div></td></tr>
            <tr>
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>path of where to download the file to (if desired). If <em>dest</em> is a directory, the basename of the file on the remote server will be used.</div></td></tr>
            <tr>
    <td>follow_redirects<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>safe</td>
        <td><ul><li>all</li><li>safe</li><li>none</li></ul></td>
        <td><div>Whether or not the URI module should follow redirects. <code>all</code> will follow all redirects. <code>safe</code> will follow only "safe" redirects, where "safe" means that the client is only doing a GET or HEAD on the URI to which it is being redirected. <code>none</code> will not follow any redirects. Note that <code>yes</code> and <code>no</code> choices are accepted for backwards compatibility, where <code>yes</code> is the equivalent of <code>all</code> and <code>no</code> is the equivalent of <code>safe</code>. <code>yes</code> and <code>no</code> are deprecated and will be removed in some future version of Ansible.</div></td></tr>
            <tr>
    <td>force_basic_auth<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>The library used by the uri module only sends authentication information when a webservice responds to an initial request with a 401 status. Since some basic auth services do not properly send a 401, logins will fail. This option forces the sending of the Basic authentication header upon initial request.</div></td></tr>
            <tr>
    <td>headers<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Add custom HTTP headers to a request in the format of a YAML hash</div></td></tr>
            <tr>
    <td>method<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>GET</td>
        <td><ul><li>GET</li><li>POST</li><li>PUT</li><li>HEAD</li><li>DELETE</li><li>OPTIONS</li><li>PATCH</li><li>TRACE</li><li>CONNECT</li><li>REFRESH</li></ul></td>
        <td><div>The HTTP method of the request or response. It MUST be uppercase.</div></td></tr>
            <tr>
    <td>others<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>all arguments accepted by the <span class='module'>file</span> module also work here</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>password for the module to use for Digest, Basic or WSSE authentication.</div></td></tr>
            <tr>
    <td>removes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a filename, when it does not exist, this step will not be run.</div></td></tr>
            <tr>
    <td>return_content<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether or not to return the body of the request as a "content" key in the dictionary result. If the reported Content-type is "application/json", then the JSON is additionally loaded into a key called <code>json</code> in the dictionary results.</div></td></tr>
            <tr>
    <td>status_code<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>200</td>
        <td><ul></ul></td>
        <td><div>A valid, numeric, HTTP status code that signifies success of the request. Can also be comma separated list of status codes.</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td><div>The socket level timeout in seconds</div></td></tr>
            <tr>
    <td>url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>HTTP or HTTPS URL in the form (http|https)://host.domain[:port]/path</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>username for the module to use for Digest, Basic or WSSE authentication.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.9.2)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated.  This should only set to <code>no</code> used on personally controlled sites using self-signed certificates.  Prior to 1.9.2 the code defaulted to <code>no</code>.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Check that you can connect (GET) to a page and it returns a status 200
    - uri: url=http://www.example.com
    
    # Check that a page returns a status 200 and fail if the word AWESOME is not
    # in the page contents.
    - action: uri url=http://www.example.com return_content=yes
      register: webpage
    
    - action: fail
      when: "'AWESOME' not in webpage.content"
    
    
    # Create a JIRA issue
    - uri:
        url: https://your.jira.example.com/rest/api/2/issue/
        method: POST
        user: your_username
        password: your_pass
        body: "{{ lookup('file','issue.json') }}"
        force_basic_auth: yes
        status_code: 201
        body_format: json
    
    # Login to a form based webpage, then use the returned cookie to
    # access the app in later tasks
    
    - uri:
        url: https://your.form.based.auth.example.com/index.php
        method: POST
        body: "name=your_username&password=your_password&enter=Sign%20in"
        status_code: 302
        HEADER_Content-Type: "application/x-www-form-urlencoded"
      register: login
    
    - uri:
        url: https://your.form.based.auth.example.com/dashboard.php
        method: GET
        return_content: yes
        HEADER_Cookie: "{{login.set_cookie}}"
    
    # Queue build of a project in Jenkins:
    - uri:
        url: "http://{{ jenkins.host }}/job/{{ jenkins.job }}/build?token={{ jenkins.token }}"
        method: GET
        user: "{{ jenkins.user }}"
        password: "{{ jenkins.password }}"
        force_basic_auth: yes
        status_code: 201
    


Notes
-----

.. note:: The dependency on httplib2 was removed in Ansible 2.1


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

