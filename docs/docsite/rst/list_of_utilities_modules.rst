Utilities Modules
`````````````````

.. toctree:: :maxdepth: 1


Helper
------

.. toctree:: :maxdepth: 1

  accelerate (D) - Enable accelerated mode on remote node <accelerate_module>
  meta - Execute Ansible 'actions' <meta_module>

Logic
-----

.. toctree:: :maxdepth: 1

  assert - Asserts given expressions are true <assert_module>
  async_status - Obtain status of asynchronous task <async_status_module>
  debug - Print statements during execution <debug_module>
  fail - Fail with custom message <fail_module>
  include - include a play or task list. <include_module>
  include_role - Load and execute a role <include_role_module>
  include_vars - Load variables from files, dynamically within a task. <include_vars_module>
  pause - Pause playbook execution <pause_module>
  set_fact - Set host facts from a task <set_fact_module>
  set_stats - Set stats for the current ansible run <set_stats_module>
  wait_for - Waits for a condition before continuing. <wait_for_module>
  wait_for_connection - Waits until remote system is reachable/usable <wait_for_connection_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.
       The module documentation details page may explain more about this rationale.
