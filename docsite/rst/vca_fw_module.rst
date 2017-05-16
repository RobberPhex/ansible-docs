.. _vca_fw:


vca_fw - add remove firewall rules in a gateway  in a vca
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Adds or removes firewall rules from a gateway in a vca environment




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
    <td>api_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5.7</td>
        <td><ul></ul></td>
        <td><div>The api version to be used with the vca</div></td></tr>
            <tr>
    <td>fw_rules<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of firewall rules to be added to the gateway, Please see examples on valid entries</div></td></tr>
            <tr>
    <td>gateway_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>gateway</td>
        <td><ul></ul></td>
        <td><div>The name of the gateway of the vdc where the rule should be added</div></td></tr>
            <tr>
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The authentication host to be used when service type  is vcd.</div></td></tr>
            <tr>
    <td>instance_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The instance id in a vchs environment to be used for creating the vapp</div></td></tr>
            <tr>
    <td>org<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The org to login to for creating vapp, mostly set when the service_type is vdc.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The vca password, if not set the environment variable VCA_PASS is checked for the password</div></td></tr>
            <tr>
    <td>service_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>vca</td>
        <td><ul><li>vca</li><li>vchs</li><li>vcd</li></ul></td>
        <td><div>The type of service we are authenticating against</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>if the object should be added or removed</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The vca username or email address, if not set the environment variable VCA_USER is checked for the username.</div></td></tr>
            <tr>
    <td>vdc_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The name of the vdc where the gateway is located.</div></td></tr>
            <tr>
    <td>verify_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>If the certificates of the authentication is to be verified</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    #Add a set of firewall rules
    
    - hosts: localhost
      connection: local
      tasks:
       - vca_fw:
           instance_id: 'b15ff1e5-1024-4f55-889f-ea0209726282'
           vdc_name: 'benz_ansible'
           state: 'absent'
           fw_rules:
             - description: "ben testing"
               source_ip: "Any"
               dest_ip: 192.168.2.11
             - description: "ben testing 2"
               source_ip: 192.168.2.100
               source_port: "Any"
               dest_port: "22"
               dest_ip: 192.168.2.13
               is_enable: "true"
               enable_logging: "false"
               protocol: "Tcp"
               policy: "allow"
    




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

