Utilities Modules
`````````````````

.. toctree:: :maxdepth: 1


Helper
------

.. toctree:: :maxdepth: 1

  _fireball (E) - Enable fireball mode on remote node <_fireball_module>
  accelerate - Enable accelerated mode on remote node <accelerate_module>

Logic
-----

.. toctree:: :maxdepth: 1

  assert - Fail with custom message <assert_module>
  async_status - Obtain status of asynchronous task <async_status_module>
  debug - Print statements during execution <debug_module>
  fail - Fail with custom message <fail_module>
  include_vars - Load variables from files, dynamically within a task. <include_vars_module>
  pause - Pause playbook execution <pause_module>
  set_fact - Set host facts from a task <set_fact_module>
  wait_for - Waits for a condition before continuing. <wait_for_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not necessarily) less actively maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
