.. _win_iis_webbinding:


win_iis_webbinding - Configures a IIS Web site.
+++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Creates, Removes and configures a binding to an existing IIS Web site




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
    <td>certificate_hash<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Certificate hash for the SSL binding. The certificate hash is the unique identifier for the certificate.</div></td></tr>
            <tr>
    <td>certificate_store_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>My</td>
        <td><ul></ul></td>
        <td><div>Name of the certificate store where the certificate for the binding is located.</div></td></tr>
            <tr>
    <td>host_header<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The host header to bind to / use for the new site.</div></td></tr>
            <tr>
    <td>ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The IP address to bind to / use for the new site.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Names of web site</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The port to bind to / use for the new site.</div></td></tr>
            <tr>
    <td>protocol<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The protocol to be used for the Web binding (usually HTTP, HTTPS, or FTP).</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the binding</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # This will return binding information for an existing host
    $ ansible -i vagrant-inventory -m win_iis_webbinding -a "name='Default Web Site'" windows
    host | success >> {
        "added": [],
        "changed": false,
        "matched": [
            {
                "bindingInformation": "*:80:",
                "certificateHash": "",
                "certificateStoreName": "",
                "isDsMapperEnabled": false,
                "protocol": "http",
                "sslFlags": 0
            }
        ],
        "parameters": {
            "Name": "Default Web Site"
        },
        "removed": []
    }
    
    # This will return the HTTPS binding information for an existing host
    $ ansible -i vagrant-inventory -m win_iis_webbinding -a "name='Default Web Site' protocol=https" windows
    
    # This will return the HTTPS binding information for an existing host
    $ ansible -i vagrant-inventory -m win_iis_webbinding -a "name='Default Web Site' port:9090 state=present" windows
    
    # This will add a HTTP binding on port 9090
    $ ansible -i vagrant-inventory -m win_iis_webbinding -a "name='Default Web Site' port=9090 state=present" windows
    
    # This will remove the HTTP binding on port 9090
    $ ansible -i vagrant-inventory -m win_iis_webbinding -a "name='Default Web Site' port=9090 state=present" windows
    
    # This will add a HTTPS binding
    $ ansible -i vagrant-inventory -m win_iis_webbinding -a "name='Default Web Site' protocol=https state=present" windows
    
    # This will add a HTTPS binding and select certificate to use
    # ansible -i vagrant-inventory -m win_iis_webbinding -a "name='Default Web Site' protocol=https certificate_hash= B0D0FA8408FC67B230338FCA584D03792DA73F4C" windows
    
    
    # Playbook example
    ---
    
    - name: Website http/https bidings
      win_iis_webbinding:
        name: "Default Web Site"
        protocol: https
        port: 443
        certificate_hash: "D1A3AF8988FD32D1A3AF8988FD323792DA73F4C"
        state: present
      when: monitor_use_https
    




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

