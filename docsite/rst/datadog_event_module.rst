.. _datadog_event:


datadog_event - Posts events to DataDog  service
++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.3


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Allows to post events to DataDog (www.datadoghq.com) service.
Uses http://docs.datadoghq.com/api/#events API.




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
    <td>aggregation_key<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>An arbitrary string to use for aggregation.</div></td></tr>
            <tr>
    <td>alert_type<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>info</td>
        <td><ul><li>error</li><li>warning</li><li>info</li><li>success</li></ul></td>
        <td><div>Type of alert.</div></td></tr>
            <tr>
    <td>api_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Your DataDog API key.</div></td></tr>
            <tr>
    <td>app_key<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Your DataDog app key.</div></td></tr>
            <tr>
    <td>date_happened<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>now</td>
        <td><ul></ul></td>
        <td><div>POSIX timestamp of the event.</div><div>Default value is now.</div></td></tr>
            <tr>
    <td>priority<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>normal</td>
        <td><ul><li>normal</li><li>low</li></ul></td>
        <td><div>The priority of the event.</div></td></tr>
            <tr>
    <td>tags<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Comma separated list of tags to apply to the event.</div></td></tr>
            <tr>
    <td>text<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The body of the event.</div></td></tr>
            <tr>
    <td>title<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The event title.</div></td></tr>
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

    # Post an event with low priority
    datadog_event: title="Testing from ansible" text="Test!" priority="low"
                   api_key: "9775a026f1ca7d1c6c5af9d94d9595a4"
                   app_key: "j4JyCYfefWHhgFgiZUqRm63AXHNZQyPGBfJtAzmN"
    # Post an event with several tags
    datadog_event: title="Testing from ansible" text="Test!"
                   api_key: "9775a026f1ca7d1c6c5af9d94d9595a4"
                   app_key: "j4JyCYfefWHhgFgiZUqRm63AXHNZQyPGBfJtAzmN"
                   tags=aa,bb,#host:{{ inventory_hostname }}




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

