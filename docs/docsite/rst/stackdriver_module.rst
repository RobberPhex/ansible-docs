.. _stackdriver:


stackdriver - Send code deploy and annotation events to stackdriver
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Send code deploy and annotation events to Stackdriver




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
                <tr><td>annotated_by<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Ansible</td>
        <td></td>
        <td><div>The person or robot who the annotation should be attributed to.</div>        </td></tr>
                <tr><td>deployed_by<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>Ansible</td>
        <td></td>
        <td><div>The person or robot responsible for deploying the code</div>        </td></tr>
                <tr><td>deployed_to<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The environment code was deployed to. (ie: development, staging, production)</div>        </td></tr>
                <tr><td>event<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>annotation</li><li>deploy</li></ul></td>
        <td><div>The type of event to send, either annotation or deploy</div>        </td></tr>
                <tr><td>event_epoch<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Unix timestamp of where the event should appear in the timeline, defaults to now. Be careful with this.</div>        </td></tr>
                <tr><td>instance_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>id of an EC2 instance that this event should be attached to, which will limit the contexts where this event is shown</div>        </td></tr>
                <tr><td>key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>API key.</div>        </td></tr>
                <tr><td>level<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>INFO</td>
        <td><ul><li>INFO</li><li>WARN</li><li>ERROR</li></ul></td>
        <td><div>one of INFO/WARN/ERROR, defaults to INFO if not supplied.  May affect display.</div>        </td></tr>
                <tr><td>msg<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The contents of the annotation message, in plain text.  Limited to 256 characters. Required for annotation.</div>        </td></tr>
                <tr><td>repository<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The repository (or project) deployed</div>        </td></tr>
                <tr><td>revision_id<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The revision of the code that was deployed. Required for deploy events</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - stackdriver:
        key: AAAAAA
        event: deploy
        deployed_to: production
        deployed_by: leeroyjenkins
        repository: MyWebApp
        revision_id: abcd123
    
    - stackdriver:
        key: AAAAAA
        event: annotation
        msg: Greetings from Ansible
        annotated_by: leeroyjenkins
        level: WARN
        instance_id: i-abcd1234





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
