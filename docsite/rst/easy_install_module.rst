.. _easy_install:


easy_install - Installs Python libraries
++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Installs Python libraries, optionally in a *virtualenv*


Requirements (on host that executes module)
-------------------------------------------

  * virtualenv


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
    <td>executable<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The explicit executable or a pathname to the executable to be used to run easy_install for a specific version of Python installed in the system. For example <code>easy_install-3.3</code>, if there are both Python 2.7 and 3.3 installations in the system and you want to run easy_install for the Python 3.3 installation.</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A Python library name</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>latest</li></ul></td>
        <td><div>The desired state of the library. <code>latest</code> ensures that the latest version is installed.</div></td></tr>
            <tr>
    <td>virtualenv<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>an optional <em>virtualenv</em> directory path to install into. If the <em>virtualenv</em> does not exist, it is created automatically</div></td></tr>
            <tr>
    <td>virtualenv_command<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>virtualenv</td>
        <td><ul></ul></td>
        <td><div>The command to create the virtual environment with. For example <code>pyvenv</code>, <code>virtualenv</code>, <code>virtualenv2</code>.</div></td></tr>
            <tr>
    <td>virtualenv_site_packages<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Whether the virtual environment will inherit packages from the global site-packages directory.  Note that if this setting is changed on an already existing virtual environment it will not have any effect, the environment must be deleted and newly created.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Examples from Ansible Playbooks
    - easy_install: name=pip state=latest
    
    # Install Bottle into the specified virtualenv.
    - easy_install: name=bottle virtualenv=/webapps/myapp/venv


Notes
-----

.. note:: Please note that the :ref:`easy_install <easy_install>` module can only install Python libraries. Thus this module is not able to remove libraries. It is generally recommended to use the :ref:`pip <pip>` module which you can first install using :ref:`easy_install <easy_install>`.
.. note:: Also note that *virtualenv* must be installed on the remote host if the ``virtualenv`` parameter is specified.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

