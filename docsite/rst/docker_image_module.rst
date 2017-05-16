.. _docker_image:


docker_image - manage docker images
+++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1


DEPRECATED
----------

functions are being rolled into the 'docker' module

Synopsis
--------

.. versionadded:: 1.5

Create, check and remove docker images

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
    <td>docker_url</td>
    <td>no</td>
    <td>unix://var/run/docker.sock</td>
        <td><ul></ul></td>
        <td>URL of docker host to issue commands to</td>
    </tr>
            <tr>
    <td>name</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Image name to work with</td>
    </tr>
            <tr>
    <td>nocache</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Do not use cache with building</td>
    </tr>
            <tr>
    <td>path</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Path to directory with Dockerfile</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>absent</li><li>build</li></ul></td>
        <td>Set the state of the image</td>
    </tr>
            <tr>
    <td>tag</td>
    <td>no</td>
    <td>latest</td>
        <td><ul></ul></td>
        <td>Image tag to work with</td>
    </tr>
            <tr>
    <td>timeout</td>
    <td>no</td>
    <td>600</td>
        <td><ul></ul></td>
        <td>Set image operation timeout</td>
    </tr>
        </table>


.. note:: Requires docker-py


Examples
--------

.. raw:: html

    <br/>


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
    




For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

