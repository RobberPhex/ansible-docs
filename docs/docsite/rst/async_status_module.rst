.. _async_status:


async_status - Obtain status of asynchronous task
+++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module gets the status of an asynchronous task.




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
                <tr><td>jid<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Job or task identifier</div>        </td></tr>
                <tr><td>mode<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>status</td>
        <td><ul><li>status</li><li>cleanup</li></ul></td>
        <td><div>if <code>status</code>, obtain the status; if <code>cleanup</code>, clean up the async job cache located in <code>~/.ansible_async/</code> for the specified job <em>jid</em>.</div>        </td></tr>
        </table>
    </br>






Notes
-----

.. note::
    - See also http://docs.ansible.com/playbooks_async.html



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
