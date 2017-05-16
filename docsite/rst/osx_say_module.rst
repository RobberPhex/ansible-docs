.. _osx_say:


osx_say - Makes an OSX computer to speak.
+++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

makes an OS computer speak!  Amuse your friends, annoy your coworkers!


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
            <tr>
    <td>msg<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>What to say</div></td></tr>
            <tr>
    <td>voice<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>What voice to use</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - local_action: osx_say msg="{{inventory_hostname}} is all done" voice=Zarvox


Notes
-----

.. note:: If you like this module, you may also be interested in the osx_say callback in the plugins/ directory of the source checkout.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

