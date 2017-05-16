.. _win_iis_webbinding:


win_iis_webbinding - Configures a IIS Web site.
+++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Creates, Removes and configures a binding to an existing IIS Web site




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
                <tr><td>certificate_hash<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Certificate hash for the SSL binding. The certificate hash is the unique identifier for the certificate.</div>        </td></tr>
                <tr><td>certificate_store_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>My</td>
        <td></td>
        <td><div>Name of the certificate store where the certificate for the binding is located.</div>        </td></tr>
                <tr><td>host_header<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The host header to bind to / use for the new site.</div>        </td></tr>
                <tr><td>ip<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The IP address to bind to / use for the new site.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Names of web site</div>        </td></tr>
                <tr><td>port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The port to bind to / use for the new site.</div>        </td></tr>
                <tr><td>protocol<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The protocol to be used for the Web binding (usually HTTP, HTTPS, or FTP).</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State of the binding</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Return binding information for an existing host
      win_iis_webbinding:
        name: Default Web Site
    
    - name: Return the HTTPS binding information for an existing host
      win_iis_webbinding:
        name: Default Web Site
        protocol: https
    
    - name: Add a HTTP binding on port 9090
      win_iis_webbinding:
        name: Default Web Site
        port: 9090
        state: present
    
    - name: Remove the HTTP binding on port 9090
      win_iis_webbinding:
        name: Default Web Site
        port: 9090
        state: absent
    
    - name: Add a HTTPS binding
      win_iis_webbinding:
        name: Default Web Site
        protocol: https
        state: present
    
    - name: Add a HTTPS binding and select certificate to use
      win_iis_webbinding:
        name: Default Web Site
        protocol: https
        certificate_hash: B0D0FA8408FC67B230338FCA584D03792DA73F4C
        state: present
    
    - name: Website https biding to specific port
      win_iis_webbinding:
        name: Default Web Site
        protocol: https
        port: 443
        certificate_hash: D1A3AF8988FD32D1A3AF8988FD323792DA73F4C
        state: present





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
