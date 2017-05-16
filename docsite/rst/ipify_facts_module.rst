.. _ipify_facts:


ipify_facts - Retrieve the public IP of your internet gateway.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

If behind NAT and need to know the public IP of your internet gateway.




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
    <td>api_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https://api.ipify.org</td>
        <td><ul></ul></td>
        <td><div>URL of the ipify.org API service.</div><div><code>?format=json</code> will be appended per default.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Gather IP facts from ipify.org
    - name: get my public IP
      ipify_facts:
    
    # Gather IP facts from your own ipify service endpoint
    - name: get my public IP
      ipify_facts: api_url=http://api.example.com/ipify

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

.. note:: Visit https://www.ipify.org to get more information.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

