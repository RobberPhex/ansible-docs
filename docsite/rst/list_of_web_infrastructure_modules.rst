Web Infrastructure Modules
``````````````````````````

.. toctree:: :maxdepth: 1

  apache2_module - enables/disables a module of the Apache2 webserver <apache2_module_module>
  django_manage - Manages a Django application. <django_manage_module>
  ejabberd_user (E) - Manages users for ejabberd servers <ejabberd_user_module>
  htpasswd - manage user files for basic authentication <htpasswd_module>
  jboss (E) - deploy applications to JBoss <jboss_module>
  jira (E) - create and modify issues in a JIRA instance <jira_module>
  supervisorctl - Manage the state of a program or group of programs running via supervisord <supervisorctl_module>
  taiga_issue (E) - Creates/deletes an issue in a Taiga Project Management Platform <taiga_issue_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not necessarily) less actively maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
