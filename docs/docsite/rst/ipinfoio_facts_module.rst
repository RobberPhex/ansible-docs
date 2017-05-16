.. _ipinfoio_facts:


ipinfoio_facts - Retrieve IP geolocation facts of a host's IP address
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Gather IP geolocation facts of a host's IP address using ipinfo.io API




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
                <tr><td>http_agent<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>ansible-ipinfoio-module/0.0.1</td>
        <td></td>
        <td><div>Set http user agent</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>HTTP connection timeout in seconds</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Retrieve geolocation data of a host's IP address
    - name: get IP geolocation data
      ipinfoio_facts:

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
        <td> ansible_facts </td>
        <td> Dictionary of ip geolocation facts for a host's IP address </td>
        <td align=center> changed </td>
        <td align=center> complex </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Check http://ipinfo.io/ for more information



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
