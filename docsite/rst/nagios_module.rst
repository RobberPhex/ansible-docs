.. _nagios:


nagios - Perform common tasks in Nagios related to downtime and notifications.
++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------


The ``nagios`` module has two basic functions: scheduling downtime and toggling alerts for services or hosts.
All actions require the *host* parameter to be given explicitly. In playbooks you can use the ``{{inventory_hostname}}`` variable to refer to the host the playbook is currently running on.
You can specify multiple services at once by separating them with commas, .e.g., ``services=httpd,nfs,puppet``.
When specifying what service to handle there is a special service value, *host*, which will handle alerts/downtime for the *host itself*, e.g., ``service=host``. This keyword may not be given with other services at the same time. *Setting alerts/downtime for a host does not affect alerts/downtime for any of the services running on it.* To schedule downtime for all services on particular host use keyword "all", e.g., ``service=all``.
When using the ``nagios`` module you will need to specify your Nagios server using the ``delegate_to`` parameter.

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
    <td>action</td>
    <td>yes</td>
    <td></td>
        <td><ul><li>downtime</li><li>enable_alerts</li><li>disable_alerts</li><li>silence</li><li>unsilence</li><li>silence_nagios</li><li>unsilence_nagios</li><li>command</li></ul></td>
        <td>Action to take.</td>
    </tr>
            <tr>
    <td>author</td>
    <td>no</td>
    <td>Ansible</td>
        <td><ul></ul></td>
        <td>Author to leave downtime comments as. Only usable with the <code>downtime</code> action.</td>
    </tr>
            <tr>
    <td>cmdfile</td>
    <td>no</td>
    <td>auto-detected</td>
        <td><ul></ul></td>
        <td>Path to the nagios <em>command file</em> (FIFO pipe). Only required if auto-detection fails.</td>
    </tr>
            <tr>
    <td>command</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The raw command to send to nagios, which should not include the submitted time header or the line-feed <b>Required</b> option when using the <code>command</code> action.</td>
    </tr>
            <tr>
    <td>host</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Host to operate on in Nagios.</td>
    </tr>
            <tr>
    <td>minutes</td>
    <td>no</td>
    <td>30</td>
        <td><ul></ul></td>
        <td>Minutes to schedule downtime for.Only usable with the <code>downtime</code> action.</td>
    </tr>
            <tr>
    <td>services</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>What to manage downtime/alerts for. Separate multiple services with commas. <code>service</code> is an alias for <code>services</code>. <b>Required</b> option when using the <code>downtime</code>, <code>enable_alerts</code>, and <code>disable_alerts</code> actions.</td>
    </tr>
        </table>


.. note:: Requires Nagios


Examples
--------

.. raw:: html

    <br/>


::

    # set 30 minutes of apache downtime
    - nagios: action=downtime minutes=30 service=httpd host={{ inventory_hostname }}
    
    # schedule an hour of HOST downtime
    - nagios: action=downtime minutes=60 service=host host={{ inventory_hostname }}
    
    # schedule downtime for ALL services on HOST
    - nagios: action=downtime minutes=45 service=all host={{ inventory_hostname }}
    
    # schedule downtime for a few services
    - nagios: action=downtime services=frob,foobar,qeuz host={{ inventory_hostname }}
    
    # enable SMART disk alerts
    - nagios: action=enable_alerts service=smart host={{ inventory_hostname }}
    
    # "two services at once: disable httpd and nfs alerts"
    - nagios: action=disable_alerts service=httpd,nfs host={{ inventory_hostname }}
    
    # disable HOST alerts
    - nagios: action=disable_alerts service=host host={{ inventory_hostname }}
    
    # silence ALL alerts
    - nagios: action=silence host={{ inventory_hostname }}
    
    # unsilence all alerts
    - nagios: action=unsilence host={{ inventory_hostname }}
    
    # SHUT UP NAGIOS
    - nagios: action=silence_nagios
    
    # ANNOY ME NAGIOS
    - nagios: action=unsilence_nagios
    
    # command something
    - nagios: action=command command='DISABLE_FAILURE_PREDICTION'



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

