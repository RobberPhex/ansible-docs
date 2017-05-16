.. _debconf:


debconf - Configure a .deb package
++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Configure a .deb package using debconf-set-selections. Or just query existing selections.

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
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of package to configure.</td>
    </tr>
            <tr>
    <td>question</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A debconf configuration setting</td>
    </tr>
            <tr>
    <td>unseen</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Do not set 'seen' flag when pre-seeding</td>
    </tr>
            <tr>
    <td>value</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Value to set the configuration to</td>
    </tr>
            <tr>
    <td>vtype</td>
    <td>no</td>
    <td></td>
        <td><ul><li>string</li><li>password</li><li>boolean</li><li>select</li><li>multiselect</li><li>note</li><li>error</li><li>title</li><li>text</li></ul></td>
        <td>The type of the value supplied</td>
    </tr>
        </table>


.. note:: Requires debconf


.. note:: Requires debconf-utils


Examples
--------

.. raw:: html

    <br/>


::

    # Set default locale to fr_FR.UTF-8
    debconf: name=locales question='locales/default_environment_locale' value=fr_FR.UTF-8 vtype='select'
    
    # set to generate locales:
    debconf: name=locales question='locales/locales_to_be_generated'  value='en_US.UTF-8 UTF-8, fr_FR.UTF-8 UTF-8' vtype='multiselect'
    
    # Accept oracle license
    debconf: name='oracle-java7-installer' question='shared/accepted-oracle-license-v1-1' value='true' vtype='select'
    
    # Specifying package you can register/return the list of questions and current values
    debconf: name='tzdata'

.. note:: This module requires the command line debconf tools.
.. note:: A number of questions have to be answered (depending on the package). Use 'debconf-show <package>' on any Debian or derivative with the package installed to see questions/settings available.


    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

