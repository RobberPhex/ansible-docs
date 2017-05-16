.. _honeybadger_deployment:


honeybadger_deployment - Notify Honeybadger.io about app deployments
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Notify Honeybadger.io about app deployments (see http://docs.honeybadger.io/article/188-deployment-tracking)




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
    <td>environment<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The environment name, typically 'production', 'staging', etc.</div></td></tr>
            <tr>
    <td>repo<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>URL of the project repository</div></td></tr>
            <tr>
    <td>revision<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>A hash, number, tag, or other identifier showing what revision was deployed</div></td></tr>
            <tr>
    <td>token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>API token.</div></td></tr>
            <tr>
    <td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https://api.honeybadger.io/v1/deploys</td>
        <td><ul></ul></td>
        <td><div>Optional URL to submit the notification to.</div></td></tr>
            <tr>
    <td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The username of the person doing the deployment</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates for the target url will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - honeybadger_deployment: token=AAAAAA
                              environment='staging'
                              user='ansible'
                              revision=b6826b8
                              repo=git@github.com:user/repo.git




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

