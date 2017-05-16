.. _slurp:


slurp - Slurps a file from remote nodes
+++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module works like :ref:`fetch <fetch>`. It is used for fetching a base64- encoded blob containing the data in a remote file.




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
    <td>src<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The file on the remote system to fetch. This <em>must</em> be a file, not a directory.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    ansible host -m slurp -a 'src=/tmp/xx'
       host | success >> {
          "content": "aGVsbG8gQW5zaWJsZSB3b3JsZAo=", 
          "encoding": "base64"
       }


Notes
-----

.. note:: See also: :ref:`fetch <fetch>`


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

