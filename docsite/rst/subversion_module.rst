.. _subversion:


subversion - Deploys a subversion repository.
+++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Deploy given repository URL / revision to dest. If dest exists, update to the specified revision, otherwise perform a checkout.

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
    <td>dest</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Absolute path where the repository should be deployed.</td>
    </tr>
            <tr>
    <td>executable</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Path to svn executable to use. If not supplied, the normal mechanism for resolving binary paths will be used. (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>export</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>yes</code>, do export instead of checkout/update. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>force</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>yes</code>, modified files will be discarded. If <code>no</code>, module will fail if it encounters modified files.</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>--password parameter passed to svn.</td>
    </tr>
            <tr>
    <td>repo</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The subversion URL to the repository.</td>
    </tr>
            <tr>
    <td>revision</td>
    <td>no</td>
    <td>HEAD</td>
        <td><ul></ul></td>
        <td>Specific revision to checkout.</td>
    </tr>
            <tr>
    <td>username</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>--username parameter passed to svn.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Checkout subversion repository to specified folder.
    - subversion: repo=svn+ssh://an.example.org/path/to/repo dest=/src/checkout
    
    # Export subversion directory to folder
    - subversion: repo=svn+ssh://an.example.org/path/to/repo dest=/src/export export=True

.. note:: Requires *svn* to be installed on the client.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

