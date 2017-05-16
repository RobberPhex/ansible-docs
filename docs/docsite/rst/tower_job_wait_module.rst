.. _tower_job_wait:


tower_job_wait - Wait for Ansible Tower job to finish.
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Wait for Ansible Tower job to finish and report success or failure. See https://www.ansible.com/tower for an overview.


Requirements (on host that executes module)
-------------------------------------------

  * python >= 2.6
  * ansible-tower-cli >= 3.0.2


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
                <tr><td>job_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>ID of the job to monitor.</div>        </td></tr>
                <tr><td>max_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>30</td>
        <td></td>
        <td><div>Maximum interval in seconds, to request an update from Tower.</div>        </td></tr>
                <tr><td>min_interval<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>1</td>
        <td></td>
        <td><div>Minimum interval in seconds, to request an update from Tower.</div>        </td></tr>
                <tr><td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Maximum time in seconds to wait for a job to finish.</div>        </td></tr>
                <tr><td>tower_config_file<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Path to the Tower config file. See notes.</div>        </td></tr>
                <tr><td>tower_host<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>URL to your Tower instance.</div>        </td></tr>
                <tr><td>tower_password<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Password for your Tower instance.</div>        </td></tr>
                <tr><td>tower_username<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Username for your Tower instance.</div>        </td></tr>
                <tr><td>tower_verify_ssl<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>True</td>
        <td></td>
        <td><div>Dis/allow insecure connections to Tower. If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates.</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: Launch a job
      tower_job_launch:
        job_template: "My Job Template"
        register: job
    - name: Wait for job max 120s
      tower_job_wait:
        job_id: job.id
        timeout: 120

Return Values
-------------

Common return values are documented here :doc:`common_return_values`, the following are the fields unique to this module:

.. raw:: html

    <table border=1 cellpadding=4>
    <tr>
    <th class="head">name</th>
    <th class="head">description</th>
    <th class="head">returned</th>
    <th class="head">type</th>
    <th class="head">sample</th>
    </tr>

        <tr>
        <td> started </td>
        <td> timestamp of when the job started running </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2017-03-01 17:03:53.200234 </td>
    </tr>
            <tr>
        <td> status </td>
        <td> current status of job </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> successful </td>
    </tr>
            <tr>
        <td> finished </td>
        <td> timestamp of when the job finished running </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> 2017-03-01 17:04:04.078782 </td>
    </tr>
            <tr>
        <td> id </td>
        <td> job id that is being waited on </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 99 </td>
    </tr>
            <tr>
        <td> elapsed </td>
        <td> total time in seconds the job took to run </td>
        <td align=center> success </td>
        <td align=center> float </td>
        <td align=center> 10.879 </td>
    </tr>
        
    </table>
    </br></br>

Notes
-----

.. note::
    - If no *config_file* is provided we will attempt to use the tower-cli library defaults to find your Tower host information.
    - *config_file* should contain Tower configuration in the following format host=hostname username=username password=password



Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
