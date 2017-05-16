.. _layman:


layman - Manage Gentoo overlays
+++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Uses Layman to manage an additional repositories for the Portage package manager on Gentoo Linux. Please note that Layman must be installed on a managed node prior using this module.

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
    <td>list_url</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>An URL of the alternative overlays list that defines the overlay to install. This list will be fetched and saved under <code>${overlay_defs}</code>/${name}.xml), where <code>overlay_defs</code> is readed from the Layman's configuration.</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The overlay id to install, synchronize, or uninstall. Use 'ALL' to sync all of the installed overlays (can be used only when <code>state=updated</code>).</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>updated</li></ul></td>
        <td>Whether to install (<code>present</code>), sync (<code>updated</code>), or uninstall (<code>absent</code>) the overlay.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Install the overlay 'mozilla' which is on the central overlays list.
    - layman: name=mozilla
    
    # Install the overlay 'cvut' from the specified alternative list.
    - layman: name=cvut list_url=http://raw.github.com/cvut/gentoo-overlay/master/overlay.xml
    
    # Update (sync) the overlay 'cvut', or install if not installed yet.
    - layman: name=cvut list_url=http://raw.github.com/cvut/gentoo-overlay/master/overlay.xml state=updated
    
    # Update (sync) all of the installed overlays.
    - layman: name=ALL state=updated
    
    # Uninstall the overlay 'cvut'.
    - layman: name=cvut state=absent



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

