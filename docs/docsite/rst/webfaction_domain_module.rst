.. _webfaction_domain:


webfaction_domain - Add or remove domains and subdomains on Webfaction
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add or remove domains or subdomains on a Webfaction host. Further documentation at http://github.com/quentinsf/ansible-webfaction.




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
                <tr><td>login_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The webfaction account to use</div>        </td></tr>
                <tr><td>login_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The webfaction password to use</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the domain</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the domain should exist</div>        </td></tr>
                <tr><td>subdomains<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Any subdomains to create.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

      - name: Create a test domain
        webfaction_domain:
          name: mydomain.com
          state: present
          subdomains:
           - www
           - blog
          login_name: "{{webfaction_user}}"
          login_password: "{{webfaction_passwd}}"
    
      - name: Delete test domain and any subdomains
        webfaction_domain:
          name: mydomain.com
          state: absent
          login_name: "{{webfaction_user}}"
          login_password: "{{webfaction_passwd}}"
    


Notes
-----

.. note::
    - If you are *deleting* domains by using ``state=absent``, then note that if you specify subdomains, just those particular subdomains will be deleted.  If you don't specify subdomains, the domain will be deleted.
    - You can run playbooks that use this on a local machine, or on a Webfaction host, or elsewhere, since the scripts use the remote webfaction API - the location is not important. However, running them on multiple hosts *simultaneously* is best avoided. If you don't specify *localhost* as your host, you may want to add ``serial: 1`` to the plays.
    - See `the webfaction API <http://docs.webfaction.com/xmlrpc-api/>`_ for more info.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
