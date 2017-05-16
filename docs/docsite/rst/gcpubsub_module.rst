.. _gcpubsub:


gcpubsub - Create and Delete Topics/Subscriptions, Publish and pull messages on PubSub.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create and Delete Topics/Subscriptions, Publish and pull messages on PubSub. See https://cloud.google.com/pubsub/docs for an overview.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * google-auth >= 0.5.0
  * google-cloud-pubsub >= 0.22.0


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
                <tr><td>ack_deadline<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Subfield of subscription. Not required. Default deadline for subscriptions to ACK the message before it is resent. See examples.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Subfield of subscription. Required if subscription is specified. See examples.</div>        </td></tr>
                <tr><td>publish<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>List of dictionaries describing messages and attributes to be published.  Dictionary is in message(str):attributes(dict) format. Only message is required.</div>        </td></tr>
                <tr><td>pull<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Subfield of subscription. Not required. If specified, messages will be retrieved from topic via the provided subscription name. max_messages (int; default None; max number of messages to pull), message_ack (bool; default False; acknowledge the message) and return_immediately (bool; default True, don't wait for messages to appear). If the messages are acknowledged, changed is set to True, otherwise, changed is False.</div>        </td></tr>
                <tr><td>push_endpoint<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Subfield of subscription.  Not required.  If specified, message will be sent to an endpoint. See <a href='https://cloud.google.com/pubsub/docs/advanced#push_endpoints'>https://cloud.google.com/pubsub/docs/advanced#push_endpoints</a> for more information.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td></td>
        <td><div>State of the topic or queue (absent, present). Applies to the most granular resource. Remove the most granular resource.  If subcription is specified we remove it.  If only topic is specified, that is what is removed. Note that a topic can be removed without first removing the subscription.</div>        </td></tr>
                <tr><td>subscription<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Dictionary containing a subscripton name associated with a topic (required), along with optional ack_deadline, push_endpoint and pull. For pulling from a subscription, message_ack (bool), max_messages (int) and return_immediate are available as subfields.  See subfields name, push_endpoint and ack_deadline for more information.</div>        </td></tr>
                <tr><td>topic<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>GCP pubsub topic name.  Only the name, not the full path, is required.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a topic and publish a message to it
    # (Message will be pushed; there is no check to see if the message was pushed before
    # Topics:
    ## Create Topic
    gcpubsub:
      topic: ansible-topic-example
      state: present
    
    ## Delete Topic
    ### Subscriptions associated with topic are not deleted.
    gcpubsub:
      topic: ansible-topic-example
      state: absent
    
    ## Messages: publish multiple messages, with attributes (key:value available with the message)
    ### setting absent will keep the messages from being sent
    gcpubsub:
      topic: "{{ topic_name }}"
      state: present
      publish:
        - message: "this is message 1"
          attributes:
            mykey1: myvalue
            mykey2: myvalu2
            mykey3: myvalue3
        - message: "this is message 2"
          attributes:
            server: prod
            sla: "99.9999"
            owner: fred
    
    # Subscriptions
    ## Create Subscription (pull)
    gcpubsub:
      topic: ansible-topic-example
      subscription:
      - name: mysub
      state: present
    
    ## Create Subscription with ack_deadline and push endpoint
    ### pull is default, ack_deadline is not required
    gcpubsub:
      topic: ansible-topic-example
      subscription:
      - name: mysub
        ack_deadline: "60"
        push_endpoint: http://pushendpoint.example.com
      state: present
    
    ## Subscription change from push to pull
    ### setting push_endpoint to "None" converts subscription to pull.
    gcpubsub:
      topic: ansible-topic-example
      subscription:
        name: mysub
        push_endpoint: "None"
    
    ## Delete subscription
    ### Topic will not be deleted
    gcpubsub:
      topic: ansible-topic-example
      subscription:
      - name: mysub
      state: absent
    
    ## Pull messages from subscription
    ### only pull keyword is required.
    gcpubsub:
      topic: ansible-topic-example
      subscription:
        name: ansible-topic-example-sub
        pull:
          message_ack: yes
          max_messages: "100"

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
        <td> topic </td>
        <td> Name of topic. </td>
        <td align=center> Always </td>
        <td align=center> str </td>
        <td align=center> mytopic </td>
    </tr>
            <tr>
        <td> state </td>
        <td> The state of the topic or subscription. Value will be either 'absent' or 'present'. </td>
        <td align=center> Always </td>
        <td align=center> str </td>
        <td align=center> present </td>
    </tr>
            <tr>
        <td> publish </td>
        <td> List of dictionaries describing messages and attributes to be published.  Dictionary is in message(str):attributes(dict) format. Only message is required. </td>
        <td align=center> Only when specified </td>
        <td align=center> list of dictionary </td>
        <td align=center> publish: ['message': 'my message', attributes: {'key1': 'value1'}] </td>
    </tr>
            <tr>
        <td> pulled_messages </td>
        <td> list of dictionaries containing message info.  Fields are ack_id, attributes, data, message_id. </td>
        <td align=center> Only when subscription.pull is specified </td>
        <td align=center> list of dictionary </td>
        <td align=center> [{'attributes': {'...': None, 'key1': 'val1'}, 'ack_id': 'XkASTCcYREl...', 'data': 'this is message 1', 'message_id': '49107464153705'}, '..'] </td>
    </tr>
            <tr>
        <td> subscription </td>
        <td> Name of subscription. </td>
        <td align=center> When subscription fields are specified </td>
        <td align=center> str </td>
        <td align=center> mysubscription </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Subscription pull happens before publish.  You cannot publish and pull in the same task.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
