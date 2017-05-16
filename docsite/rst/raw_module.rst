.. _raw:


raw - Executes a low-down and dirty SSH command
+++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Executes a low-down and dirty SSH command, not going through the module subsystem. This is useful and should only be done in two cases. The first case is installing ``python-simplejson`` on older (Python 2.4 and before) hosts that need it as a dependency to run modules, since nearly all core modules require it. Another is speaking to any devices such as routers that do not have any Python installed. In any other case, using the ``shell`` or ``command`` module is much more appropriate. Arguments given to ``raw`` are run directly through the configured remote shell. Standard output, error output and return code are returned when available. There is no change handler support for this module.
This module does not require python on the remote system, much like the ``script`` module.

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
    <td>executable</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>change the shell used to execute the command. Should be an absolute path to the executable. (added in Ansible 1.0)</td>
    </tr>
            <tr>
    <td>free_form</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>the raw module takes a free form command to run</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Bootstrap a legacy python 2.4 host
    - raw: yum -y install python-simplejson

.. note:: If you want to execute a command securely and predictably, it may be better to use the ``command`` module instead. Best practices when writing playbooks will follow the trend of using ``command`` unless ``shell`` is explicitly required. When running ad-hoc commands, use your best judgement.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

