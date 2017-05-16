.. _proxmox_template:


proxmox_template - management of OS templates in Proxmox VE cluster
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

allows you to upload/delete templates in Proxmox VE cluster


Requirements (on host that executes module)
-------------------------------------------

  * proxmoxer
  * requests


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
    <td>api_host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the host of the Proxmox VE cluster</div></td></tr>
            <tr>
    <td>api_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the password to authenticate with</div><div>you can use PROXMOX_PASSWORD environment variable</div></td></tr>
            <tr>
    <td>api_user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the user to authenticate with</div></td></tr>
            <tr>
    <td>content_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>vztmpl</td>
        <td><ul><li>vztmpl</li><li>iso</li></ul></td>
        <td><div>content type</div><div>required only for <code>state=present</code></div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>can be used only with <code>state=present</code>, exists template will be overwritten</div></td></tr>
            <tr>
    <td>node<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Proxmox VE node, when you will operate with template</div></td></tr>
            <tr>
    <td>src<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>path to uploaded file</div><div>required only for <code>state=present</code></div></br>
        <div style="font-size: small;">aliases: path<div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Indicate desired state of the template</div></td></tr>
            <tr>
    <td>storage<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>local</td>
        <td><ul></ul></td>
        <td><div>target storage</div></td></tr>
            <tr>
    <td>template<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the template name</div><div>required only for states <code>absent</code>, <code>info</code></div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td><div>timeout for operations</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>enable / disable https certificate verification</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Upload new openvz template with minimal options
    - proxmox_template: node='uk-mc02' api_user='root@pam' api_password='1q2w3e' api_host='node1' src='~/ubuntu-14.04-x86_64.tar.gz'
    
    # Upload new openvz template with minimal options use environment PROXMOX_PASSWORD variable(you should export it before)
    - proxmox_template: node='uk-mc02' api_user='root@pam' api_host='node1' src='~/ubuntu-14.04-x86_64.tar.gz'
    
    # Upload new openvz template with all options and force overwrite
    - proxmox_template: node='uk-mc02' api_user='root@pam' api_password='1q2w3e' api_host='node1' storage='local' content_type='vztmpl' src='~/ubuntu-14.04-x86_64.tar.gz' force=yes
    
    # Delete template with minimal options
    - proxmox_template: node='uk-mc02' api_user='root@pam' api_password='1q2w3e' api_host='node1' template='ubuntu-14.04-x86_64.tar.gz' state=absent


Notes
-----

.. note:: Requires proxmoxer and requests modules on host. This modules can be installed with pip.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

