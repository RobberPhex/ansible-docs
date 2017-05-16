.. _win_timezone:


win_timezone - Sets Windows machine timezone
++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.1


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Sets machine time to the specified timezone, the module will check if the provided timezone is supported on the machine.




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
    <td>timezone<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Timezone to set to.  Example Central Standard Time</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

      # Set machine's timezone to Central Standard Time
      win_timezone:
        timezone: "Central Standard Time"




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

