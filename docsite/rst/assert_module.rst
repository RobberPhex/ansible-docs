.. _assert:


assert - Asserts given expressions are true
+++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.5


.. contents::
   :local:
   :depth: 1


Synopsis
--------

This module asserts that given expressions are true with an optional custom message.




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
    <td></td>
        <td><ul></ul></td>
        <td><div>The customized message used for a failing assertion</div></td></tr>
            <tr>
    <td>that<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A string expression of the same form that can be passed to the 'when' statement</div><div>Alternatively, a list of string expressions</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - assert: { that: "ansible_os_family != 'RedHat'" }
    
    - assert: 
        that: 
          - "'foo' in some_command_result.stdout" 
          - "number_of_the_counting == 3"
    
    - assert: 
        that: 
          - "my_param <= 100"
          - "my_param >= 0"
        msg: "'my_param' must be between 0 and 100"




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

