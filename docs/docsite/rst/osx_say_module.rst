.. _osx_say:


osx_say - Makes an OSX computer to speak.
+++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* makes an OS computer speak!  Amuse your friends, annoy your coworkers!


Requirements (on host that executes module)
-------------------------------------------

  * say


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
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>What to say</div>        </td></tr>
                <tr><td>voice<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>What voice to use</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - osx_say:
        msg: '{{ inventory_hostname }} is all done'
        voice: Zarvox
      delegate_to: localhost


Notes
-----

.. note::
    - If you like this module, you may also be interested in the osx_say callback in the plugins/ directory of the source checkout.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
