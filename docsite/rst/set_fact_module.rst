.. _set_fact:


set_fact - Set host facts from a task
+++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.2

This module allows setting new variables.  Variables are set on a host-by-host basis just like facts discovered by the setup module.
These variables will survive between plays.

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
    <td>key_value</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The <code>set_fact</code> module takes key=value pairs as variables to set in the playbook scope. Or alternatively, accepts complex arguments using the <code>args:</code> statement.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Example setting host facts using key=value pairs
    - set_fact: one_fact="something" other_fact="{{ local_var * 2 }}"
    
    # Example setting host facts using complex arguments
    - set_fact:
         one_fact: something
         other_fact: "{{ local_var * 2 }}"
    
    # As of 1.8, Ansible will convert boolean strings ('true', 'false', 'yes', 'no')
    # to proper boolean values when using the key=value syntax, however it is still
    # recommended that booleans be set using the complex argument style:
    - set_fact:
        one_fact: true
        other_fact: false
    



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

