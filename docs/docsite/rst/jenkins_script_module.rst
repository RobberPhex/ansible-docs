.. _jenkins_script:


jenkins_script - Executes a groovy script in the jenkins instance
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* The ``jenkins_script`` module takes a script plus a dict of values to use within the script and returns the result of the script being run.




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
                <tr><td>args<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A dict of key-value pairs used in formatting the script.</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The password to connect to the jenkins server with.</div>        </td></tr>
                <tr><td>script<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The groovy script to be executed. This gets passed as a string Template if args is defined.</div>        </td></tr>
                <tr><td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>http://localhost:8080</td>
        <td></td>
        <td><div>The jenkins server to execute the script against. The default is a local jenkins instance that is not being proxied through a webserver.</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The username to connect to the jenkins server with.</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>If set to <code>no</code>, the SSL certificates will not be validated. This should only set to <code>no</code> used on personally controlled sites using self-signed certificates as it avoids verifying the source site.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Obtaining a list of plugins
      jenkins_script:
        script: 'println(Jenkins.instance.pluginManager.plugins)'
        user: admin
        password: admin
    
    - name: Setting master using a variable to hold a more complicate script
      vars:
        setmaster_mode: |
            import jenkins.model.*
            instance = Jenkins.getInstance()
            instance.setMode(${jenkins_mode})
            instance.save()
    
    - name: use the variable as the script
      jenkins_script:
        script: "{{ setmaster_mode }}"
        args:
          jenkins_mode: Node.Mode.EXCLUSIVE
    
    - name: interacting with an untrusted HTTPS connection
      jenkins_script:
        script: "println(Jenkins.instance.pluginManager.plugins)"
        user: admin
        password: admin
        url: https://localhost
        validate_certs: no

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
        <td> output </td>
        <td> Result of script </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> Result: true </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Since the script can do anything this does not report on changes. Knowing the script is being run it's important to set changed_when for the ansible output to be clear on any alterations made.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
