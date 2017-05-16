.. _cisco_spark:


cisco_spark - Send a message to a Cisco Spark Room or Individual.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Send a message to a Cisco Spark Room or Individual with options to control the formatting.




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
                <tr><td>message<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The message you would like to send.</div>        </td></tr>
                <tr><td>message_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>text</td>
        <td><ul><li>text</li><li>markdown</li></ul></td>
        <td><div>Specifies how you would like the message formatted.</div>        </td></tr>
                <tr><td>personal_token<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Your personal access token required to validate the Spark API.</div></br>
    <div style="font-size: small;">aliases: token<div>        </td></tr>
                <tr><td>recipient_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The unique identifier associated with the supplied <code>recipient_type</code>.</div>        </td></tr>
                <tr><td>recipient_type<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>roomId</li><li>toPersonEmail</li><li>toPersonId</li></ul></td>
        <td><div>The request parameter you would like to send the message to.</div><div>Messages can be sent to either a room or individual (by ID or E-Mail).</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Note: The following examples assume a variable file has been imported
    # that contains the appropriate information.
    
    - name: Cisco Spark - Markdown Message to a Room
      cisco_spark:
        recipient_type: roomId
        recipient_id: "{{ room_id }}"
        message_type: markdown
        personal_token: "{{ token }}"
        message: "**Cisco Spark Ansible Module - Room Message in Markdown**"
    
    - name: Cisco Spark - Text Message to a Room
      cisco_spark:
        recipient_type: roomId
        recipient_id: "{{ room_id }}"
        message_type: text
        personal_token: "{{ token }}"
        message: "Cisco Spark Ansible Module - Room Message in Text"
    
    - name: Cisco Spark - Text Message by an Individuals ID
      cisco_spark:
        recipient_type: toPersonId
        recipient_id: "{{ person_id}}"
        message_type: text
        personal_token: "{{ token }}"
        message: "Cisco Spark Ansible Module - Text Message to Individual by ID"
    
    - name: Cisco Spark - Text Message by an Individuals E-Mail Address
      cisco_spark:
        recipient_type: toPersonEmail
        recipient_id: "{{ person_email }}"
        message_type: text
        personal_token: "{{ token }}"
        message: "Cisco Spark Ansible Module - Text Message to Individual by E-Mail"
    

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> status_code </td>
        <td> ['The Response Code returned by the Spark API.', 'Full Responsde Code explanations can be found at U(https://developer.ciscospark.com/endpoint-messages-post.html).'] </td>
        <td align=center> always </td>
        <td align=center> int </td>
        <td align=center> 200 </td>
    </tr>
            <tr>
        <td> message </td>
        <td> ['The Response Message returned by the Spark API.', 'Full Responsde Code explanations can be found at U(https://developer.ciscospark.com/endpoint-messages-post.html.'] </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> OK (585 bytes) </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - The ``recipient_id`` type must be valid for the supplied ``recipient_id``.
    - Full API documentation can be found at https://developer.ciscospark.com/endpoint-messages-post.html.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
