.. _sendgrid:


sendgrid - Sends an email with the SendGrid API
+++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Sends an email with a SendGrid account through their API, not through the SMTP service.




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
    <td>from_address<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the address in the "from" field for the email</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>password that corresponds to the username</div></td></tr>
            <tr>
    <td>subject<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>the desired subject for the email</div></td></tr>
            <tr>
    <td>to_addresses<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>a list with one or more recipient email addresses</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>username for logging into the SendGrid account</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # send an email to a single recipient that the deployment was successful
    - sendgrid:
        username: "{{ sendgrid_username }}"
        password: "{{ sendgrid_password }}"
        from_address: "ansible@mycompany.com"
        to_addresses:
          - "ops@mycompany.com"
        subject: "Deployment success."
        body: "The most recent Ansible deployment was successful."
      delegate_to: localhost
    
    # send an email to more than one recipient that the build failed
    - sendgrid
          username: "{{ sendgrid_username }}"
          password: "{{ sendgrid_password }}"
          from_address: "build@mycompany.com"
          to_addresses:
            - "ops@mycompany.com"
            - "devteam@mycompany.com"
          subject: "Build failure!."
          body: "Unable to pull source repository from Git server."
      delegate_to: localhost


Notes
-----

.. note:: This module is non-idempotent because it sends an email through the external API. It is idempotent only in the case that the module fails.
.. note:: Like the other notification modules, this one requires an external dependency to work. In this case, you'll need an active SendGrid account.


    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

