.. _jenkins_job:


jenkins_job - Manage jenkins jobs
+++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage Jenkins jobs by using Jenkins REST API.


Requirements (on host that executes module)
-------------------------------------------

  * python-jenkins >= 0.4.12
  * lxml >= 3.3.3


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
                <tr><td>config<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>config in XML format.</div><div>Required if job does not yet exist.</div><div>Mututally exclusive with <code>enabled</code>.</div><div>Considered if <code>state=present</code>.</div>        </td></tr>
                <tr><td>enabled<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Whether the job should be enabled or disabled.</div><div>Mututally exclusive with <code>config</code>.</div><div>Considered if <code>state=present</code>.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Name of the Jenkins job.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password to authenticate with the Jenkins server.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Attribute that specifies if the job has to be created or deleted.</div>        </td></tr>
                <tr><td>token<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>API token used to authenticate alternatively to password.</div>        </td></tr>
                <tr><td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>http://localhost:8080</td>
        <td></td>
        <td><div>Url where the Jenkins server is accessible.</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>User to authenticate with the Jenkins server.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a jenkins job using basic authentication
    - jenkins_job:
        config: "{{ lookup('file', 'templates/test.xml') }}"
        name: test
        password: admin
        url: http://localhost:8080
        user: admin
    
    # Create a jenkins job using the token
    - jenkins_job:
        config: "{{ lookup('template', 'templates/test.xml.j2') }}"
        name: test
        token: asdfasfasfasdfasdfadfasfasdfasdfc
        url: http://localhost:8080
        user: admin
    
    # Delete a jenkins job using basic authentication
    - jenkins_job:
        name: test
        password: admin
        state: absent
        url: http://localhost:8080
        user: admin
    
    # Delete a jenkins job using the token
    - jenkins_job:
        name: test
        token: asdfasfasfasdfasdfadfasfasdfasdfc
        state: absent
        url: http://localhost:8080
        user: admin
    
    # Disable a jenkins job using basic authentication
    - jenkins_job:
        name: test
        password: admin
        enabled: False
        url: http://localhost:8080
        user: admin
    
    # Disable a jenkins job using the token
    - jenkins_job:
        name: test
        token: asdfasfasfasdfasdfadfasfasdfasdfc
        enabled: False
        url: http://localhost:8080
        user: admin

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
        <td> Url to connect to the Jenkins server. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> https://jenkins.mydomain.com </td>
    </tr>
            <tr>
        <td> state </td>
        <td> State of the jenkins job. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> present </td>
    </tr>
            <tr>
        <td> enabled </td>
        <td> Whether the jenkins job is enabled or not. </td>
        <td align=center> success </td>
        <td align=center> bool </td>
        <td align=center> True </td>
    </tr>
            <tr>
        <td> name </td>
        <td> Name of the jenkins job. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> test-job </td>
    </tr>
            <tr>
        <td> user </td>
        <td> User used for authentication. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> admin </td>
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
