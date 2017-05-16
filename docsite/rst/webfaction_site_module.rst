.. _webfaction_site:


webfaction_site - Add or remove a website on a Webfaction host
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Add or remove a website on a Webfaction host.  Further documentation at http://github.com/quentinsf/ansible-webfaction.




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
    <td>host<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The webfaction host on which the site should be created.</div></td></tr>
            <tr>
    <td>https<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>false</td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td><div>Whether or not to use HTTPS</div></td></tr>
            <tr>
    <td>login_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The webfaction account to use</div></td></tr>
            <tr>
    <td>login_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The webfaction password to use</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the website</div></td></tr>
            <tr>
    <td>site_apps<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A mapping of URLs to apps</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the website should exist</div></td></tr>
            <tr>
    <td>subdomains<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of subdomains associated with this site.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

      - name: create website
        webfaction_site:
          name: testsite1
          state: present
          host: myhost.webfaction.com 
          subdomains: 
            - 'testsite1.my_domain.org'
          site_apps:
            - ['testapp1', '/']
          https: no
          login_name: "{{webfaction_user}}"
          login_password: "{{webfaction_passwd}}"


Notes
-----

.. note:: Sadly, you *do* need to know your webfaction hostname for the ``host`` parameter.  But at least, unlike the API, you don't need to know the IP address - you can use a DNS name.
.. note:: If a site of the same name exists in the account but on a different host, the operation will exit.
.. note:: You can run playbooks that use this on a local machine, or on a Webfaction host, or elsewhere, since the scripts use the remote webfaction API - the location is not important. However, running them on multiple hosts *simultaneously* is best avoided. If you don't specify *localhost* as your host, you may want to add ``serial: 1`` to the plays.
.. note:: See `the webfaction API <http://docs.webfaction.com/xmlrpc-api/>`_ for more info.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

