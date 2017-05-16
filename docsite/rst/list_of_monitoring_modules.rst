Monitoring Modules
``````````````````

.. toctree:: :maxdepth: 1

  airbrake_deployment (E) - Notify airbrake about app deployments <airbrake_deployment_module>
  bigpanda (E) - Notify BigPanda about deployments <bigpanda_module>
  boundary_meter (E) - Manage boundary meters <boundary_meter_module>
  circonus_annotation (E) - create an annotation in circonus <circonus_annotation_module>
  datadog_event (E) - Posts events to DataDog  service <datadog_event_module>
  datadog_monitor (E) - Manages Datadog monitors <datadog_monitor_module>
  honeybadger_deployment (E) - Notify Honeybadger.io about app deployments <honeybadger_deployment_module>
  librato_annotation (E) - create an annotation in librato <librato_annotation_module>
  logentries (E) - Module for tracking logs via logentries.com <logentries_module>
  logicmonitor (E) - Manage your LogicMonitor account through Ansible Playbooks <logicmonitor_module>
  logicmonitor_facts (E) - Collect facts about LogicMonitor objects <logicmonitor_facts_module>
  monit (E) - Manage the state of a program monitored via Monit <monit_module>
  nagios (E) - Perform common tasks in Nagios related to downtime and notifications. <nagios_module>
  newrelic_deployment (E) - Notify newrelic about app deployments <newrelic_deployment_module>
  pagerduty (E) - Create PagerDuty maintenance windows <pagerduty_module>
  pagerduty_alert (E) - Trigger, acknowledge or resolve PagerDuty incidents <pagerduty_alert_module>
  pingdom (E) - Pause/unpause Pingdom alerts <pingdom_module>
  rollbar_deployment (E) - Notify Rollbar about app deployments <rollbar_deployment_module>
  sensu_check (E) - Manage Sensu checks <sensu_check_module>
  sensu_subscription (E) - Manage Sensu subscriptions <sensu_subscription_module>
  stackdriver (E) - Send code deploy and annotation events to stackdriver <stackdriver_module>
  statusio_maintenance (E) - Create maintenance windows for your status.io dashboard <statusio_maintenance_module>
  uptimerobot (E) - Pause and start Uptime Robot monitoring <uptimerobot_module>
  zabbix_group (E) - Zabbix host groups creates/deletes <zabbix_group_module>
  zabbix_host (E) - Zabbix host creates/updates/deletes <zabbix_host_module>
  zabbix_hostmacro (E) - Zabbix host macro creates/updates/deletes <zabbix_hostmacro_module>
  zabbix_maintenance (E) - Create Zabbix maintenance windows <zabbix_maintenance_module>
  zabbix_screen (E) - Zabbix screen creates/updates/deletes <zabbix_screen_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not necessarily) less actively maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
