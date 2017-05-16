.. _ipa_host:


ipa_host - Manage FreeIPA host
++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add, modify and delete an IPA host using IPA API




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
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A description of this host.</div>        </td></tr>
                <tr><td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Force host name even if not in DNS.</div>        </td></tr>
                <tr><td>fqdn<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Full qualified domain name.</div><div>Can not be changed as it is the unique identifier.</div></br>
    <div style="font-size: small;">aliases: name<div>        </td></tr>
                <tr><td>ip_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Add the host to DNS with this IP address.</div>        </td></tr>
                <tr><td>ipa_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ipa.example.com</td>
        <td></td>
        <td><div>IP or hostname of IPA server</div>        </td></tr>
                <tr><td>ipa_pass<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password of administrative user</div>        </td></tr>
                <tr><td>ipa_port<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>443</td>
        <td></td>
        <td><div>Port of IPA server</div>        </td></tr>
                <tr><td>ipa_prot<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https</td>
        <td><ul><li>http</li><li>https</li></ul></td>
        <td><div>Protocol used by IPA server</div>        </td></tr>
                <tr><td>ipa_user<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>admin</td>
        <td></td>
        <td><div>Administrative account used on IPA server</div>        </td></tr>
                <tr><td>mac_address<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of Hardware MAC address(es) off this host.</div><div>If option is omitted MAC addresses will not be checked or changed.</div><div>If an empty list is passed all assigned MAC addresses will be removed.</div><div>MAC addresses that are already assigned but not passed will be removed.</div></br>
    <div style="font-size: small;">aliases: macaddress<div>        </td></tr>
                <tr><td>ns_hardware_platform<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Host hardware platform (e.g. "Lenovo T61")</div></br>
    <div style="font-size: small;">aliases: nshardwareplatform<div>        </td></tr>
                <tr><td>ns_host_location<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Host location (e.g. "Lab 2")</div></br>
    <div style="font-size: small;">aliases: nshostlocation<div>        </td></tr>
                <tr><td>ns_os_version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Host operating system and version (e.g. "Fedora 9")</div></br>
    <div style="font-size: small;">aliases: nsosversion<div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>disabled</li></ul></td>
        <td><div>State to ensure</div>        </td></tr>
                <tr><td>user_certificate<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of Base-64 encoded server certificates.</div><div>If option is omitted certificates will not be checked or changed.</div><div>If an emtpy list is passed all assigned certificates will be removed.</div><div>Certificates already assigned but not passed will be removed.</div></br>
    <div style="font-size: small;">aliases: usercertificate<div>        </td></tr>
                <tr><td>validate_certs<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>This only applies if <code>ipa_prot</code> is <em>https</em>.</div><div>If set to <code>no</code>, the SSL certificates will not be validated.</div><div>This should only set to <code>no</code> used on personally controlled sites using self-signed certificates.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Ensure host is present
    - ipa_host:
        name: host01.example.com
        description: Example host
        ip_address: 192.168.0.123
        ns_host_location: Lab
        ns_os_version: CentOS 7
        ns_hardware_platform: Lenovo T61
        mac_address:
        - "08:00:27:E3:B1:2D"
        - "52:54:00:BD:97:1E"
        state: present
        ipa_host: ipa.example.com
        ipa_user: admin
        ipa_pass: topsecret
    
    # Ensure host is disabled
    - ipa_host:
        name: host01.example.com
        state: disabled
        ipa_host: ipa.example.com
        ipa_user: admin
        ipa_pass: topsecret
    
    # Ensure that all user certificates are removed
    - ipa_host:
        name: host01.example.com
        user_certificate: []
        ipa_host: ipa.example.com
        ipa_user: admin
        ipa_pass: topsecret
    
    # Ensure host is absent
    - ipa_host:
        name: host01.example.com
        state: absent
        ipa_host: ipa.example.com
        ipa_user: admin
        ipa_pass: topsecret

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> host </td>
        <td> Host as returned by IPA API. </td>
        <td align=center> always </td>
        <td align=center> dict </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> host_diff </td>
        <td> List of options that differ and would be changed </td>
        <td align=center> if check mode and a difference is found </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>




Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
