.. _katello:


katello - Manage Katello Resources
++++++++++++++++++++++++++++++++++

.. versionadded:: 2.3


.. contents::
   :local:
   :depth: 2


Synopsis
--------

* Allows the management of Katello resources inside your Foreman server


Requirements (on host that executes module)
-------------------------------------------

  * nailgun >= 0.28.0
  * python >= 2.6
  * datetime


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
                <tr><td>entity<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>The Foreman resource that the action will be performed on (e.g. organization, host)</div>        </td></tr>
                <tr><td>params<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Parameters associated to the entity resource to set or edit in dictionary format (e.g. name, description)</div>        </td></tr>
                <tr><td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Password for user accessing Foreman server</div>        </td></tr>
                <tr><td>server_url<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>URL of Foreman server</div>        </td></tr>
                <tr><td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td></td>
        <td><div>Username on Foreman server</div>        </td></tr>
        </table>
    </br>



Examples
--------

 ::

    ---
    # Simple Example:
    
    - name: "Create Product"
      local_action:
          module: katello
          username: "admin"
          password: "admin"
          server_url: "https://fakeserver.com"
          entity: "product"
          params:
            name: "Centos 7"
    
    # Abstraction Example:
    # katello.yml
    ---
    - name: "{{ name }}"
      local_action:
          module: katello
          username: "admin"
          password: "admin"
          server_url: "https://fakeserver.com"
          entity: "{{ entity }}"
          params: "{{ params }}"
    
    # tasks.yml
    ---
    - include: katello.yml
      vars:
        name: "Create Dev Environment"
        entity: "lifecycle_environment"
        params:
          name: "Dev"
          prior: "Library"
          organization: "Default Organization"
    
    - include: katello.yml
      vars:
        name: "Create Centos Product"
        entity: "product"
        params:
          name: "Centos 7"
          organization: "Default Organization"
    
    - include: katello.yml
      vars:
        name: "Create 7.2 Repository"
        entity: "repository"
        params:
          name: "Centos 7.2"
          product: "Centos 7"
          organization: "Default Organization"
          content_type: "yum"
          url: "http://mirror.centos.org/centos/7/os/x86_64/"
    
    - include: katello.yml
      vars:
          name: "Create Centos 7 View"
          entity: "content_view"
          params:
            name: "Centos 7 View"
            organization: "Default Organization"
            repositories:
              - name: "Centos 7.2"
                product: "Centos 7"
    
    - include: katello.yml
      vars:
          name: "Enable RHEL Product"
          entity: "repository_set"
          params:
            name: "Red Hat Enterprise Linux 7 Server (RPMs)"
            product: "Red Hat Enterprise Linux Server"
            organization: "Default Organization"
            basearch: "x86_64"
            releasever: "7"





Status
~~~~~~

This module is flagged as **preview** which means that it is not guaranteed to have a backwards compatible interface.


Support
~~~~~~~

This module is community maintained without core committer oversight.

For more information on what this means please read :doc:`modules_support`


For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`dev_guide/developing_test_pr` and :doc:`dev_guide/developing_modules`.
