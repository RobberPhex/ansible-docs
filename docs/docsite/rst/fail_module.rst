.. _fail:


fail - Fail with custom message
+++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module fails the progress with a custom message. It can be useful for bailing out when a certain condition is met using ``when``.




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
                <tr><td>msg<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>'Failed as requested from task'</td>
        <td></td>
        <td><div>The customized message used for failing execution. If omitted, fail will simply bail out with a generic message.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Example playbook using fail and when together
    - fail:
        msg: "The system may not be provisioned according to the CMDB status."
      when: cmdb_status != "to-be-staged"





Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
