.. _git:


git - Deploy software (or files) from git checkouts
+++++++++++++++++++++++++++++++++++++++++++++++++++



.. contents::
   :local:
   :depth: 1


Synopsis
--------

Manage *git* checkouts of repositories to deploy files or software.


Requirements (on host that executes module)
-------------------------------------------

  * git>=1.7.1 (the command line tool)


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
    <td>accept_hostkey<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>if <code>yes</code>, adds the hostkey for the repo url if not already added. If ssh_opts contains "-o StrictHostKeyChecking=no", this parameter is ignored.</div></td></tr>
            <tr>
    <td>bare<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>if <code>yes</code>, repository will be created as a bare repo, otherwise it will be a standard repo with a workspace.</div></td></tr>
            <tr>
    <td>clone<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, do not clone the repository if it does not exist locally</div></td></tr>
            <tr>
    <td>depth<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Create a shallow clone with a history truncated to the specified number or revisions. The minimum possible value is <code>1</code>, otherwise ignored. Needs <em>git&gt;=1.9.1</em> to work correctly.</div></td></tr>
            <tr>
    <td>dest<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Absolute path of where the repository should be checked out to. This parameter is required, unless <code>clone</code> is set to <code>no</code> This change was made in version 1.8.3. Prior to this version, the <code>dest</code> parameter was always required.</div></td></tr>
            <tr>
    <td>executable<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to git executable to use. If not supplied, the normal mechanism for resolving binary paths will be used.</div></td></tr>
            <tr>
    <td>force<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>yes</code>, any modified files in the working repository will be discarded.  Prior to 0.7, this was always 'yes' and could not be disabled.  Prior to 1.9, the default was `yes`</div></td></tr>
            <tr>
    <td>key_file<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Specify an optional private key file to use for the checkout.</div></td></tr>
            <tr>
    <td>recursive<br/><div style="font-size: small;"> (added in 1.6)</div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>if <code>no</code>, repository will be cloned without the --recursive option, skipping sub-modules.</div></td></tr>
            <tr>
    <td>reference<br/><div style="font-size: small;"> (added in 1.4)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Reference repository (see "git clone --reference ...")</div></td></tr>
            <tr>
    <td>refspec<br/><div style="font-size: small;"> (added in 1.9)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Add an additional refspec to be fetched. If version is set to a <em>SHA-1</em> not reachable from any branch or tag, this option may be necessary to specify the ref containing the <em>SHA-1</em>. Uses the same syntax as the 'git fetch' command. An example value could be "refs/meta/config".</div></td></tr>
            <tr>
    <td>remote<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>origin</td>
        <td><ul></ul></td>
        <td><div>Name of the remote.</div></td></tr>
            <tr>
    <td>repo<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>git, SSH, or HTTP(S) protocol address of the git repository.</div></br>
        <div style="font-size: small;">aliases: name<div></td></tr>
            <tr>
    <td>ssh_opts<br/><div style="font-size: small;"> (added in 1.5)</div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>Creates a wrapper script and exports the path as GIT_SSH which git then automatically uses to override ssh arguments. An example value could be "-o StrictHostKeyChecking=no"</div></td></tr>
            <tr>
    <td>track_submodules<br/><div style="font-size: small;"> (added in 1.8)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>if <code>yes</code>, submodules will track the latest commit on their master branch (or other branch specified in .gitmodules).  If <code>no</code>, submodules will be kept at the revision specified by the main project. This is equivalent to specifying the --remote flag to git submodule update.</div></td></tr>
            <tr>
    <td>umask<br/><div style="font-size: small;"> (added in 2.2)</div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The umask to set before doing any checkouts, or any other repository maintenance.</div></td></tr>
            <tr>
    <td>update<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>If <code>no</code>, do not retrieve new revisions from the origin repository</div></td></tr>
            <tr>
    <td>verify_commit<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>no</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td><div>if <code>yes</code>, when cloning or checking out a <code>version</code> verify the signature of a GPG signed commit. This requires <code>git</code> version&gt;=2.1.0 to be installed. The commit MUST be signed and the public key MUST be trusted in the GPG trustdb.</div></td></tr>
            <tr>
    <td>version<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>HEAD</td>
        <td><ul></ul></td>
        <td><div>What version of the repository to check out.  This can be the the literal string <code>HEAD</code>, a branch name, a tag name. It can also be a <em>SHA-1</em> hash, in which case <code>refspec</code> needs to be specified if the given revision is not already available.</div></td></tr>
        </table>
    </br>



Examples
--------

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


Notes
-----

.. note:: If the task seems to be hanging, first verify remote host is in ``known_hosts``. SSH will prompt user to authorize the first contact with a remote host.  To avoid this prompt, one solution is to use the option accept_hostkey. Another solution is to add the remote host public key in ``/etc/ssh/ssh_known_hosts`` before calling the git module, with the following command: ssh-keyscan -H remote_host.com >> /etc/ssh/ssh_known_hosts.


    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

