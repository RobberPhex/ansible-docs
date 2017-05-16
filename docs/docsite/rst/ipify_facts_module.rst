.. _ipify_facts:


ipify_facts - Retrieve the public IP of your internet gateway.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* If behind NAT and need to know the public IP of your internet gateway.




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
                <tr><td>api_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https://api.ipify.org</td>
        <td></td>
        <td><div>URL of the ipify.org API service.</div><div><code>?format=json</code> will be appended per default.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"> (added in 2.3)</div></td>
    <td>no</td>
    <td>10</td>
        <td></td>
        <td><div>HTTP connection timeout in seconds.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Gather IP facts from ipify.org
    - name: get my public IP
      ipify_facts:
    
    # Gather IP facts from your own ipify service endpoint with a custom timeout
    - name: get my public IP
      ipify_facts:
        api_url: http://api.example.com/ipify
        timeout: 20

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
        <td> ipify_public_ip </td>
        <td> Public IP of the internet gateway. </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 1.2.3.4 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Visit https://www.ipify.org to get more information.



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
