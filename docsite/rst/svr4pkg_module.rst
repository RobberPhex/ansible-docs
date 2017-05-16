.. _svr4pkg:


svr4pkg - Manage Solaris SVR4 packages
++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Manages SVR4 packages on Solaris 10 and 11.
These were the native packages on Solaris <= 10 and are available as a legacy feature in Solaris 11.
Note that this is a very basic packaging system. It will not enforce dependencies on install or remove.

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
    <td>category</td>
    <td>no</td>
    <td></td>
        <td><ul><li>true</li><li>false</li></ul></td>
        <td>Install/Remove category instead of a single package. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Package name, e.g. <code>SUNWcsr</code></td>
    </tr>
            <tr>
    <td>proxy</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>HTTP[s] proxy to be used if <code>src</code> is a URL.</td>
    </tr>
            <tr>
    <td>response_file</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Specifies the location of a response file to be used if package expects input on install. (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>src</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Specifies the location to install the package from. Required when <code>state=present</code>.Can be any path acceptable to the <code>pkgadd</code> command's <code>-d</code> option. e.g.: <code>somefile.pkg</code>, <code>/dir/with/pkgs</code>, <code>http:/server/mypkgs.pkg</code>.If using a file or directory, they must already be accessible by the host. See the <span class='module'>copy</span> module for a way to get them there.</td>
    </tr>
            <tr>
    <td>state</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td>Whether to install (<code>present</code>), or remove (<code>absent</code>) a package.If the package is to be installed, then <em>src</em> is required.The SVR4 package system doesn't provide an upgrade operation. You need to uninstall the old, then install the new package.</td>
    </tr>
            <tr>
    <td>zone</td>
    <td>no</td>
    <td>all</td>
        <td><ul><li>current</li><li>all</li></ul></td>
        <td>Whether to install the package only in the current zone, or install it into all zones.The installation into all zones works only if you are working with the global zone. (added in Ansible 1.6)</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Install a package from an already copied file
    - svr4pkg: name=CSWcommon src=/tmp/cswpkgs.pkg state=present
    
    # Install a package directly from an http site
    - svr4pkg: name=CSWpkgutil src=http://get.opencsw.org/now state=present zone=current
    
    # Install a package with a response file
    - svr4pkg: name=CSWggrep src=/tmp/third-party.pkg response_file=/tmp/ggrep.response state=present
    
    # Ensure that a package is not installed.
    - svr4pkg: name=SUNWgnome-sound-recorder state=absent
    
    # Ensure that a category is not installed.
    - svr4pkg: name=FIREFOX state=absent category=true



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

