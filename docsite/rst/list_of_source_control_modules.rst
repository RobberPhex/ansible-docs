Source Control Modules
``````````````````````

.. toctree:: :maxdepth: 1

  bzr (E) - Deploy software (or files) from bzr branches <bzr_module>
  git - Deploy software (or files) from git checkouts <git_module>
  git_config (E) - Read and write git configuration <git_config_module>
  github_hooks (E) - Manages github service hooks. <github_hooks_module>
  github_key (E) - Manage GitHub access keys. <github_key_module>
  github_release (E) - Interact with GitHub Releases <github_release_module>
  gitlab_group (E) - Creates/updates/deletes Gitlab Groups <gitlab_group_module>
  gitlab_project (E) - Creates/updates/deletes Gitlab Projects <gitlab_project_module>
  gitlab_user (E) - Creates/updates/deletes Gitlab Users <gitlab_user_module>
  hg - Manages Mercurial (hg) repositories. <hg_module>
  subversion - Deploys a subversion repository. <subversion_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not necessarily) less actively maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
