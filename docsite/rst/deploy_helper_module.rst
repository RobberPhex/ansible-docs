.. _deploy_helper:


deploy_helper - Manages some of the steps common in deploying projects.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

The Deploy Helper manages some of the steps common in deploying software. It creates a folder structure, manages a symlink for the current release and cleans up old releases.
Running it with the ``state=query`` or ``state=present`` will return the ``deploy_helper`` fact. ``project_path``, whatever you set in the path parameter, ``current_path``, the path to the symlink that points to the active release, ``releases_path``, the path to the folder to keep releases in, ``shared_path``, the path to the folder to keep shared resources in, ``unfinished_filename``, the file to check for to recognize unfinished builds, ``previous_release``, the release the 'current' symlink is pointing to, ``previous_release_path``, the full path to the 'current' symlink target, ``new_release``, either the 'release' parameter or a generated timestamp, ``new_release_path``, the path to the new release folder (not created by the module).




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
    <td>clean<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td><div>Whether to run the clean procedure in case of <code>state=finalize</code>.</div></td></tr>
            <tr>
    <td>current_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>current</td>
        <td><ul></ul></td>
        <td><div>the name of the symlink that is created when the deploy is finalized. Used in <code>finalize</code> and <code>clean</code>. Returned in the <code>deploy_helper.current_path</code> fact.</div></td></tr>
            <tr>
    <td>keep_releases<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>5</td>
        <td><ul></ul></td>
        <td><div>the number of old releases to keep when cleaning. Used in <code>finalize</code> and <code>clean</code>. Any unfinished builds will be deleted first, so only correct releases will count. The current version will not count.</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the root path of the project. Alias <em>dest</em>. Returned in the <code>deploy_helper.project_path</code> fact.</div></br>
        <div style="font-size: small;">aliases: dest<div></td></tr>
            <tr>
    <td>release<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>the release version that is being deployed. Defaults to a timestamp format %Y%m%d%H%M%S (i.e. '20141119223359'). This parameter is optional during <code>state=present</code>, but needs to be set explicitly for <code>state=finalize</code>. You can use the generated fact <code>release={{ deploy_helper.new_release }}</code>.</div></td></tr>
            <tr>
    <td>releases_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>releases</td>
        <td><ul></ul></td>
        <td><div>the name of the folder that will hold the releases. This can be relative to <code>path</code> or absolute. Returned in the <code>deploy_helper.releases_path</code> fact.</div></td></tr>
            <tr>
    <td>shared_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>shared</td>
        <td><ul></ul></td>
        <td><div>the name of the folder that will hold the shared resources. This can be relative to <code>path</code> or absolute. If this is set to an empty string, no shared folder will be created. Returned in the <code>deploy_helper.shared_path</code> fact.</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>finalize</li><li>absent</li><li>clean</li><li>query</li></ul></td>
        <td><div>the state of the project. <code>query</code> will only gather facts, <code>present</code> will create the project <em>root</em> folder, and in it the <em>releases</em> and <em>shared</em> folders, <code>finalize</code> will remove the unfinished_filename file, create a symlink to the newly deployed release and optionally clean old releases, <code>clean</code> will remove failed &amp; old releases, <code>absent</code> will remove the project folder (synonymous to the <span class='module'>file</span> module with <code>state=absent</code>)</div></td></tr>
            <tr>
    <td>unfinished_filename<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>DEPLOY_UNFINISHED</td>
        <td><ul></ul></td>
        <td><div>the name of the file that indicates a deploy has not finished. All folders in the releases_path that contain this file will be deleted on <code>state=finalize</code> with clean=True, or <code>state=clean</code>. This file is automatically deleted from the <em>new_release_path</em> during <code>state=finalize</code>.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    
    # General explanation, starting with an example folder structure for a project:
    
    root:
        releases:
            - 20140415234508
            - 20140415235146
            - 20140416082818
    
        shared:
            - sessions
            - uploads
    
        current: -> releases/20140416082818
    
    
    The 'releases' folder holds all the available releases. A release is a complete build of the application being
    deployed. This can be a clone of a repository for example, or a sync of a local folder on your filesystem.
    Having timestamped folders is one way of having distinct releases, but you could choose your own strategy like
    git tags or commit hashes.
    
    During a deploy, a new folder should be created in the releases folder and any build steps required should be
    performed. Once the new build is ready, the deploy procedure is 'finalized' by replacing the 'current' symlink
    with a link to this build.
    
    The 'shared' folder holds any resource that is shared between releases. Examples of this are web-server
    session files, or files uploaded by users of your application. It's quite common to have symlinks from a release
    folder pointing to a shared/subfolder, and creating these links would be automated as part of the build steps.
    
    The 'current' symlink points to one of the releases. Probably the latest one, unless a deploy is in progress.
    The web-server's root for the project will go through this symlink, so the 'downtime' when switching to a new
    release is reduced to the time it takes to switch the link.
    
    To distinguish between successful builds and unfinished ones, a file can be placed in the folder of the release
    that is currently in progress. The existence of this file will mark it as unfinished, and allow an automated
    procedure to remove it during cleanup.
    
    
    # Typical usage:
    - name: Initialize the deploy root and gather facts
      deploy_helper: path=/path/to/root
    - name: Clone the project to the new release folder
      git: repo=git://foosball.example.org/path/to/repo.git dest={{ deploy_helper.new_release_path }} version=v1.1.1
    - name: Add an unfinished file, to allow cleanup on successful finalize
      file: path={{ deploy_helper.new_release_path }}/{{ deploy_helper.unfinished_filename }} state=touch
    - name: Perform some build steps, like running your dependency manager for example
      composer: command=install working_dir={{ deploy_helper.new_release_path }}
    - name: Create some folders in the shared folder
      file: path='{{ deploy_helper.shared_path }}/{{ item }}' state=directory
      with_items: ['sessions', 'uploads']
    - name: Add symlinks from the new release to the shared folder
      file: path='{{ deploy_helper.new_release_path }}/{{ item.path }}'
            src='{{ deploy_helper.shared_path }}/{{ item.src }}'
            state=link
      with_items:
          - { path: "app/sessions", src: "sessions" }
          - { path: "web/uploads",  src: "uploads" }
    - name: Finalize the deploy, removing the unfinished file and switching the symlink
      deploy_helper: path=/path/to/root release={{ deploy_helper.new_release }} state=finalize
    
    # Retrieving facts before running a deploy
    - name: Run 'state=query' to gather facts without changing anything
      deploy_helper: path=/path/to/root state=query
    # Remember to set the 'release' parameter when you actually call 'state=present' later
    - name: Initialize the deploy root
      deploy_helper: path=/path/to/root release={{ deploy_helper.new_release }} state=present
    
    # all paths can be absolute or relative (to the 'path' parameter)
    - deploy_helper: path=/path/to/root
                     releases_path=/var/www/project/releases
                     shared_path=/var/www/shared
                     current_path=/var/www/active
    
    # Using your own naming strategy for releases (a version tag in this case):
    - deploy_helper: path=/path/to/root release=v1.1.1 state=present
    - deploy_helper: path=/path/to/root release={{ deploy_helper.new_release }} state=finalize
    
    # Using a different unfinished_filename:
    - deploy_helper: path=/path/to/root
                     unfinished_filename=README.md
                     release={{ deploy_helper.new_release }}
                     state=finalize
    
    # Postponing the cleanup of older builds:
    - deploy_helper: path=/path/to/root release={{ deploy_helper.new_release }} state=finalize clean=False
    - deploy_helper: path=/path/to/root state=clean
    # Or running the cleanup ahead of the new deploy
    - deploy_helper: path=/path/to/root state=clean
    - deploy_helper: path=/path/to/root state=present
    
    # Keeping more old releases:
    - deploy_helper: path=/path/to/root release={{ deploy_helper.new_release }} state=finalize keep_releases=10
    # Or, if you use 'clean=false' on finalize:
    - deploy_helper: path=/path/to/root state=clean keep_releases=10
    
    # Removing the entire project root folder
    - deploy_helper: path=/path/to/root state=absent
    
    # Debugging the facts returned by the module
    - deploy_helper: path=/path/to/root
    - debug: var=deploy_helper
    


Notes
-----

.. note:: Facts are only returned for ``state=query`` and ``state=present``. If you use both, you should pass any overridden parameters to both calls, otherwise the second call will overwrite the facts of the first one.
.. note:: When using ``state=clean``, the releases are ordered by *creation date*. You should be able to switch to a new naming strategy without problems.
.. note:: Because of the default behaviour of generating the *new_release* fact, this module will not be idempotent unless you pass your own release name with ``release``. Due to the nature of deploying software, this should not be much of a problem.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

