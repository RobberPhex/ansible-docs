Commands Modules
````````````````

.. toctree:: :maxdepth: 1

  command - Executes a command on a remote node <command_module>
  expect (E) - Executes a command and responds to prompts <expect_module>
  raw - Executes a low-down and dirty SSH command <raw_module>
  script - Runs a local script on a remote node after transferring it <script_module>
  shell - Execute commands in nodes. <shell_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not necessarily) less actively maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
