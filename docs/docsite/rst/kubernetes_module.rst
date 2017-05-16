.. _kubernetes:


kubernetes - Manage Kubernetes resources.
+++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module can manage Kubernetes resources on an existing cluster using the Kubernetes server API. Users can specify in-line API data, or specify an existing Kubernetes YAML file. Currently, this module, Only supports HTTP Basic Auth Only supports 'strategic merge' for update, http://goo.gl/fCPYxT SSL certs are not working, use 'validate_certs=off' to disable




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
                <tr><td>api_endpoint<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The IPv4 API endpoint of the Kubernetes cluster.</div></br>
    <div style="font-size: small;">aliases: endpoint<div>        </td></tr>
                <tr><td>certificate_authority_data<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Certificate Authority data for Kubernetes server. Should be in either standard PEM format or base64 encoded PEM data. Note that certificate verification is broken until ansible supports a version of 'match_hostname' that can match the IP address against the CA data.</div>        </td></tr>
                <tr><td>file_reference<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Specify full path to a Kubernets YAML file to send to API <em>endpoint</em>. This option is mutually exclusive with <code>'inline_data'</code>.</div>        </td></tr>
                <tr><td>inline_data<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The Kubernetes YAML data to send to the API <em>endpoint</em>. This option is mutually exclusive with <code>'file_reference'</code>.</div>        </td></tr>
                <tr><td>insecure<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Reverts the connection to using HTTP instead of HTTPS. This option should only be used when execuing the <span class='module'>'kubernetes'</span> module local to the Kubernetes cluster using the insecure local port (locahost:8080 by default).</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>update</li><li>replace</li></ul></td>
        <td><div>The desired action to take on the Kubernetes data.</div>        </td></tr>
                <tr><td>url_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The HTTP Basic Auth password for the API <em>endpoint</em>. This should be set unless using the <code>'insecure'</code> option.</div></br>
    <div style="font-size: small;">aliases: password<div>        </td></tr>
                <tr><td>url_username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>admin</td>
        <td></td>
        <td><div>The HTTP Basic Auth username for the API <em>endpoint</em>. This should be set unless using the <code>'insecure'</code> option.</div></br>
    <div style="font-size: small;">aliases: username<div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Enable/disable certificate validation. Note that this is set to <code>false</code> until Ansible can support IP address based certificate hostname matching (exists in &gt;= python3.5.0).</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a new namespace with in-line YAML.
    - name: Create a kubernetes namespace
      kubernetes:
        api_endpoint: 123.45.67.89
        url_username: admin
        url_password: redacted
        inline_data:
          kind: Namespace
          apiVersion: v1
          metadata:
            name: ansible-test
            labels:
              label_env: production
              label_ver: latest
            annotations:
              a1: value1
              a2: value2
        state: present
    
    # Create a new namespace from a YAML file.
    - name: Create a kubernetes namespace
      kubernetes:
        api_endpoint: 123.45.67.89
        url_username: admin
        url_password: redacted
        file_reference: /path/to/create_namespace.yaml
        state: present
    
    # Do the same thing, but using the insecure localhost port
    - name: Create a kubernetes namespace
      kubernetes:
        api_endpoint: 123.45.67.89
        insecure: true
        file_reference: /path/to/create_namespace.yaml
        state: present
    

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
        <td> api_response </td>
        <td> Raw response from Kubernetes API, content varies with API. </td>
        <td align=center> success </td>
        <td align=center> dictionary </td>
        <td align=center>  </td>
    </tr>
        <tr><td>contains: </td>
    <td colspan=4>
        <table border=1 cellpadding=2>
        <tr>
        <th class="head">name</th>
        <th class="head">description</th>
        <th class="head">returned</th>
        <th class="head">type</th>
        <th class="head">sample</th>
        </tr>

                <tr>
        <td> status </td>
        <td>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
        </tr>
                <tr>
        <td> kind </td>
        <td>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
        </tr>
                <tr>
        <td> spec </td>
        <td>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
        </tr>
                <tr>
        <td> apiVersion </td>
        <td>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
        </tr>
                <tr>
        <td> metadata </td>
        <td>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
        <td align=center>  </td>
        </tr>
        
        </table>
    </td></tr>

        
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
