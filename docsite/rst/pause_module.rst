.. _pause:


pause - Pause playbook execution
++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Pauses playbook execution for a set amount of time, or until a prompt is acknowledged. All parameters are optional. The default behavior is to pause with a prompt.
You can use ``ctrl+c`` if you wish to advance a pause earlier than it is set to expire or if you need to abort a playbook run entirely. To continue early: press ``ctrl+c`` and then ``c``. To abort a playbook: press ``ctrl+c`` and then ``a``.
The pause module integrates into async/parallelized playbooks without any special considerations (see also: Rolling Updates). When using pauses with the ``serial`` playbook parameter (as in rolling updates) you are only prompted once for the current group of hosts.




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
    <td>minutes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A positive number of minutes to pause for.</div></td></tr>
            <tr>
    <td>prompt<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Optional text to use for the prompt message.</div></td></tr>
            <tr>
    <td>seconds<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A positive number of seconds to pause for.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Pause for 5 minutes to build app cache.
    - pause: minutes=5
    
    # Pause until you can verify updates to an application were successful.
    - pause:
    
    # A helpful reminder of what to look out for post-update.
    - pause: prompt="Make sure org.foo.FooOverload exception is not present"


Notes
-----

.. note:: Starting in 2.2,  if you specify 0 or negative for minutes or seconds, it will wait for 1 second, previously it would wait indefinitely.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

