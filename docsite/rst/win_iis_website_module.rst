.. _win_iis_website:


win_iis_website - Configures a IIS Web site.
++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Creates, Removes and configures a IIS Web site




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
    <td>application_pool<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The application pool in which the new site executes.</div></td></tr>
            <tr>
    <td>hostname<br/><div style="font-size: small;"></div></td>
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
    <td>parameters<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Custom site Parameters from string where properties are seperated by a pipe and property name/values by colon Ex. "foo:1|bar:2"</div></td></tr>
            <tr>
    <td>physical_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The physical path on the remote host to use for the new site. The specified folder must already exist.</div></td></tr>
            <tr>
    <td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The port to bind to / use for the new site.</div></td></tr>
            <tr>
    <td>ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Enables HTTPS binding on the site..</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>started</li><li>restarted</li><li>stopped</li><li>absent</li></ul></td>
        <td><div>State of the web site</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # This return information about an existing host
    $ ansible -i vagrant-inventory -m win_iis_website -a "name='Default Web Site'" window
    host | success >> {
        "changed": false,
        "site": {
            "ApplicationPool": "DefaultAppPool",
            "Bindings": [
                "*:80:"
            ],
            "ID": 1,
            "Name": "Default Web Site",
            "PhysicalPath": "%SystemDrive%\inetpub\wwwroot",
            "State": "Stopped"
        }
    }
    
    # This stops an existing site.
    $ ansible -i hosts -m win_iis_website -a "name='Default Web Site' state=stopped" host
    
    # This creates a new site.
    $ ansible -i hosts -m win_iis_website -a "name=acme physical_path=c:\sites\acme" host
    
    # Change logfile .
    $ ansible -i hosts -m win_iis_website -a "name=acme physical_path=c:\sites\acme" host
    
    
    # Playbook example
    ---
    
    - name: Acme IIS site
      win_iis_website:
        name: "Acme"
        state: started
        port: 80
        ip: 127.0.0.1
        hostname: acme.local
        application_pool: "acme"
        physical_path: 'c:\sites\acme'
        parameters: 'logfile.directory:c:\sites\logs'
      register: website
    




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

