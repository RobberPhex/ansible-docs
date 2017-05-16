.. _airbrake_deployment:


airbrake_deployment - Notify airbrake about app deployments
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Notify airbrake about app deployments (see http://help.airbrake.io/kb/api-2/deploy-tracking)




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
                <tr><td>environment<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The airbrake environment name, typically 'production', 'staging', etc.</div>        </td></tr>
                <tr><td>repo<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>URL of the project repository</div>        </td></tr>
                <tr><td>revision<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A hash, number, tag, or other identifier showing what revision was deployed</div>        </td></tr>
                <tr><td>token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>API token.</div>        </td></tr>
                <tr><td>url<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>https://airbrake.io/deploys.txt</td>
        <td></td>
        <td><div>Optional URL to submit the notification to. Use to send notifications to Airbrake-compliant tools like Errbit.</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The username of the person doing the deployment</div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates for the target url will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - airbrake_deployment:
        token: AAAAAA
        environment: staging
        user: ansible
        revision: '4.2'





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
