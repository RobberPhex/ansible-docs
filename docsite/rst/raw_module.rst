.. _raw:


raw - Executes a low-down and dirty SSH command
+++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Executes a low-down and dirty SSH command, not going through the module subsystem. This is useful and should only be done in two cases. The first case is installing ``python-simplejson`` on older (Python 2.4 and before) hosts that need it as a dependency to run modules, since nearly all core modules require it. Another is speaking to any devices such as routers that do not have any Python installed. In any other case, using the :ref:`shell <shell>` or :ref:`command <command>` module is much more appropriate. Arguments given to :ref:`raw <raw>` are run directly through the configured remote shell. Standard output, error output and return code are returned when available. There is no change handler support for this module.
This module does not require python on the remote system, much like the :ref:`script <script>` module.




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
    <td>executable<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>change the shell used to execute the command. Should be an absolute path to the executable.</div><div>when using privilege escalation (<code>become</code>), a default shell will be assigned if one is not provided as privilege escalation requires a shell.</div></td></tr>
            <tr>
    <td>free_form<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the raw module takes a free form command to run</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Bootstrap a legacy python 2.4 host
    - raw: yum -y install python-simplejson
    
    # Bootstrap a host without python2 installed
    - raw: dnf install -y python2 python2-dnf libselinux-python
    
    # Run a command that uses non-posix shell-isms (in this example /bin/sh
    # doesn't handle redirection and wildcards together but bash does)
    - raw: cat < /tmp/*txt
      args:
        executable: /bin/bash


Notes
-----

.. note:: If using raw from a playbook, you may need to disable fact gathering using ``gather_facts: no`` if you're using ``raw`` to bootstrap python onto the machine.
.. note:: If you want to execute a command securely and predictably, it may be better to use the :ref:`command <command>` or :ref:`shell <shell>` modules instead.
.. note:: the ``environment`` keyword does not work with raw normally, it requires a shell which means it only works if ``executable`` is set or using the module with privilege escalation (``become``).


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

