.. _twilio:


twilio - Sends a text message to a mobile phone through Twilio.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Sends a text message to a phone number through an the Twilio SMS service.

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
    <td>account_sid</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>user's account id for Twilio found on the account page</td>
    </tr>
            <tr>
    <td>auth_token</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>user's authentication token for Twilio found on the account page</td>
    </tr>
            <tr>
    <td>from_number</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>what phone number to send the text message from, format +15551112222</td>
    </tr>
            <tr>
    <td>msg</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>the body of the text message</td>
    </tr>
            <tr>
    <td>to_number</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>what phone number to send the text message to, format +15551112222</td>
    </tr>
        </table>


.. note:: Requires urllib


.. note:: Requires urllib2


Examples
--------

.. raw:: html

    <br/>


::

    # send a text message from the local server about the build status to (555) 303 5681
    # note: you have to have purchased the 'from_number' on your Twilio account
    - local_action: text msg="All servers with webserver role are now configured." 
      account_sid={{ twilio_account_sid }}
      auth_token={{ twilio_auth_token }}
      from_number=+15552014545 to_number=+15553035681
    
    # send a text message from a server to (555) 111 3232
    # note: you have to have purchased the 'from_number' on your Twilio account
    - text: msg="This server's configuration is now complete."
      account_sid={{ twilio_account_sid }}
      auth_token={{ twilio_auth_token }}
      from_number=+15553258899 to_number=+15551113232
      

.. note:: Like the other notification modules, this one requires an external dependency to work. In this case, you'll need a Twilio account with a purchased or verified phone number to send the text message.


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

