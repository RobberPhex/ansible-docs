.. _tower_job_cancel:


tower_job_cancel - Cancel an Ansible Tower Job.
+++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Cancel Ansible Tower jobs. See https://www.ansible.com/tower for an overview.


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
                <tr><td>fail_if_not_running<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td></td>
        <td><div>Fail loudly if the job_id does not reference a running job.</div>        </td></tr>
                <tr><td>job_id<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>ID of the job to cancel</div>        </td></tr>
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

    - name: Cancel job
      tower_job_cancel:
        job_id: job.id

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
        <td> status </td>
        <td> status of the cancel request </td>
        <td align=center> success </td>
        <td align=center> string </td>
        <td align=center> canceled </td>
    </tr>
            <tr>
        <td> id </td>
        <td> job id requesting to cancel </td>
        <td align=center> success </td>
        <td align=center> int </td>
        <td align=center> 94 </td>
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
