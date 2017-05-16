.. _easy_install:


easy_install - Installs Python libraries
++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Installs Python libraries, optionally in a *virtualenv*

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
        <td>The explicit executable or a pathname to the executable to be used to run easy_install for a specific version of Python installed in the system. For example <code>easy_install-3.3</code>, if there are both Python 2.7 and 3.3 installations in the system and you want to run easy_install for the Python 3.3 installation. (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>A Python library name</td>
    </tr>
            <tr>
    <td>virtualenv</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>an optional <em>virtualenv</em> directory path to install into. If the <em>virtualenv</em> does not exist, it is created automatically</td>
    </tr>
            <tr>
    <td>virtualenv_command</td>
    <td>no</td>
    <td>virtualenv</td>
        <td><ul></ul></td>
        <td>The command to create the virtual environment with. For example <code>pyvenv</code>, <code>virtualenv</code>, <code>virtualenv2</code>. (added in Ansible 1.1)</td>
    </tr>
            <tr>
    <td>virtualenv_site_packages</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Whether the virtual environment will inherit packages from the global site-packages directory.  Note that if this setting is changed on an already existing virtual environment it will not have any effect, the environment must be deleted and newly created. (added in Ansible 1.1)</td>
    </tr>
        </table>


.. note:: Requires virtualenv


Examples
--------

.. raw:: html

    <br/>


::

    # Examples from Ansible Playbooks
    - easy_install: name=pip
    
    # Install Bottle into the specified virtualenv.
    - easy_install: name=bottle virtualenv=/webapps/myapp/venv

.. note:: Please note that the ``easy_install`` module can only install Python libraries. Thus this module is not able to remove libraries. It is generally recommended to use the ``pip`` module which you can first install using ``easy_install``.
.. note:: Also note that *virtualenv* must be installed on the remote host if the ``virtualenv`` parameter is specified.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

