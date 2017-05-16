.. _newrelic_deployment:


newrelic_deployment - Notify newrelic about app deployments
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Notify newrelic about app deployments (see https://docs.newrelic.com/docs/apm/new-relic-apm/maintenance/deployment-notifications#api)




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
    <td>app_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>(one of app_name or application_id are required) The value of app_name in the newrelic.yml file used by the application</div></td></tr>
            <tr>
    <td>application_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>(one of app_name or application_id are required) The application id, found in the URL when viewing the application in RPM</div></td></tr>
            <tr>
    <td>appname<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of the application</div></td></tr>
            <tr>
    <td>changelog<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of changes for this deployment</div></td></tr>
            <tr>
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Text annotation for the deployment - notes for you</div></td></tr>
            <tr>
    <td>environment<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The environment for this deployment</div></td></tr>
            <tr>
    <td>revision<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A revision number (e.g., git commit SHA)</div></td></tr>
            <tr>
    <td>token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>API token, to place in the x-api-key header.</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the user/process that triggered this deployment</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5.1)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - newrelic_deployment: token=AAAAAA
                           app_name=myapp
                           user='ansible deployment'
                           revision=1.0




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

