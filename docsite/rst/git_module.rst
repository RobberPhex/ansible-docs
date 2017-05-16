.. _git:


git - Deploy software (or files) from git checkouts
+++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


Manage *git* checkouts of repositories to deploy files or software.

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
    <td>accept_hostkey</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>if <code>yes</code>, adds the hostkey for the repo url if not already added. If ssh_args contains "-o StrictHostKeyChecking=no", this parameter is ignored. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>bare</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>if <code>yes</code>, repository will be created as a bare repo, otherwise it will be a standard repo with a workspace. (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>clone</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, do not clone the repository if it does not exist locally (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>depth</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Create a shallow clone with a history truncated to the specified number or revisions. The minimum possible value is <code>1</code>, otherwise ignored. (added in Ansible 1.2)</td>
    </tr>
            <tr>
    <td>dest</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Absolute path of where the repository should be checked out to. This parameter is required, unless <code>clone</code> is set to <code>no</code> This change was made in version 1.8.3. Prior to this version, the <code>dest</code> parameter was always required.</td>
    </tr>
            <tr>
    <td>executable</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Path to git executable to use. If not supplied, the normal mechanism for resolving binary paths will be used. (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>force</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>yes</code>, any modified files in the working repository will be discarded.  Prior to 0.7, this was always 'yes' and could not be disabled.  Prior to 1.9, the default was `yes` (added in Ansible 0.7)</td>
    </tr>
            <tr>
    <td>key_file</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>Specify an optional private key file to use for the checkout. (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>recursive</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>if <code>no</code>, repository will be cloned without the --recursive option, skipping sub-modules. (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>reference</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Reference repository (see "git clone --reference ...") (added in Ansible 1.4)</td>
    </tr>
            <tr>
    <td>refspec</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Add an additional refspec to be fetched. If version is set to a <em>SHA-1</em> not reachable from any branch or tag, this option may be necessary to specify the ref containing the <em>SHA-1</em>. Uses the same syntax as the 'git fetch' command. An example value could be "refs/meta/config". (added in Ansible 1.9)</td>
    </tr>
            <tr>
    <td>remote</td>
    <td>no</td>
    <td>origin</td>
        <td><ul></ul></td>
        <td>Name of the remote.</td>
    </tr>
            <tr>
    <td>repo</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>git, SSH, or HTTP protocol address of the git repository.</td>
    </tr>
            <tr>
    <td>ssh_opts</td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td>Creates a wrapper script and exports the path as GIT_SSH which git then automatically uses to override ssh arguments. An example value could be "-o StrictHostKeyChecking=no" (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>track_submodules</td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>if <code>yes</code>, submodules will track the latest commit on their master branch (or other branch specified in .gitmodules).  If <code>no</code>, submodules will be kept at the revision specified by the main project. This is equivalent to specifying the --remote flag to git submodule update. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>update</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, do not retrieve new revisions from the origin repository (added in Ansible 1.2)</td>
    </tr>
            <tr>
    <td>version</td>
    <td>no</td>
    <td>HEAD</td>
        <td><ul></ul></td>
        <td>What version of the repository to check out.  This can be the full 40-character <em>SHA-1</em> hash, the literal string <code>HEAD</code>, a branch name, or a tag name.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Example git checkout from Ansible Playbooks
    - git: repo=git://foosball.example.org/path/to/repo.git
           dest=/srv/checkout
           version=release-0.22
    
    # Example read-write git checkout from github
    - git: repo=ssh://git@github.com/mylogin/hello.git dest=/home/mylogin/hello
    
    # Example just ensuring the repo checkout exists
    - git: repo=git://foosball.example.org/path/to/repo.git dest=/srv/checkout update=no
    
    # Example just get information about the repository whether or not it has
    # already been cloned locally.
    - git: repo=git://foosball.example.org/path/to/repo.git dest=/srv/checkout clone=no update=no
    
    # Example checkout a github repo and use refspec to fetch all pull requests
    - git: repo=https://github.com/ansible/ansible-examples.git dest=/src/ansible-examples refspec=+refs/pull/*:refs/heads/*

.. note:: If the task seems to be hanging, first verify remote host is in ``known_hosts``. SSH will prompt user to authorize the first contact with a remote host.  To avoid this prompt, one solution is to add the remote host public key in ``/etc/ssh/ssh_known_hosts`` before calling the git module, with the following command: ssh-keyscan -H remote_host.com >> /etc/ssh/ssh_known_hosts.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

