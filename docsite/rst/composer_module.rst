.. _composer:


composer - Dependency Manager for PHP
+++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Composer is a tool for dependency management in PHP. It allows you to declare the dependent libraries your project needs and it will install them in your project for you

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
    <td>command</td>
    <td>no</td>
    <td>install</td>
        <td><ul></ul></td>
        <td>Composer command like "install", "update" and so on (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>no_dev</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Disables installation of require-dev packages ( see --no-dev )</td>
    </tr>
            <tr>
    <td>no_plugins</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Disables all plugins ( see --no-plugins )</td>
    </tr>
            <tr>
    <td>no_scripts</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Skips the execution of all scripts defined in composer.json ( see --no-scripts )</td>
    </tr>
            <tr>
    <td>optimize_autoloader</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Optimize autoloader during autoloader dump ( see --optimize-autoloader ). Convert PSR-0/4 autoloading to classmap to get a faster autoloader. This is recommended especially for production, but can take a bit of time to run so it is currently not done by default.</td>
    </tr>
            <tr>
    <td>prefer_dist</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Forces installation from package dist even for dev versions ( see --prefer-dist )</td>
    </tr>
            <tr>
    <td>prefer_source</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>Forces installation from package sources when possible ( see --prefer-source )</td>
    </tr>
            <tr>
    <td>working_dir</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Directory of your project ( see --working-dir )</td>
    </tr>
        </table>


.. note:: Requires php


.. note:: Requires composer installed in bin path (recommended /usr/local/bin)


Examples
--------

.. raw:: html

    <br/>


::

    # Downloads and installs all the libs and dependencies outlined in the /path/to/project/composer.lock
    - composer: command=install working_dir=/path/to/project

.. note:: Default options that are always appended in each execution are --no-ansi, --no-progress, and --no-interaction


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

