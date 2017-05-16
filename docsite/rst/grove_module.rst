.. _grove:


grove - Sends a notification to a grove.io channel
++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.4


.. contents::
   :local:
   :depth: 1


Synopsis
--------

The :ref:`grove <grove>` module sends a message for a service to a Grove.io channel.




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
    <td>channel_token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Token of the channel to post to.</div></td></tr>
            <tr>
    <td>icon_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Icon for the service</div></td></tr>
            <tr>
    <td>message<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Message content</div></td></tr>
            <tr>
    <td>service<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ansible</td>
        <td><ul></ul></td>
        <td><div>Name of the service (displayed as the "user" in the message)</div></td></tr>
            <tr>
    <td>url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Service URL for the web client</div></td></tr>
            <tr>
    <td>validate_certs<br/><div style="font-size: small;"> (added in 1.5.1)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - grove: >
        channel_token=6Ph62VBBJOccmtTPZbubiPzdrhipZXtg
        service=my-app
        message=deployed {{ target }}




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

