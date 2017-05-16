.. _django_manage:


django_manage - Manages a Django application.
+++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.1

Manages a Django application using the *manage.py* application frontend to *django-admin*. With the *virtualenv* parameter, all management commands will be executed by the given *virtualenv* installation.

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
    <td>app_path</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The path to the root of the Django application where <b>manage.py</b> lives.</td>
    </tr>
            <tr>
    <td>apps</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A list of space-delimited apps to target. Used by the 'test' command.</td>
    </tr>
            <tr>
    <td>cache_table</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The name of the table used for database-backed caching. Used by the 'createcachetable' command.</td>
    </tr>
            <tr>
    <td>command</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>cleanup</li><li>collectstatic</li><li>flush</li><li>loaddata</li><li>migrate</li><li>runfcgi</li><li>syncdb</li><li>test</li><li>validate</li></ul></td>
        <td>The name of the Django management command to run. Built in commands are cleanup, collectstatic, flush, loaddata, migrate, runfcgi, syncdb, test, and validate. Other commands can be entered, but will fail if they're unknown to Django.</td>
    </tr>
            <tr>
    <td>database</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The database to target. Used by the 'createcachetable', 'flush', 'loaddata', and 'syncdb' commands.</td>
    </tr>
            <tr>
    <td>failfast</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Fail the command immediately if a test fails. Used by the 'test' command.</td>
    </tr>
            <tr>
    <td>fixtures</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A space-delimited list of fixture file names to load in the database. <b>Required</b> by the 'loaddata' command.</td>
    </tr>
            <tr>
    <td>link</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Will create links to the files instead of copying them, you can only use this parameter with 'collectstatic' command (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>merge</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Will run out-of-order or missing migrations as they are not rollback migrations, you can only use this parameter with 'migrate' command (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>pythonpath</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A directory to add to the Python path. Typically used to include the settings module if it is located external to the application directory.</td>
    </tr>
            <tr>
    <td>settings</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The Python path to the application's settings module, such as 'myapp.settings'.</td>
    </tr>
            <tr>
    <td>skip</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Will skip over out-of-order missing migrations, you can only use this parameter with <em>migrate</em> (added in Ansible 1.3)</td>
    </tr>
            <tr>
    <td>virtualenv</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>An optional path to a <em>virtualenv</em> installation to use while running the manage application.</td>
    </tr>
        </table>


.. note:: Requires virtualenv


.. note:: Requires django


Examples
--------

.. raw:: html

    <br/>


::

    # Run cleanup on the application installed in 'django_dir'.
    - django_manage: command=cleanup app_path={{ django_dir }}
    
    # Load the initial_data fixture into the application
    - django_manage: command=loaddata app_path={{ django_dir }} fixtures={{ initial_data }}
    
    #Run syncdb on the application
    - django_manage: >
          command=syncdb
          app_path={{ django_dir }}
          settings={{ settings_app_name }}
          pythonpath={{ settings_dir }}
          virtualenv={{ virtualenv_dir }}
    
    #Run the SmokeTest test case from the main app. Useful for testing deploys.
    - django_manage: command=test app_path=django_dir apps=main.SmokeTest

.. note:: *virtualenv* (http://www.virtualenv.org) must be installed on the remote host if the virtualenv parameter is specified.
.. note:: This module will create a virtualenv if the virtualenv parameter is specified and a virtualenv does not already exist at the given location.
.. note:: This module assumes English error messages for the 'createcachetable' command to detect table existence, unfortunately.
.. note:: To be able to use the migrate command, you must have south installed and added as an app in your settings
.. note:: To be able to use the collectstatic command, you must have enabled staticfiles in your settings


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

