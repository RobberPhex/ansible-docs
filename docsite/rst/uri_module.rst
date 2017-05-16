.. _uri:


uri - Interacts with webservices
++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.1

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
    <td>HEADER_</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Any parameter starting with "HEADER_" is a sent with your request as a header. For example, HEADER_Content-Type="application/json" would send the header "Content-Type" along with your request with a value of "application/json".</td>
    </tr>
            <tr>
    <td>body</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The body of the http request/response to the web service.</td>
    </tr>
            <tr>
    <td>creates</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>a filename, when it already exists, this step will not be run.</td>
    </tr>
            <tr>
    <td>dest</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>path of where to download the file to (if desired). If <em>dest</em> is a directory, the basename of the file on the remote server will be used.</td>
    </tr>
            <tr>
    <td>follow_redirects</td>
    <td>no</td>
    <td>safe</td>
        <td><ul><li>all</li><li>safe</li><li>none</li></ul></td>
        <td>Whether or not the URI module should follow redirects. <code>all</code> will follow all redirects. <code>safe</code> will follow only "safe" redirects, where "safe" means that the client is only doing a GET or HEAD on the URI to which it is being redirected. <code>none</code> will not follow any redirects. Note that <code>yes</code> and <code>no</code> choices are accepted for backwards compatibility, where <code>yes</code> is the equivalent of <code>all</code> and <code>no</code> is the equivalent of <code>safe</code>. <code>yes</code> and <code>no</code> are deprecated and will be removed in some future version of Ansible.</td>
    </tr>
            <tr>
    <td>force_basic_auth</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>httplib2, the library used by the uri module only sends authentication information when a webservice responds to an initial request with a 401 status. Since some basic auth services do not properly send a 401, logins will fail. This option forces the sending of the Basic authentication header upon initial request.</td>
    </tr>
            <tr>
    <td>method</td>
    <td>no</td>
    <td>GET</td>
        <td><ul><li>GET</li><li>POST</li><li>PUT</li><li>HEAD</li><li>DELETE</li><li>OPTIONS</li><li>PATCH</li></ul></td>
        <td>The HTTP method of the request or response.</td>
    </tr>
            <tr>
    <td>others</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>all arguments accepted by the <span class='module'>file</span> module also work here</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>password for the module to use for Digest, Basic or WSSE authentication.</td>
    </tr>
            <tr>
    <td>removes</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>a filename, when it does not exist, this step will not be run.</td>
    </tr>
            <tr>
    <td>return_content</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Whether or not to return the body of the request as a "content" key in the dictionary result. If the reported Content-type is "application/json", then the JSON is additionally loaded into a key called <code>json</code> in the dictionary results.</td>
    </tr>
            <tr>
    <td>status_code</td>
    <td>no</td>
    <td>200</td>
        <td><ul></ul></td>
        <td>A valid, numeric, HTTP status code that signifies success of the request. Can also be comma separated list of status codes.</td>
    </tr>
            <tr>
    <td>timeout</td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td>The socket level timeout in seconds</td>
    </tr>
            <tr>
    <td>url</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>HTTP or HTTPS URL in the form (http|https)://host.domain[:port]/path</td>
    </tr>
            <tr>
    <td>user</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>username for the module to use for Digest, Basic or WSSE authentication.</td>
    </tr>
        </table>


.. note:: Requires urlparse


.. note:: Requires httplib2


Examples
--------

.. raw:: html

    <br/>


::

    # Check that you can connect (GET) to a page and it returns a status 200
    - uri: url=http://www.example.com
    
    # Check that a page returns a status 200 and fail if the word AWESOME is not in the page contents.
    - action: uri url=http://www.example.com return_content=yes
      register: webpage
    
    - action: fail
      when: 'AWESOME' not in "{{ webpage.content }}"
    
    
    # Create a JIRA issue
    
    - uri: url=https://your.jira.example.com/rest/api/2/issue/ 
           method=POST user=your_username password=your_pass 
           body="{{ lookup('file','issue.json') }}" force_basic_auth=yes 
           status_code=201 HEADER_Content-Type="application/json"  
    
    # Login to a form based webpage, then use the returned cookie to
    # access the app in later tasks
    
    - uri: url=https://your.form.based.auth.examle.com/index.php 
           method=POST body="name=your_username&password=your_password&enter=Sign%20in" 
           status_code=302 HEADER_Content-Type="application/x-www-form-urlencoded"
      register: login
    
    - uri: url=https://your.form.based.auth.example.com/dashboard.php
           method=GET return_content=yes HEADER_Cookie="{{login.set_cookie}}"
                
    # Queue build of a project in Jenkins:
    
    - uri: url=http://{{jenkins.host}}/job/{{jenkins.job}}/build?token={{jenkins.token}} 
           method=GET user={{jenkins.user}} password={{jenkins.password}} force_basic_auth=yes status_code=201
    



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

