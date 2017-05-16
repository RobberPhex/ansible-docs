.. _gcpubsub_facts:


gcpubsub_facts - List Topics/Subscriptions and Messages from Google PubSub.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* List Topics/Subscriptions from Google PubSub.  Use the gcpubsub module for topic/subscription management. See https://cloud.google.com/pubsub/docs for an overview.


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
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>list is the only valid option.</div>        </td></tr>
                <tr><td>topic<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>GCP pubsub topic name.  Only the name, not the full path, is required.</div>        </td></tr>
                <tr><td>view<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Choices are 'topics' or 'subscriptions'</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    ## List all Topics in a project
    gcpubsub_facts:
      view: topics
      state: list
    
    ## List all Subscriptions in a project
    gcpubsub_facts:
      view: subscriptions
      state: list
    
    ## List all Subscriptions for a Topic in a project
    gcpubsub_facts:
      view: subscriptions
      topic: my-topic
      state: list

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
        <td> Name of topic. Used to filter subscriptions. </td>
        <td align=center> Always </td>
        <td align=center> str </td>
        <td align=center> mytopic </td>
    </tr>
            <tr>
        <td> topics </td>
        <td> List of topics. </td>
        <td align=center> When view is set to topics. </td>
        <td align=center> list </td>
        <td align=center> ['mytopic', 'mytopic2'] </td>
    </tr>
            <tr>
        <td> subscriptions </td>
        <td> List of subscriptions. </td>
        <td align=center> When view is set to subscriptions. </td>
        <td align=center> list </td>
        <td align=center> ['mysubscription', 'mysubscription2'] </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - list state enables user to list topics or subscriptions in the project.  See examples for details.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
