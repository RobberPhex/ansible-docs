.. _docker_image:


docker_image - manage docker images
+++++++++++++++++++++++++++++++++++

.. versionadded:: 1.5


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Create, check and remove docker images


Requirements
------------

  * python >= 2.6
  * docker-py
  * requests


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
    <td>docker_api_version<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>docker-py default remote API version</td>
        <td><ul></ul></td>
        <td><div>Remote API version to use. This defaults to the current default as specified by docker-py.</div></td></tr>
            <tr>
    <td>docker_url<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>${DOCKER_HOST} or unix://var/run/docker.sock</td>
        <td><ul></ul></td>
        <td><div>URL of docker host to issue commands to</div></td></tr>
            <tr>
    <td>dockerfile<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>Dockerfile</td>
        <td><ul></ul></td>
        <td><div>Dockerfile to use</div></td></tr>
            <tr>
    <td>name<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Image name to work with</div></td></tr>
            <tr>
    <td>nocache<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Do not use cache with building</div></td></tr>
            <tr>
    <td>path<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>Path to directory with Dockerfile</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>build</li></ul></td>
        <td><div>Set the state of the image</div></td></tr>
            <tr>
    <td>tag<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>latest</td>
        <td><ul></ul></td>
        <td><div>Image tag to work with</div></td></tr>
            <tr>
    <td>timeout<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td>600</td>
        <td><ul></ul></td>
        <td><div>Set image operation timeout</div></td></tr>
            <tr>
    <td>tls_ca_cert<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>${DOCKER_CERT_PATH}/ca.pem</td>
        <td><ul></ul></td>
        <td><div>Path to a PEM-encoded certificate authority to secure the Docker connection. This has no effect if use_tls is encrypt.</div></td></tr>
            <tr>
    <td>tls_client_cert<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>${DOCKER_CERT_PATH}/cert.pem</td>
        <td><ul></ul></td>
        <td><div>Path to the PEM-encoded certificate used to authenticate docker client. If specified tls_client_key must be valid</div></td></tr>
            <tr>
    <td>tls_client_key<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>${DOCKER_CERT_PATH}/key.pem</td>
        <td><ul></ul></td>
        <td><div>Path to the PEM-encoded key used to authenticate docker client. If specified tls_client_cert must be valid</div></td></tr>
            <tr>
    <td>tls_hostname<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td>Taken from docker_url</td>
        <td><ul></ul></td>
        <td><div>A hostname to check matches what's supplied in the docker server's certificate.  If unspecified, the hostname is taken from the docker_url.</div></td></tr>
            <tr>
    <td>use_tls<br/><div style="font-size: small;"> (added in 2.0)</div></td>
    <td>no</td>
    <td></td>
        <td><ul><li>no</li><li>encrypt</li><li>verify</li></ul></td>
        <td><div>Whether to use tls to connect to the docker server.  "no" means not to use tls (and ignore any other tls related parameters). "encrypt" means to use tls to encrypt the connection to the server.  "verify" means to also verify that the server's certificate is valid for the server (this both verifies the certificate against the CA and that the certificate was issued for that host. If this is unspecified, tls will only be used if one of the other tls options require it.</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    Build docker image if required. Path should contains Dockerfile to build image:
    
    - hosts: web
      sudo: yes
      tasks:
      - name: check or build image
        docker_image: path="/path/to/build/dir" name="my/app" state=present
    
    Build new version of image:
    
    - hosts: web
      sudo: yes
      tasks:
      - name: check or build image
        docker_image: path="/path/to/build/dir" name="my/app" state=build
    
    Remove image from local docker storage:
    
    - hosts: web
      sudo: yes
      tasks:
      - name: remove image
        docker_image: name="my/app" state=absent
    




    
This is a Core Module
---------------------

For more information on what this means please read :doc:`modules_core`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

