.. _composer:


composer - Dependency Manager for PHP
+++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Composer is a tool for dependency management in PHP. It allows you to declare the dependent libraries your project needs and it will install them in your project for you


Requirements (on host that executes module)
-------------------------------------------

  * php
  * composer installed in bin path (recommended /usr/local/bin)


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
    <td>arguments<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Composer arguments like required package, version and so on</div></td></tr>
            <tr>
    <td>command<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>install</td>
        <td><ul></ul></td>
        <td><div>Composer command like "install", "update" and so on</div></td></tr>
            <tr>
    <td>ignore_platform_reqs<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Ignore php, hhvm, lib-* and ext-* requirements and force the installation even if the local machine does not fulfill these.</div></br>
        <div style="font-size: small;">aliases: ignore-platform-reqs<div></td></tr>
            <tr>
    <td>no_dev<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Disables installation of require-dev packages ( see --no-dev )</div></br>
        <div style="font-size: small;">aliases: no-dev<div></td></tr>
            <tr>
    <td>no_plugins<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Disables all plugins ( see --no-plugins )</div></br>
        <div style="font-size: small;">aliases: no-plugins<div></td></tr>
            <tr>
    <td>no_scripts<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Skips the execution of all scripts defined in composer.json ( see --no-scripts )</div></br>
        <div style="font-size: small;">aliases: no-scripts<div></td></tr>
            <tr>
    <td>optimize_autoloader<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Optimize autoloader during autoloader dump ( see --optimize-autoloader ). Convert PSR-0/4 autoloading to classmap to get a faster autoloader. This is recommended especially for production, but can take a bit of time to run so it is currently not done by default.</div></br>
        <div style="font-size: small;">aliases: optimize-autoloader<div></td></tr>
            <tr>
    <td>prefer_dist<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Forces installation from package dist even for dev versions ( see --prefer-dist )</div></br>
        <div style="font-size: small;">aliases: prefer-dist<div></td></tr>
            <tr>
    <td>prefer_source<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>Forces installation from package sources when possible ( see --prefer-source )</div></br>
        <div style="font-size: small;">aliases: prefer-source<div></td></tr>
            <tr>
    <td>working_dir<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Directory of your project ( see --working-dir )</div></br>
        <div style="font-size: small;">aliases: working-dir<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Downloads and installs all the libs and dependencies outlined in the /path/to/project/composer.lock
    - composer: command=install working_dir=/path/to/project
    
    - composer:
        command: "require"
        arguments: "my/package"
        working_dir: "/path/to/project"
    
    # Clone project and install with all dependencies
    - composer:
        command: "create-project"
        arguments: "package/package /path/to/project ~1.0"
        working_dir: "/path/to/project"
        prefer_dist: "yes"


Notes
-----

.. note:: Default options that are always appended in each execution are --no-ansi, --no-interaction and --no-progress if available.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

