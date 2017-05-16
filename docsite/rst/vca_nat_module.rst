.. _vca_nat:


vca_nat - add remove nat rules in a gateway  in a vca
+++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Adds or removes nat rules from a gateway in a vca environment




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
    <td>nat_rules<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of rules to be added to the gateway, Please see examples on valid entries</div></td></tr>
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
        <td><div>The vca password, if not set the environment variable VCA_PASS is checked for the password</div></br>
        <div style="font-size: small;">aliases: pass, pwd<div></td></tr>
            <tr>
    <td>purge_rules<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If set to true, it will delete all rules in the gateway that are not given as paramter to this module.</div></td></tr>
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
        <td><div>The vca username or email address, if not set the environment variable VCA_USER is checked for the username.</div></br>
        <div style="font-size: small;">aliases: user<div></td></tr>
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

    
    #An example for a source nat
    
    - hosts: localhost
      connection: local
      tasks:
       - vca_nat:
           instance_id: 'b15ff1e5-1024-4f55-889f-ea0209726282'
           vdc_name: 'benz_ansible'
           state: 'present'
           nat_rules:
             - rule_type: SNAT
               original_ip: 192.168.2.10
               translated_ip: 107.189.95.208
    
    #example for a DNAT
    - hosts: localhost
      connection: local
      tasks:
       - vca_nat:
           instance_id: 'b15ff1e5-1024-4f55-889f-ea0209726282'
           vdc_name: 'benz_ansible'
           state: 'present'
           nat_rules:
             - rule_type: DNAT
               original_ip: 107.189.95.208
               original_port: 22
               translated_ip: 192.168.2.10
               translated_port: 22
    




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

