.. _cpanm:


cpanm - Manages Perl library dependencies.
++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

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
    <td>from_path</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The local directory from where to install</td>
    </tr>
            <tr>
    <td>locallib</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Specify the install base to install modules</td>
    </tr>
            <tr>
    <td>mirror</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Specifies the base URL for the CPAN mirror to use</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The name of the Perl library to install. You may use the "full distribution path", e.g.  MIYAGAWA/Plack-0.99_05.tar.gz</td>
    </tr>
            <tr>
    <td>notest</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Do not run unit tests</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <p>Install <em>Dancer</em> perl package.</p>    <p>
    <pre>
    cpanm: name=Dancer
    </pre>
    </p>
    <p>Install version 0.99_05 of the <em>Plack</em> perl package.</p>    <p>
    <pre>
    cpanm: name=MIYAGAWA/Plack-0.99_05.tar.gz
    </pre>
    </p>
    <p>Install <em>Dancer</em> (<a href='http://perldancer.org/'>http://perldancer.org/</a>) into the specified <em>locallib</em></p>    <p>
    <pre>
    cpanm: name=Dancer locallib=/srv/webapps/my_app/extlib
    </pre>
    </p>
    <p>Install perl dependencies from local directory.</p>    <p>
    <pre>
    cpanm: from_path=/srv/webapps/my_app/src/
    </pre>
    </p>
    <p>Install <em>Dancer</em> perl package without running the unit tests in indicated <em>locallib</em>.</p>    <p>
    <pre>
    cpanm: name=Dancer notest=True locallib=/srv/webapps/my_app/extlib
    </pre>
    </p>
    <p>Install <em>Dancer</em> perl package from a specific mirror</p>    <p>
    <pre>
    cpanm: name=Dancer mirror=http://cpan.cpantesters.org/
    </pre>
    </p>
    <br/>


.. note:: Please note that http://search.cpan.org/dist/App-cpanminus/bin/cpanm, cpanm must be installed on the remote host.


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

