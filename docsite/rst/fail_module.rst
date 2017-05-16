.. _fail:


fail - Fail with custom message
+++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module fails the progress with a custom message. It can be useful for bailing out when a certain condition is met using ``when``.




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
    <td>msg<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>'Failed as requested from task'</td>
        <td><ul></ul></td>
        <td><div>The customized message used for failing execution. If omitted, fail will simple bail out with a generic message.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example playbook using fail and when together
    - fail: msg="The system may not be provisioned according to the CMDB status."
      when: cmdb_status != "to-be-staged"




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

