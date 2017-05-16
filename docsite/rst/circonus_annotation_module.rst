.. _circonus_annotation:


circonus_annotation - create an annotation in circonus
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create an annotation event with a given category, title and description. Optionally start, end or durations can be provided


Requirements (on host that executes module)
-------------------------------------------

  * urllib3
  * requests
  * time


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
    <td>api_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Circonus API key</div></td></tr>
            <tr>
    <td>category<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Annotation Category</div></td></tr>
            <tr>
    <td>description<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Description of annotation</div></td></tr>
            <tr>
    <td>duration<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Duration in seconds of annotation, defaults to 0</div></td></tr>
            <tr>
    <td>start<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Unix timestamp of event start, defaults to now</div></td></tr>
            <tr>
    <td>stop<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Unix timestamp of event end, defaults to now + duration</div></td></tr>
            <tr>
    <td>title<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Title of annotation</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a simple annotation event with a source, defaults to start and end time of now
    - circonus_annotation:
        api_key: XXXXXXXXXXXXXXXXX
        title: 'App Config Change'
        description: 'This is a detailed description of the config change'
        category: 'This category groups like annotations'
    # Create an annotation with a duration of 5 minutes and a default start time of now
    - circonus_annotation:
        api_key: XXXXXXXXXXXXXXXXX
        title: 'App Config Change'
        description: 'This is a detailed description of the config change'
        category: 'This category groups like annotations'
        duration: 300
    # Create an annotation with a start_time and end_time
    - circonus_annotation:
        api_key: XXXXXXXXXXXXXXXXX
        title: 'App Config Change'
        description: 'This is a detailed description of the config change'
        category: 'This category groups like annotations'
        start_time: 1395940006
        end_time: 1395954407




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

