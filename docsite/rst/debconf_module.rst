.. _debconf:


debconf - Configure a .deb package
++++++++++++++++++++++++++++++++++

.. versionadded:: 1.6


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Configure a .deb package using debconf-set-selections. Or just query existing selections.


Requirements (on host that executes module)
-------------------------------------------

  * debconf
  * debconf-utils


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
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Name of package to configure.</div></br>
        <div style="font-size: small;">aliases: pkg<div></td></tr>
            <tr>
    <td>question<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A debconf configuration setting</div></br>
        <div style="font-size: small;">aliases: setting, selection<div></td></tr>
            <tr>
    <td>unseen<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Do not set 'seen' flag when pre-seeding</div></td></tr>
            <tr>
    <td>value<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Value to set the configuration to</div></br>
        <div style="font-size: small;">aliases: answer<div></td></tr>
            <tr>
    <td>vtype<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>string</li><li>password</li><li>boolean</li><li>select</li><li>multiselect</li><li>note</li><li>error</li><li>title</li><li>text</li><li>seen</li></ul></td>
        <td><div>The type of the value supplied.</div><div><code>seen</code> was added in 2.2.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Set default locale to fr_FR.UTF-8
    debconf: name=locales question='locales/default_environment_locale' value=fr_FR.UTF-8 vtype='select'
    
    # set to generate locales:
    debconf: name=locales question='locales/locales_to_be_generated'  value='en_US.UTF-8 UTF-8, fr_FR.UTF-8 UTF-8' vtype='multiselect'
    
    # Accept oracle license
    debconf: name='oracle-java7-installer' question='shared/accepted-oracle-license-v1-1' value='true' vtype='select'
    
    # Specifying package you can register/return the list of questions and current values
    debconf: name='tzdata'


Notes
-----

.. note:: This module requires the command line debconf tools.
.. note:: A number of questions have to be answered (depending on the package). Use 'debconf-show <package>' on any Debian or derivative with the package installed to see questions/settings available.
.. note:: Some distros will always record tasks involving the setting of passwords as changed. This is due to debconf-get-selections masking passwords.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

