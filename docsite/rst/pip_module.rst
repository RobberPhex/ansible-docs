.. _pip:


pip - Manages Python library dependencies.
++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Manage Python library dependencies. To use this module, one of the following keys is required: ``name`` or ``requirements``.

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
    <td>chdir</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>cd into this directory before running the command (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>executable</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The explicit executable or a pathname to the executable to be used to run pip for a specific version of Python installed in the system. For example <code>pip-3.3</code>, if there are both Python 2.7 and 3.3 installations in the system and you want to run pip for the Python 3.3 installation. (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>extra_args</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Extra arguments passed to pip. (added in Ansible 1.0)</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The name of a Python library to install or the url of the remote package.</td>
    </tr>
            <tr>
    <td>requirements</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The path to a pip requirements file</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>latest</li></ul></td>
        <td>The state of module</td>
    </tr>
            <tr>
    <td>version</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The version number to install of the Python library specified in the <em>name</em> parameter</td>
    </tr>
            <tr>
    <td>virtualenv</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>An optional path to a <em>virtualenv</em> directory to install into</td>
    </tr>
            <tr>
    <td>virtualenv_command</td>
    <td>no</td>
    <td>virtualenv</td>
        <td><ul></ul></td>
        <td>The command or a pathname to the command to create the virtual environment with. For example <code>pyvenv</code>, <code>virtualenv</code>, <code>virtualenv2</code>, <code>~/bin/virtualenv</code>, <code>/usr/local/bin/virtualenv</code>.</td>
    </tr>
            <tr>
    <td>virtualenv_site_packages</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Whether the virtual environment will inherit packages from the global site-packages directory.  Note that if this setting is changed on an already existing virtual environment it will not have any effect, the environment must be deleted and newly created. (added in Ansible 1.0)</td>
    </tr>
        </table>


.. note:: Requires virtualenv


.. note:: Requires pip


Examples
--------

.. raw:: html

    <br/>


::

    # Install (Bottle) python package.
    - pip: name=bottle
    
    # Install (Bottle) python package on version 0.11.
    - pip: name=bottle version=0.11
    
    # Install (MyApp) using one of the remote protocols (bzr+,hg+,git+,svn+). You do not have to supply '-e' option in extra_args.
    - pip: name='svn+http://myrepo/svn/MyApp#egg=MyApp'
    
    # Install (Bottle) into the specified (virtualenv), inheriting none of the globally installed modules
    - pip: name=bottle virtualenv=/my_app/venv
    
    # Install (Bottle) into the specified (virtualenv), inheriting globally installed modules
    - pip: name=bottle virtualenv=/my_app/venv virtualenv_site_packages=yes
    
    # Install (Bottle) into the specified (virtualenv), using Python 2.7
    - pip: name=bottle virtualenv=/my_app/venv virtualenv_command=virtualenv-2.7
    
    # Install specified python requirements.
    - pip: requirements=/my_app/requirements.txt
    
    # Install specified python requirements in indicated (virtualenv).
    - pip: requirements=/my_app/requirements.txt virtualenv=/my_app/venv
    
    # Install specified python requirements and custom Index URL.
    - pip: requirements=/my_app/requirements.txt extra_args='-i https://example.com/pypi/simple'
    
    # Install (Bottle) for Python 3.3 specifically,using the 'pip-3.3' executable.
    - pip: name=bottle executable=pip-3.3

.. note:: Please note that virtualenv (http://www.virtualenv.org/) must be installed on the remote host if the virtualenv parameter is specified.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

