.. _cpanm:


cpanm - Manages Perl library dependencies.
++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage Perl library dependencies.




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
    <td>from_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The local directory from where to install</div></td></tr>
            <tr>
    <td>installdeps<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Only install dependencies</div></td></tr>
            <tr>
    <td>locallib<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specify the install base to install modules</div></td></tr>
            <tr>
    <td>mirror<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Specifies the base URL for the CPAN mirror to use</div></td></tr>
            <tr>
    <td>mirror_only<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use the mirror's index file instead of the CPAN Meta DB</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the Perl library to install. You may use the "full distribution path", e.g.  MIYAGAWA/Plack-0.99_05.tar.gz</div></br>
        <div style="font-size: small;">aliases: pkg<div></td></tr>
            <tr>
    <td>notest<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Do not run unit tests</div></td></tr>
            <tr>
    <td>system_lib<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Use this if you want to install modules to the system perl include path. You must be root or have "passwordless" sudo for this to work.</div><div>This uses the cpanm commandline option '--sudo', which has nothing to do with ansible privilege escalation.</div></br>
        <div style="font-size: small;">aliases: use_sudo<div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # install Dancer perl package
    - cpanm: name=Dancer
    
    # install version 0.99_05 of the Plack perl package
    - cpanm: name=MIYAGAWA/Plack-0.99_05.tar.gz
    
    # install Dancer into the specified locallib
    - cpanm: name=Dancer locallib=/srv/webapps/my_app/extlib
    
    # install perl dependencies from local directory
    - cpanm: from_path=/srv/webapps/my_app/src/
    
    # install Dancer perl package without running the unit tests in indicated locallib
    - cpanm: name=Dancer notest=True locallib=/srv/webapps/my_app/extlib
    
    # install Dancer perl package from a specific mirror
    - cpanm: name=Dancer mirror=http://cpan.cpantesters.org/
    
    # install Dancer perl package into the system root path
    - cpanm: name=Dancer system_lib=yes


Notes
-----

.. note:: Please note that http://search.cpan.org/dist/App-cpanminus/bin/cpanm, cpanm must be installed on the remote host.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

