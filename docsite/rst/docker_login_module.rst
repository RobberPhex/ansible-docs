.. _docker_login:


docker_login - Manage Docker registry logins
++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Ansible version of the "docker login" CLI command.
This module allows you to login to a Docker registry without directly pulling an image or performing any other actions.
It will write your login credentials to your local .dockercfg file that is compatible to the Docker CLI client as well as docker-py and all other Docker related modules that are based on docker-py.


Requirements
------------

  * python >= 2.6
  * docker-py >= 1.1.0


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
    <td>docker_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>unix://var/run/docker.sock</td>
        <td><ul></ul></td>
        <td></td></tr>
            <tr>
    <td>dockercfg_path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>~/.docker/config.json</td>
        <td><ul></ul></td>
        <td><div>Use a custom path for the .dockercfg file</div></td></tr>
            <tr>
    <td>email<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>None</td>
        <td><ul></ul></td>
        <td><div>The email address for the registry account. Note that private registries usually don't need this, but if you want to log into your Docker Hub account (default behaviour) you need to specify this in order to be able to log in.</div></td></tr>
            <tr>
    <td>password<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The plaintext password for the registry account</div></td></tr>
            <tr>
    <td>reauth<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Whether refresh existing authentication on the Docker server (boolean)</div></td></tr>
            <tr>
    <td>registry<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>https://index.docker.io/v1/</td>
        <td><ul></ul></td>
        <td><div>URL of the registry, defaults to: https://index.docker.io/v1/</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>600</td>
        <td><ul></ul></td>
        <td><div>The HTTP request timeout in seconds</div></td></tr>
            <tr>
    <td>username<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The username for the registry account</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    Login to a Docker registry without performing any other action. Make sure that the user you are using is either in the docker group which owns the Docker socket or use sudo to perform login actions:
    
    - name: login to DockerHub remote registry using your account
      docker_login:
        username: docker
        password: rekcod
        email: docker@docker.io
    
    - name: login to private Docker remote registry and force reauthentification
      docker_login:
        registry: your.private.registry.io
        username: yourself
        password: secrets3
        reauth: yes
    
    - name: login to DockerHub remote registry using a custom dockercfg file location
      docker_login:
        username: docker
        password: rekcod
        email: docker@docker.io
        dockercfg_path: /tmp/.mydockercfg
    




    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

