.. _django_manage:


django_manage - Manages a Django application.
+++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manages a Django application using the *manage.py* application frontend to *django-admin*. With the *virtualenv* parameter, all management commands will be executed by the given *virtualenv* installation.


Requirements (on host that executes module)
-------------------------------------------

  * virtualenv
  * django


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
    <td>app_path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The path to the root of the Django application where <b>manage.py</b> lives.</div></td></tr>
            <tr>
    <td>apps<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of space-delimited apps to target. Used by the 'test' command.</div></td></tr>
            <tr>
    <td>cache_table<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the table used for database-backed caching. Used by the 'createcachetable' command.</div></td></tr>
            <tr>
    <td>command<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>cleanup</li><li>collectstatic</li><li>flush</li><li>loaddata</li><li>migrate</li><li>runfcgi</li><li>syncdb</li><li>test</li><li>validate</li></ul></td>
        <td><div>The name of the Django management command to run. Built in commands are cleanup, collectstatic, flush, loaddata, migrate, runfcgi, syncdb, test, and validate.</div><div>Other commands can be entered, but will fail if they're unknown to Django.  Other commands that may prompt for user input should be run with the <em>--noinput</em> flag.</div></td></tr>
            <tr>
    <td>database<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The database to target. Used by the 'createcachetable', 'flush', 'loaddata', and 'syncdb' commands.</div></td></tr>
            <tr>
    <td>failfast<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Fail the command immediately if a test fails. Used by the 'test' command.</div></td></tr>
            <tr>
    <td>fixtures<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A space-delimited list of fixture file names to load in the database. <b>Required</b> by the 'loaddata' command.</div></td></tr>
            <tr>
    <td>link<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Will create links to the files instead of copying them, you can only use this parameter with 'collectstatic' command</div></td></tr>
            <tr>
    <td>merge<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Will run out-of-order or missing migrations as they are not rollback migrations, you can only use this parameter with 'migrate' command</div></td></tr>
            <tr>
    <td>pythonpath<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A directory to add to the Python path. Typically used to include the settings module if it is located external to the application directory.</div></td></tr>
            <tr>
    <td>settings<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The Python path to the application's settings module, such as 'myapp.settings'.</div></td></tr>
            <tr>
    <td>skip<br/><div style="font-size: small;"> (added in 1.3)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Will skip over out-of-order missing migrations, you can only use this parameter with <em>migrate</em></div></td></tr>
            <tr>
    <td>virtualenv<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>An optional path to a <em>virtualenv</em> installation to use while running the manage application.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Run cleanup on the application installed in 'django_dir'.
    - django_manage: command=cleanup app_path={{ django_dir }}
    
    # Load the initial_data fixture into the application
    - django_manage: command=loaddata app_path={{ django_dir }} fixtures={{ initial_data }}
    
    # Run syncdb on the application
    - django_manage: >
          command=syncdb
          app_path={{ django_dir }}
          settings={{ settings_app_name }}
          pythonpath={{ settings_dir }}
          virtualenv={{ virtualenv_dir }}
    
    # Run the SmokeTest test case from the main app. Useful for testing deploys.
    - django_manage: command=test app_path={{ django_dir }} apps=main.SmokeTest
    
    # Create an initial superuser.
    - django_manage: command="createsuperuser --noinput --username=admin --email=admin@example.com" app_path={{ django_dir }}


Notes
-----

.. note:: *virtualenv* (http://www.virtualenv.org) must be installed on the remote host if the virtualenv parameter is specified.
.. note:: This module will create a virtualenv if the virtualenv parameter is specified and a virtualenv does not already exist at the given location.
.. note:: This module assumes English error messages for the 'createcachetable' command to detect table existence, unfortunately.
.. note:: To be able to use the migrate command with django versions < 1.7, you must have south installed and added as an app in your settings.
.. note:: To be able to use the collectstatic command, you must have enabled staticfiles in your settings.
.. note:: As of ansible 2.x, your *manage.py* application must be executable (rwxr-xr-x), and must have a valid *shebang*, i.e. "#!/usr/bin/env python", for invoking the appropriate Python interpreter.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

