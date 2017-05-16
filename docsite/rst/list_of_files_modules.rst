Files Modules
`````````````

.. toctree:: :maxdepth: 1

  acl - Sets and retrieves file ACL information. <acl_module>
  assemble - Assembles a configuration file from fragments <assemble_module>
  blockinfile (E) - Insert/update/remove a text block surrounded by marker lines. <blockinfile_module>
  copy - Copies files to remote locations. <copy_module>
  fetch - Fetches a file from remote nodes <fetch_module>
  file - Sets attributes of files <file_module>
  find - return a list of files based on specific criteria <find_module>
  ini_file - Tweak settings in INI files <ini_file_module>
  lineinfile - Ensure a particular line is in a file, or replace an existing line using a back-referenced regular expression. <lineinfile_module>
  patch (E) - Apply patch files using the GNU patch tool. <patch_module>
  replace - Replace all instances of a particular string in a file using a back-referenced regular expression. <replace_module>
  stat - retrieve file or file system status <stat_module>
  synchronize - Uses rsync to make synchronizing file paths in your playbooks quick and easy. <synchronize_module>
  template - Templates a file out to a remote server. <template_module>
  unarchive - Unpacks an archive after (optionally) copying it from the local machine. <unarchive_module>
  xattr - set/retrieve extended attributes <xattr_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not necessarily) less actively maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
