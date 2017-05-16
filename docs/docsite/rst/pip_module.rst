.. _pip:


pip - Manages Python library dependencies.
++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Manage Python library dependencies. To use this module, one of the following keys is required: ``name`` or ``requirements``.


Requirements (on host that executes module)
-------------------------------------------

  * virtualenv
  * pip


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
                <tr><td>chdir<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>cd into this directory before running the command</div>        </td></tr>
                <tr><td>editable<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Pass the editable flag for versioning URLs.</div>        </td></tr>
                <tr><td>executable<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The explicit executable or a pathname to the executable to be used to run pip for a specific version of Python installed in the system. For example <code>pip-3.3</code>, if there are both Python 2.7 and 3.3 installations in the system and you want to run pip for the Python 3.3 installation. It cannot be specified together with the 'virtualenv' parameter (added in 2.1). By default, it will take the appropriate version for the python interpreter use by ansible, e.g. pip3 on python 3, and pip2 or pip on python 2.</div>        </td></tr>
                <tr><td>extra_args<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Extra arguments passed to pip.</div>        </td></tr>
                <tr><td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The name of a Python library to install or the url of the remote package.</div><div>As of 2.2 you can supply a list of names.</div>        </td></tr>
                <tr><td>requirements<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The path to a pip requirements file, which should be local to the remote system. File can be specified as a relative path if using the chdir option.</div>        </td></tr>
                <tr><td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>latest</li><li>forcereinstall</li></ul></td>
        <td><div>The state of module</div><div>The 'forcereinstall' option is only available in Ansible 2.1 and above.</div>        </td></tr>
                <tr><td>umask<br/><div style="font-size: small;"> (added in 2.1)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The system umask to apply before installing the pip package. This is useful, for example, when installing on systems that have a very restrictive umask by default (e.g., 0077) and you want to pip install packages which are to be used by all users. Note that this requires you to specify desired umask mode in octal, with a leading 0 (e.g., 0077).</div>        </td></tr>
                <tr><td>version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The version number to install of the Python library specified in the <em>name</em> parameter</div>        </td></tr>
                <tr><td>virtualenv<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>An optional path to a <em>virtualenv</em> directory to install into. It cannot be specified together with the 'executable' parameter (added in 2.1). If the virtualenv does not exist, it will be created before installing packages. The optional virtualenv_site_packages, virtualenv_command, and virtualenv_python options affect the creation of the virtualenv.</div>        </td></tr>
                <tr><td>virtualenv_command<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>virtualenv</td>
        <td></td>
        <td><div>The command or a pathname to the command to create the virtual environment with. For example <code>pyvenv</code>, <code>virtualenv</code>, <code>virtualenv2</code>, <code>~/bin/virtualenv</code>, <code>/usr/local/bin/virtualenv</code>.</div>        </td></tr>
                <tr><td>virtualenv_python<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>The Python executable used for creating the virtual environment. For example <code>python3.5</code>, <code>python2.7</code>. When not specified, the Python version used to run the ansible module is used.</div>        </td></tr>
                <tr><td>virtualenv_site_packages<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether the virtual environment will inherit packages from the global site-packages directory.  Note that if this setting is changed on an already existing virtual environment it will not have any effect, the environment must be deleted and newly created.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Install (Bottle) python package.
    - pip:
        name: bottle
    
    # Install (Bottle) python package on version 0.11.
    - pip:
        name: bottle
        version: 0.11
    
    # Install (MyApp) using one of the remote protocols (bzr+,hg+,git+,svn+). You do not have to supply '-e' option in extra_args.
    - pip:
        name: svn+http://myrepo/svn/MyApp#egg=MyApp
    
    # Install MyApp using one of the remote protocols (bzr+,hg+,git+) in a non editable way.
    - pip:
        name: git+http://myrepo/app/MyApp
        editable: false
    
    # Install (MyApp) from local tarball
    - pip:
        name: file:///path/to/MyApp.tar.gz
    
    # Install (Bottle) into the specified (virtualenv), inheriting none of the globally installed modules
    - pip:
        name: bottle
        virtualenv: /my_app/venv
    
    # Install (Bottle) into the specified (virtualenv), inheriting globally installed modules
    - pip:
        name: bottle
        virtualenv: /my_app/venv
        virtualenv_site_packages: yes
    
    # Install (Bottle) into the specified (virtualenv), using Python 2.7
    - pip:
        name: bottle
        virtualenv: /my_app/venv
        virtualenv_command: virtualenv-2.7
    
    # Install specified python requirements.
    - pip:
        requirements: /my_app/requirements.txt
    
    # Install specified python requirements in indicated (virtualenv).
    - pip:
        requirements: /my_app/requirements.txt
        virtualenv: /my_app/venv
    
    # Install specified python requirements and custom Index URL.
    - pip:
        requirements: /my_app/requirements.txt
        extra_args: -i https://example.com/pypi/simple
    
    # Install (Bottle) for Python 3.3 specifically,using the 'pip-3.3' executable.
    - pip:
        name: bottle
        executable: pip-3.3
    
    # Install (Bottle), forcing reinstallation if it's already installed
    - pip:
        name: bottle
        state: forcereinstall
    
    # Install (Bottle) while ensuring the umask is 0022 (to ensure other users can use it)
    - pip:
        name: bottle
        umask: 0022
      become: True


Notes
-----

.. note::
    - Please note that virtualenv (http://www.virtualenv.org/) must be installed on the remote host if the virtualenv parameter is specified and the virtualenv needs to be created.
    - By default, this module will use the appropriate version of pip for the interpreter used by ansible (e.g. pip3 when using python 3, pip2 otherwise)



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is supported mainly by the community and is curated by core committers.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
