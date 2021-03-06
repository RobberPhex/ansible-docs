.. _typetalk:


typetalk - Send a message to typetalk
+++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Send a message to typetalk using typetalk API ( http://developers.typetalk.in/ )

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
    <td>client_id</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>OAuth2 client ID</td>
    </tr>
            <tr>
    <td>client_secret</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>OAuth2 client secret</td>
    </tr>
            <tr>
    <td>msg</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>message body</td>
    </tr>
            <tr>
    <td>topic</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>topic id to post message</td>
    </tr>
        </table>


.. note:: Requires urllib


.. note:: Requires urllib2


.. note:: Requires json


Examples
--------

.. raw:: html

    <br/>


::

    - typetalk: client_id=12345 client_secret=12345 topic=1 msg="install completed"



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

