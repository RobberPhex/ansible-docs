.. _at:


at - Schedule the execution of a command or script file via the at command.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.5

Use this module to schedule a command or script file to run once in the future.
All jobs are executed in the 'a' queue.

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
    <td>command</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A command to be executed in the future.</td>
    </tr>
            <tr>
    <td>count</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The count of units in the future to execute the command or script file.</td>
    </tr>
            <tr>
    <td>script_file</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>An existing script file to be executed in the future.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>The state dictates if the command or script file should be evaluated as present(added) or absent(deleted).</td>
    </tr>
            <tr>
    <td>unique</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>If a matching job is present a new job will not be added.</td>
    </tr>
            <tr>
    <td>units</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>minutes</li><li>hours</li><li>days</li><li>weeks</li></ul></td>
        <td>The type of units in the future to execute the command or script file.</td>
    </tr>
        </table>


.. note:: Requires at


Examples
--------

.. raw:: html

    <br/>


::

    # Schedule a command to execute in 20 minutes as root.
    - at: command="ls -d / > /dev/null" count=20 units="minutes"
    
    # Match a command to an existing job and delete the job.
    - at: command="ls -d / > /dev/null" state="absent"
    
    # Schedule a command to execute in 20 minutes making sure it is unique in the queue.
    - at: command="ls -d / > /dev/null" unique=true count=20 units="minutes"



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

