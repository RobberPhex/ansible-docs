.. _twilio:


twilio - Sends a text message to a mobile phone through Twilio.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Sends a text message to a phone number through the Twilio messaging API.




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
    <td>account_sid<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>user's Twilio account token found on the account page</div></td></tr>
            <tr>
    <td>auth_token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>user's Twilio authentication token</div></td></tr>
            <tr>
    <td>from_number<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the Twilio number to send the text message from, format +15551112222</div></td></tr>
            <tr>
    <td>media_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a URL with a picture, video or sound clip to send with an MMS (multimedia message) instead of a plain SMS</div></td></tr>
            <tr>
    <td>msg<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the body of the text message</div></td></tr>
            <tr>
    <td>to_number<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>one or more phone numbers to send the text message to, format +15551112222</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # send an SMS about the build status to (555) 303 5681
    # note: replace account_sid and auth_token values with your credentials
    # and you have to have the 'from_number' on your Twilio account
    - twilio:
        msg: "All servers with webserver role are now configured."
        account_sid: "ACXXXXXXXXXXXXXXXXX"
        auth_token: "ACXXXXXXXXXXXXXXXXX"
        from_number: "+15552014545"
        to_number: "+15553035681"
      delegate_to: localhost
    
    # send an SMS to multiple phone numbers about the deployment
    # note: replace account_sid and auth_token values with your credentials
    # and you have to have the 'from_number' on your Twilio account
    - twilio:
        msg: "This server's configuration is now complete."
        account_sid: "ACXXXXXXXXXXXXXXXXX"
        auth_token: "ACXXXXXXXXXXXXXXXXX"
        from_number: "+15553258899"
        to_number:
          - "+15551113232"
          - "+12025551235"
          - "+19735559010"
      delegate_to: localhost
    
    # send an MMS to a single recipient with an update on the deployment
    # and an image of the results
    # note: replace account_sid and auth_token values with your credentials
    # and you have to have the 'from_number' on your Twilio account
    - twilio:
        msg: "Deployment complete!"
        account_sid: "ACXXXXXXXXXXXXXXXXX"
        auth_token: "ACXXXXXXXXXXXXXXXXX"
        from_number: "+15552014545"
        to_number: "+15553035681"
        media_url: "https://demo.twilio.com/logo.png"
      delegate_to: localhost


Notes
-----

.. note:: This module is non-idempotent because it sends an email through the external API. It is idempotent only in the case that the module fails.
.. note:: Like the other notification modules, this one requires an external dependency to work. In this case, you'll need a Twilio account with a purchased or verified phone number to send the text message.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

