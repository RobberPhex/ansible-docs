Monitoring Modules
``````````````````

.. toctree:: :maxdepth: 1

  airbrake_deployment (E) - Notify airbrake about app deployments <airbrake_deployment_module>
  bigpanda (E) - Notify BigPanda about deployments <bigpanda_module>
  boundary_meter (E) - Manage boundary meters <boundary_meter_module>
  datadog_event (E) - Posts events to DataDog  service <datadog_event_module>
  librato_annotation (E) - create an annotation in librato <librato_annotation_module>
  logentries (E) - Module for tracking logs via logentries.com <logentries_module>
  monit (E) - Manage the state of a program monitored via Monit <monit_module>
  nagios (E) - Perform common tasks in Nagios related to downtime and notifications. <nagios_module>
  newrelic_deployment (E) - Notify newrelic about app deployments <newrelic_deployment_module>
  pagerduty (E) - Create PagerDuty maintenance windows <pagerduty_module>
  pingdom (E) - Pause/unpause Pingdom alerts <pingdom_module>
  rollbar_deployment (E) - Notify Rollbar about app deployments <rollbar_deployment_module>
  stackdriver (E) - Send code deploy and annotation events to stackdriver <stackdriver_module>
  zabbix_maintenance (E) - Create Zabbix maintenance windows <zabbix_maintenance_module>



.. note::
    -  (D): This marks a module as deprecated, which means a module is kept for backwards compatibility but usage is discouraged.  The module documentation details page may explain more about this rationale.
    -  (E): This marks a module as 'extras', which means it ships with ansible but may be a newer module and possibly (but not neccessarily) less activity maintained than 'core' modules.
    - Tickets filed on modules are filed to different repos than those on the main open source project. Core module tickets should be filed at `ansible/ansible-modules-core on GitHub <http://github.com/ansible/ansible-modules-core>`_, extras tickets to `ansible/ansible-modules-extras on GitHub <http://github.com/ansible/ansible-modules-extras>`_
