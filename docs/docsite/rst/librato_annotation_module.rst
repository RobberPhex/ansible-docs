.. _librato_annotation:


librato_annotation - create an annotation in librato
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Create an annotation event on the given annotation stream :name. If the annotation stream does not exist, it will be created automatically




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
                <tr><td>api_key<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Librato account api key</div>        </td></tr>
                <tr><td>description<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The description contains extra meta-data about a particular annotation</div><div>The description should contain specifics on the individual annotation e.g. Deployed 9b562b2 shipped new feature foo!</div>        </td></tr>
                <tr><td>end_time<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The unix timestamp indicating the the time at which the event referenced by this annotation ended</div><div>For events that have a duration, this is a useful way to annotate the duration of the event</div>        </td></tr>
                <tr><td>links<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>See examples</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The annotation stream name</div><div>If the annotation stream does not exist, it will be created automatically</div>        </td></tr>
                <tr><td>source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A string which describes the originating source of an annotation when that annotation is tracked across multiple members of a population</div>        </td></tr>
                <tr><td>start_time<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The unix timestamp indicating the the time at which the event referenced by this annotation started</div>        </td></tr>
                <tr><td>title<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The title of an annotation is a string and may contain spaces</div><div>The title should be a short, high-level summary of the annotation e.g. v45 Deployment</div>        </td></tr>
                <tr><td>user<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Librato account username</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Create a simple annotation event with a source
    - librato_annotation:
        user: user@example.com
        api_key: XXXXXXXXXXXXXXXXX
        title: App Config Change
        source: foo.bar
        description: This is a detailed description of the config change
    
    # Create an annotation that includes a link
    - librato_annotation:
        user: user@example.com
        api_key: XXXXXXXXXXXXXXXXXX
        name: code.deploy
        title: app code deploy
        description: this is a detailed description of a deployment
        links:
          - rel: example
            href: http://www.example.com/deploy
    
    # Create an annotation with a start_time and end_time
    - librato_annotation:
        user: user@example.com
        api_key: XXXXXXXXXXXXXXXXXX
        name: maintenance
        title: Maintenance window
        description: This is a detailed description of maintenance
        start_time: 1395940006
        end_time: 1395954406





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
