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
    <td>minutes</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Number of minutes to pause for.</td>
    </tr>
            <tr>
    <td>prompt</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Optional text to use for the prompt message.</td>
    </tr>
            <tr>
    <td>seconds</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Number of seconds to pause for.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Pause for 5 minutes to build app cache.
    - pause: minutes=5
    
    # Pause until you can verify updates to an application were successful.
    - pause:
    
    # A helpful reminder of what to look out for post-update.
    - pause: prompt="Make sure org.foo.FooOverload exception is not present"



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

