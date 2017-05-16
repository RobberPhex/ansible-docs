.. _assert:


assert - Asserts given expressions are true
+++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.5


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* This module asserts that given expressions are true with an optional custom message.




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
    <td></td>
        <td></td>
        <td><div>The customized message used for a failing assertion</div>        </td></tr>
                <tr><td>that<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>A string expression of the same form that can be passed to the 'when' statement</div><div>Alternatively, a list of string expressions</div>        </td></tr>
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





Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
