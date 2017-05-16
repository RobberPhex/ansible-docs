.. _win_chocolatey:


win_chocolatey - Installs packages using chocolatey
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.9

Installs packages using Chocolatey (http://chocolatey.org/). If Chocolatey is missing from the system, the module will install it. List of packages can be found at http://chocolatey.org/packages

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
    <td>force</td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td>Forces install of the package (even if it already exists). Using Force will cause ansible to always report that a change was made</td>
    </tr>
            <tr>
    <td>logPath</td>
    <td>no</td>
    <td>c:\ansible-playbook.log</td>
        <td><ul></ul></td>
        <td>Where to log command output to</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Name of the package to be installed</td>
    </tr>
            <tr>
    <td>showlog</td>
    <td>no</td>
    <td></td>
        <td><ul><li>True</li><li>False</li></ul></td>
        <td>Outputs the chocolatey log inside a chocolatey_log property.</td>
    </tr>
            <tr>
    <td>source</td>
    <td>no</td>
    <td>chocolatey</td>
        <td><ul><li>chocolatey</li><li>ruby</li><li>webpi</li><li>windowsfeatures</li></ul></td>
        <td>Which source to install from</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>State of the package on the system</td>
    </tr>
            <tr>
    <td>version</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Specific version of the package to be installedIgnored when state == 'absent'</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

      # Install git
      win_chocolatey:
        name: git
    
      # Install notepadplusplus version 6.6
      win_chocolatey:
        name: notepadplusplus.install
        version: 6.6
    
      # Uninstall git
      win_chocolatey:
        name: git
        state: absent
    
      # Install Application Request Routing v3 from webpi
      # Logically, this requires that you install IIS first (see win_feature)
      # To find a list of packages available via webpi source, `choco list -source webpi`
      win_chocolatey:
        name: ARRv3
        source: webpi



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

