.. _webfaction_app:


webfaction_app - Add or remove applications on a Webfaction host
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Add or remove applications on a Webfaction host.  Further documentation at http://github.com/quentinsf/ansible-webfaction.




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
                <tr><td>autostart<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td></td>
        <td><div>Whether the app should restart with an autostart.cgi script</div>        </td></tr>
                <tr><td>extra_info<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Any extra parameters required by the app</div>        </td></tr>
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
                <tr><td>machine<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The machine name to use (optional for accounts with only one machine)</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The name of the application</div>        </td></tr>
                <tr><td>port_open<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>IF the port should be opened</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the application should exist</div>        </td></tr>
                <tr><td>type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The type of application to create. See the Webfaction docs at http://docs.webfaction.com/xmlrpc-api/apps.html for a list.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

      - name: Create a test app
        webfaction_app:
          name="my_wsgi_app1"
          state=present
          type=mod_wsgi35-python27
          login_name={{webfaction_user}}
          login_password={{webfaction_passwd}}
          machine={{webfaction_machine}}


Notes
-----

.. note::
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
