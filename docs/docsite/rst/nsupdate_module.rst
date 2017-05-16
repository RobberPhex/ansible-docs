.. _nsupdate:


nsupdate - Manage DNS records.
++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create, update and remove DNS records using DDNS updates
* DDNS works well with both bind and Microsoft DNS (see https://technet.microsoft.com/en-us/library/cc961412.aspx)


Requirements (on host that executes module)
-------------------------------------------

  * dnspython


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
                <tr><td>key_algorithm<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>hmac-md5</td>
        <td><ul><li>HMAC-MD5.SIG-ALG.REG.INT</li><li>hmac-md5</li><li>hmac-sha1</li><li>hmac-sha224</li><li>hmac-sha256</li><li>hamc-sha384</li><li>hmac-sha512</li></ul></td>
        <td><div>Specify key algorithm used by <code>key_secret</code>.</div>        </td></tr>
                <tr><td>key_name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Use TSIG key name to authenticate against DNS <code>server</code></div>        </td></tr>
                <tr><td>key_secret<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Use TSIG key secret, associated with <code>key_name</code>, to authenticate against <code>server</code></div>        </td></tr>
                <tr><td>record<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Sets the DNS record to modify.</div>        </td></tr>
                <tr><td>server<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Apply DNS modification on this server.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Manage DNS record.</div>        </td></tr>
                <tr><td>ttl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>3600</td>
        <td></td>
        <td><div>Sets the record TTL.</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>A</td>
        <td></td>
        <td><div>Sets the record type.</div>        </td></tr>
                <tr><td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td></td>
        <td><div>Sets the record value.</div>        </td></tr>
                <tr><td>zone<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>DNS record will be modified on this <code>zone</code>.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Add or modify ansible.example.org A to 192.168.1.1"
      nsupdate:
        key_name: "nsupdate"
        key_secret: "+bFQtBCta7j2vWkjPkAFtgA=="
        server: "10.1.1.1"
        zone: "example.org"
        record: "ansible"
        value: "192.168.1.1"
    
    - name: Remove puppet.example.org CNAME
      nsupdate:
        key_name: "nsupdate"
        key_secret: "+bFQtBCta7j2vWkjPkAFtgA=="
        server: "10.1.1.1"
        zone: "example.org"
        record: "puppet"
        type: "CNAME"
        state: absent

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
        <td> zone </td>
        <td> DNS record zone </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> example.org. </td>
    </tr>
            <tr>
        <td> changed </td>
        <td> If module has modified record </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> value </td>
        <td> DNS record value </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 192.168.1.1 </td>
    </tr>
            <tr>
        <td> record </td>
        <td> DNS record </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> ansible </td>
    </tr>
            <tr>
        <td> dns_rc </td>
        <td> dnspython return code </td>
        <td align=center> always </td>
        <td align=center> int </td>
        <td align=center> 4 </td>
    </tr>
            <tr>
        <td> ttl </td>
        <td> DNS record TTL </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 86400 </td>
    </tr>
            <tr>
        <td> type </td>
        <td> DNS record type </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> CNAME </td>
    </tr>
            <tr>
        <td> dns_rc_str </td>
        <td> dnspython return code (string representation) </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> REFUSED </td>
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
