.. _webfaction_mailbox:


webfaction_mailbox - Add or remove mailboxes on Webfaction
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Add or remove mailboxes on a Webfaction account. Further documentation at http://github.com/quentinsf/ansible-webfaction.




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
    <td>mailbox_name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the mailbox</div></td></tr>
            <tr>
    <td>mailbox_password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The password for the mailbox</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>Whether the mailbox should exist</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

      - name: Create a mailbox
        webfaction_mailbox:
          mailbox_name="mybox"
          mailbox_password="myboxpw"
          state=present
          login_name={{webfaction_user}}
          login_password={{webfaction_passwd}}


Notes
-----

.. note:: You can run playbooks that use this on a local machine, or on a Webfaction host, or elsewhere, since the scripts use the remote webfaction API - the location is not important. However, running them on multiple hosts *simultaneously* is best avoided. If you don't specify *localhost* as your host, you may want to add ``serial: 1`` to the plays.
.. note:: See `the webfaction API <http://docs.webfaction.com/xmlrpc-api/>`_ for more info.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

