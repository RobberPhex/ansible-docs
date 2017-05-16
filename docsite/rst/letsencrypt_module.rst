.. _letsencrypt:


letsencrypt - Create SSL certificates with Let's Encrypt
++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.2


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create and renew SSL certificates with Let's Encrypt. Let’s Encrypt is a free, automated, and open certificate authority (CA), run for the public’s benefit. For details see https://letsencrypt.org. The current implementation supports the http-01, tls-sni-02 and dns-01 challenges.
To use this module, it has to be executed at least twice. Either as two different tasks in the same run or during multiple runs.
Between these two tasks you have to fulfill the required steps for the choosen challenge by whatever means necessary. For http-01 that means creating the necessary challenge file on the destination webserver. For dns-01 the necessary dns record has to be created. tls-sni-02 requires you to create a SSL certificate with the appropriate subjectAlternativeNames. It is *not* the responsibility of this module to perform these steps.
For details on how to fulfill these challenges, you might have to read through https://tools.ietf.org/html/draft-ietf-acme-acme-02#section-7
Although the defaults are choosen so that the module can be used with the Let's Encrypt CA, the module can be used with any service using the ACME protocol.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * openssl


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
    <td>account_email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The email address associated with this account.</div><div>It will be used for certificate expiration warnings.</div></td></tr>
            <tr>
    <td>account_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>File containing the the Let's Encrypt account RSA key.</div><div>Can be created with <code>openssl rsa ...</code>.</div></td></tr>
            <tr>
    <td>acme_directory<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https://acme-staging.api.letsencrypt.org/directory</td>
        <td><ul></ul></td>
        <td><div>The ACME directory to use. This is the entry point URL to access CA server API.</div><div>For safety reasons the default is set to the Let's Encrypt staging server. This will create technically correct, but untrusted certificates.</div></td></tr>
            <tr>
    <td>agreement<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https://letsencrypt.org/documents/LE-SA-v1.1.1-August-1-2016.pdf</td>
        <td><ul></ul></td>
        <td><div>URI to a terms of service document you agree to when using the ACME service at <code>acme_directory</code>.</div></td></tr>
            <tr>
    <td>challenge<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>http-01</td>
        <td><ul><li>http-01</li><li>dns-01</li><li>tls-sni-02</li></ul></td>
        <td><div>The challenge to be performed.</div></td></tr>
            <tr>
    <td>csr<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>File containing the CSR for the new certificate.</div><div>Can be created with <code>openssl csr ...</code>.</div><div>The CSR may contain multiple Subject Alternate Names, but each one will lead to an individual challenge that must be fulfilled for the CSR to be signed.</div></td></tr>
            <tr>
    <td>data<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The data to validate ongoing challenges.</div><div>The value that must be used here will be provided by a previous use of this module.</div></td></tr>
            <tr>
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The destination file for the certificate.</div></td></tr>
            <tr>
    <td>remaining_days<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td><ul></ul></td>
        <td><div>The number of days the certificate must have left being valid before it will be renewed.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - letsencrypt:
        account_key: /etc/pki/cert/private/account.key
        csr: /etc/pki/cert/csr/sample.com.csr
        dest: /etc/httpd/ssl/sample.com.crt
      register: sample_com_challenge
    
    # perform the necessary steps to fulfill the challenge
    # for example:
    #
    # - copy:
    #     dest: /var/www/html/{{ sample_com_challenge['challenge_data']['sample.com']['http-01']['resource'] }}
    #     content: "{{ sample_com_challenge['challenge_data']['sample.com']['http-01']['resource_value'] }}"
    #     when: sample_com_challenge|changed
    
    - letsencrypt:
        account_key: /etc/pki/cert/private/account.key
        csr: /etc/pki/cert/csr/sample.com.csr
        dest: /etc/httpd/ssl/sample.com.crt
        data: "{{ sample_com_challenge }}"

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
        <td> challenge_data </td>
        <td> per domain / challenge type challenge data </td>
        <td align=center> changed </td>
        <td align=center> dictionary </td>
        <td align=center>  </td>
    </tr>
        <tr><td>contains: </td>
    <td colspan=4>
        <table border=1 cellpadding=2>
        <tr>
        <th class="head">name</th>
        <th class="head">description</th>
        <th class="head">returned</th>
        <th class="head">type</th>
        <th class="head">sample</th>
        </tr>

                <tr>
        <td> resource </td>
        <td> the challenge resource that must be created for validation </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> .well-known/acme-challenge/evaGxfADs6pSRb2LAv9IZf17Dt3juxGJ-PCt92wr-oA </td>
        </tr>
                <tr>
        <td> resource_value </td>
        <td> the value the resource has to produce for the validation </td>
        <td align=center> changed </td>
        <td align=center> string </td>
        <td align=center> IlirfxKKXA...17Dt3juxGJ-PCt92wr-oA </td>
        </tr>
        
        </table>
    </td></tr>

            <tr>
        <td> cert_days </td>
        <td> the number of days the certificate remains valid. </td>
        <td align=center> success </td>
        <td align=center>  </td>
        <td align=center>  </td>
    </tr>
            <tr>
        <td> authorizations </td>
        <td> ACME authorization data. </td>
        <td align=center> changed </td>
        <td align=center> list </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

