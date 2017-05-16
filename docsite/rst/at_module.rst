.. _at:


at - Schedule the execution of a command or script file via the at command.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.5


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Use this module to schedule a command or script file to run once in the future.
All jobs are executed in the 'a' queue.


Requirements (on host that executes module)
-------------------------------------------

  * at


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
    <td>command<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A command to be executed in the future.</div></td></tr>
            <tr>
    <td>count<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The count of units in the future to execute the command or script file.</div></td></tr>
            <tr>
    <td>script_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>An existing script file to be executed in the future.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>The state dictates if the command or script file should be evaluated as present(added) or absent(deleted).</div></td></tr>
            <tr>
    <td>unique<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>If a matching job is present a new job will not be added.</div></td></tr>
            <tr>
    <td>units<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>minutes</li><li>hours</li><li>days</li><li>weeks</li></ul></td>
        <td><div>The type of units in the future to execute the command or script file.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Schedule a command to execute in 20 minutes as root.
    - at: command="ls -d / > /dev/null" count=20 units="minutes"
    
    # Match a command to an existing job and delete the job.
    - at: command="ls -d / > /dev/null" state="absent"
    
    # Schedule a command to execute in 20 minutes making sure it is unique in the queue.
    - at: command="ls -d / > /dev/null" unique=true count=20 units="minutes"




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

