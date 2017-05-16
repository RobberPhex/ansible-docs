.. _campfire:


campfire - Send a message to Campfire
+++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

Send a message to Campfire.
Messages with newlines will result in a "Paste" message being sent.

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
    <td>msg</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The message body.</td>
    </tr>
            <tr>
    <td>notify</td>
    <td>no</td>
    <td></td>
        <td><ul><li>56k</li><li>bell</li><li>bezos</li><li>bueller</li><li>clowntown</li><li>cottoneyejoe</li><li>crickets</li><li>dadgummit</li><li>dangerzone</li><li>danielsan</li><li>deeper</li><li>drama</li><li>greatjob</li><li>greyjoy</li><li>guarantee</li><li>heygirl</li><li>horn</li><li>horror</li><li>inconceivable</li><li>live</li><li>loggins</li><li>makeitso</li><li>noooo</li><li>nyan</li><li>ohmy</li><li>ohyeah</li><li>pushit</li><li>rimshot</li><li>rollout</li><li>rumble</li><li>sax</li><li>secret</li><li>sexyback</li><li>story</li><li>tada</li><li>tmyk</li><li>trololo</li><li>trombone</li><li>unix</li><li>vuvuzela</li><li>what</li><li>whoomp</li><li>yeah</li><li>yodel</li></ul></td>
        <td>Send a notification sound before the message.</td>
    </tr>
            <tr>
    <td>room</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Room number to which the message should be sent.</td>
    </tr>
            <tr>
    <td>subscription</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The subscription name to use.</td>
    </tr>
            <tr>
    <td>token</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>API token.</td>
    </tr>
        </table>


.. note:: Requires urllib2


.. note:: Requires cgi


Examples
--------

.. raw:: html

    <br/>


::

    - campfire: subscription=foo token=12345 room=123 msg="Task completed."
    
    - campfire: subscription=foo token=12345 room=123 notify=loggins
            msg="Task completed ... with feeling."



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

