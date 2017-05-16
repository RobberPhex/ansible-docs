.. _bigpanda:


bigpanda - Notify BigPanda about deployments
++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.8


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Notify BigPanda when deployments start and end (successfully or not). Returns a deployment object containing all the parameters for future module calls.




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
    <td>component<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the component being deployed. Ex: billing</div></td></tr>
            <tr>
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Free text description of the deployment.</div></td></tr>
            <tr>
    <td>env<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The environment name, typically 'production', 'staging', etc.</div></td></tr>
            <tr>
    <td>hosts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>machine's hostname</td>
        <td><ul></ul></td>
        <td><div>Name of affected host name. Can be a list.</div></td></tr>
            <tr>
    <td>owner<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The person responsible for the deployment.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>started</li><li>finished</li><li>failed</li></ul></td>
        <td><div>State of the deployment.</div></td></tr>
            <tr>
    <td>token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>API token.</div></td></tr>
            <tr>
    <td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https://api.bigpanda.io</td>
        <td><ul></ul></td>
        <td><div>Base URL of the API server.</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates for the target url will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div></td></tr>
            <tr>
    <td>version<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The deployment version.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - bigpanda: component=myapp version=1.3 token={{ bigpanda_token }} state=started
    ...
    - bigpanda: component=myapp version=1.3 token={{ bigpanda_token }} state=finished
    
    or using a deployment object:
    - bigpanda: component=myapp version=1.3 token={{ bigpanda_token }} state=started
      register: deployment
    
    - bigpanda: state=finished
      args: deployment
    
    If outside servers aren't reachable from your machine, use local_action and pass the hostname:
    - local_action: bigpanda component=myapp version=1.3 hosts={{ansible_hostname}} token={{ bigpanda_token }} state=started
      register: deployment
    ...
    - local_action: bigpanda state=finished
      args: deployment




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

