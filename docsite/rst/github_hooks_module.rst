.. _github_hooks:


github_hooks - Manages github service hooks.
++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

Adds service hooks and removes service hooks that have an error status.

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
    <td>action</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>create</li><li>cleanall</li></ul></td>
        <td>This tells the githooks module what you want it to do.</td>
    </tr>
            <tr>
    <td>hookurl</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>When creating a new hook, this is the url that you want github to post to. It is only required when creating a new hook.</td>
    </tr>
            <tr>
    <td>oauthkey</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The oauth key provided by github. It can be found/generated on github under "Edit Your Profile" &gt;&gt; "Applications" &gt;&gt; "Personal Access Tokens"</td>
    </tr>
            <tr>
    <td>repo</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>This is the API url for the repository you want to manage hooks for. It should be in the form of: https://api.github.com/repos/user:/repo:. Note this is different than the normal repo url.</td>
    </tr>
            <tr>
    <td>user</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Github username.</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, SSL certificates for the target repo will not be validated. This should only be used on personally controlled sites using self-signed certificates.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Example creating a new service hook. It ignores duplicates.
    - github_hooks: action=create hookurl=http://11.111.111.111:2222 user={{ gituser }} oauthkey={{ oauthkey }} repo=https://api.github.com/repos/pcgentry/Github-Auto-Deploy
    
    # Cleaning all hooks for this repo that had an error on the last update. Since this works for all hooks in a repo it is probably best that this would be called from a handler.
    - local_action: github_hooks action=cleanall user={{ gituser }} oauthkey={{ oauthkey }} repo={{ repo }}



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

