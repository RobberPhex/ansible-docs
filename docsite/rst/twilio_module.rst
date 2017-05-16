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
        <td><div>u</div><div>s</div><div>e</div><div>r</div><div>'</div><div>s</div><div> </div><div>T</div><div>w</div><div>i</div><div>l</div><div>i</div><div>o</div><div> </div><div>a</div><div>c</div><div>c</div><div>o</div><div>u</div><div>n</div><div>t</div><div> </div><div>t</div><div>o</div><div>k</div><div>e</div><div>n</div><div> </div><div>f</div><div>o</div><div>u</div><div>n</div><div>d</div><div> </div><div>o</div><div>n</div><div> </div><div>t</div><div>h</div><div>e</div><div> </div><div>a</div><div>c</div><div>c</div><div>o</div><div>u</div><div>n</div><div>t</div><div> </div><div>p</div><div>a</div><div>g</div><div>e</div></td></tr>
            <tr>
    <td>auth_token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>u</div><div>s</div><div>e</div><div>r</div><div>'</div><div>s</div><div> </div><div>T</div><div>w</div><div>i</div><div>l</div><div>i</div><div>o</div><div> </div><div>a</div><div>u</div><div>t</div><div>h</div><div>e</div><div>n</div><div>t</div><div>i</div><div>c</div><div>a</div><div>t</div><div>i</div><div>o</div><div>n</div><div> </div><div>t</div><div>o</div><div>k</div><div>e</div><div>n</div></td></tr>
            <tr>
    <td>from_number<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>t</div><div>h</div><div>e</div><div> </div><div>T</div><div>w</div><div>i</div><div>l</div><div>i</div><div>o</div><div> </div><div>n</div><div>u</div><div>m</div><div>b</div><div>e</div><div>r</div><div> </div><div>t</div><div>o</div><div> </div><div>s</div><div>e</div><div>n</div><div>d</div><div> </div><div>t</div><div>h</div><div>e</div><div> </div><div>t</div><div>e</div><div>x</div><div>t</div><div> </div><div>m</div><div>e</div><div>s</div><div>s</div><div>a</div><div>g</div><div>e</div><div> </div><div>f</div><div>r</div><div>o</div><div>m</div><div>,</div><div> </div><div>f</div><div>o</div><div>r</div><div>m</div><div>a</div><div>t</div><div> </div><div>+</div><div>1</div><div>5</div><div>5</div><div>5</div><div>1</div><div>1</div><div>1</div><div>2</div><div>2</div><div>2</div><div>2</div></td></tr>
            <tr>
    <td>media_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a</div><div> </div><div>U</div><div>R</div><div>L</div><div> </div><div>w</div><div>i</div><div>t</div><div>h</div><div> </div><div>a</div><div> </div><div>p</div><div>i</div><div>c</div><div>t</div><div>u</div><div>r</div><div>e</div><div>,</div><div> </div><div>v</div><div>i</div><div>d</div><div>e</div><div>o</div><div> </div><div>o</div><div>r</div><div> </div><div>s</div><div>o</div><div>u</div><div>n</div><div>d</div><div> </div><div>c</div><div>l</div><div>i</div><div>p</div><div> </div><div>t</div><div>o</div><div> </div><div>s</div><div>e</div><div>n</div><div>d</div><div> </div><div>w</div><div>i</div><div>t</div><div>h</div><div> </div><div>a</div><div>n</div><div> </div><div>M</div><div>M</div><div>S</div><div> </div><div>(</div><div>m</div><div>u</div><div>l</div><div>t</div><div>i</div><div>m</div><div>e</div><div>d</div><div>i</div><div>a</div><div> </div><div>m</div><div>e</div><div>s</div><div>s</div><div>a</div><div>g</div><div>e</div><div>)</div><div> </div><div>i</div><div>n</div><div>s</div><div>t</div><div>e</div><div>a</div><div>d</div><div> </div><div>o</div><div>f</div><div> </div><div>a</div><div> </div><div>p</div><div>l</div><div>a</div><div>i</div><div>n</div><div> </div><div>S</div><div>M</div><div>S</div></td></tr>
            <tr>
    <td>msg<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>t</div><div>h</div><div>e</div><div> </div><div>b</div><div>o</div><div>d</div><div>y</div><div> </div><div>o</div><div>f</div><div> </div><div>t</div><div>h</div><div>e</div><div> </div><div>t</div><div>e</div><div>x</div><div>t</div><div> </div><div>m</div><div>e</div><div>s</div><div>s</div><div>a</div><div>g</div><div>e</div></td></tr>
            <tr>
    <td>to_number<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>o</div><div>n</div><div>e</div><div> </div><div>o</div><div>r</div><div> </div><div>m</div><div>o</div><div>r</div><div>e</div><div> </div><div>p</div><div>h</div><div>o</div><div>n</div><div>e</div><div> </div><div>n</div><div>u</div><div>m</div><div>b</div><div>e</div><div>r</div><div>s</div><div> </div><div>t</div><div>o</div><div> </div><div>s</div><div>e</div><div>n</div><div>d</div><div> </div><div>t</div><div>h</div><div>e</div><div> </div><div>t</div><div>e</div><div>x</div><div>t</div><div> </div><div>m</div><div>e</div><div>s</div><div>s</div><div>a</div><div>g</div><div>e</div><div> </div><div>t</div><div>o</div><div>,</div><div> </div><div>f</div><div>o</div><div>r</div><div>m</div><div>a</div><div>t</div><div> </div><div>+</div><div>1</div><div>5</div><div>5</div><div>5</div><div>1</div><div>1</div><div>1</div><div>2</div><div>2</div><div>2</div><div>2</div></td></tr>
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

