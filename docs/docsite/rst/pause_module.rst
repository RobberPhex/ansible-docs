.. _pause:


pause - Pause playbook execution
++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Pauses playbook execution for a set amount of time, or until a prompt is acknowledged. All parameters are optional. The default behavior is to pause with a prompt.
* You can use ``ctrl+c`` if you wish to advance a pause earlier than it is set to expire or if you need to abort a playbook run entirely. To continue early: press ``ctrl+c`` and then ``c``. To abort a playbook: press ``ctrl+c`` and then ``a``.
* The pause module integrates into async/parallelized playbooks without any special considerations (see also: Rolling Updates). When using pauses with the ``serial`` playbook parameter (as in rolling updates) you are only prompted once for the current group of hosts.




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
                <tr><td>minutes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A positive number of minutes to pause for.</div>        </td></tr>
                <tr><td>prompt<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Optional text to use for the prompt message.</div>        </td></tr>
                <tr><td>seconds<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>A positive number of seconds to pause for.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Pause for 5 minutes to build app cache.
    - pause:
        minutes: 5
    
    # Pause until you can verify updates to an application were successful.
    - pause:
    
    # A helpful reminder of what to look out for post-update.
    - pause:
        prompt: "Make sure org.foo.FooOverload exception is not present"

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
        <td> start </td>
        <td> Time when started pausing </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 2017-02-23 14:35:07.298862 </td>
    </tr>
            <tr>
        <td> user_input </td>
        <td> User input from interactive console </td>
        <td align=center> if no waiting time set </td>
        <td align=center> string </td>
        <td align=center> Example user input </td>
    </tr>
            <tr>
        <td> delta </td>
        <td> Time paused in seconds </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 2 </td>
    </tr>
            <tr>
        <td> stop </td>
        <td> Time when ended pausing </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> 2017-02-23 14:35:09.552594 </td>
    </tr>
            <tr>
        <td> stdout </td>
        <td> Output of pause module </td>
        <td align=center> always </td>
        <td align=center> string </td>
        <td align=center> Paused for 0.04 minutes </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - Starting in 2.2,  if you specify 0 or negative for minutes or seconds, it will wait for 1 second, previously it would wait indefinitely.



Status
~~~~~~

This module is flagged as **stableinterface** which means that the maintainers for this module guarantee that no backward incompatible interface changes will be made.


Support
~~~~~~~

This module is maintained by those with core commit privileges

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
