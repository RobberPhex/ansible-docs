.. _docker:


docker - manage docker containers
+++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.4

Manage the life cycle of docker containers.

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
    <td>command</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Set command to run in a container on startup</td>
    </tr>
            <tr>
    <td>count</td>
    <td>no</td>
    <td>1</td>
        <td><ul></ul></td>
        <td>Set number of containers to run</td>
    </tr>
            <tr>
    <td>detach</td>
    <td>no</td>
    <td>True</td>
        <td><ul></ul></td>
        <td>Enable detached mode on start up, leaves container running in background</td>
    </tr>
            <tr>
    <td>dns</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Set custom DNS servers for the container</td>
    </tr>
            <tr>
    <td>docker_api_version</td>
    <td>no</td>
    <td>docker-py default remote API version</td>
        <td><ul></ul></td>
        <td>Remote API version to use. This defaults to the current default as specified by docker-py. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>docker_url</td>
    <td>no</td>
    <td>unix://var/run/docker.sock</td>
        <td><ul></ul></td>
        <td>URL of docker host to issue commands to</td>
    </tr>
            <tr>
    <td>env</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Set environment variables (e.g. env="PASSWORD=sEcRe7,WORKERS=4")</td>
    </tr>
            <tr>
    <td>expose</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Set container ports to expose for port mappings or links. (If the port is already exposed using EXPOSE in a Dockerfile, you don't need to expose it again.) (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>hostname</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Set container hostname</td>
    </tr>
            <tr>
    <td>image</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Set container image to use</td>
    </tr>
            <tr>
    <td>links</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Link container(s) to other container(s) (e.g. links=redis,postgresql:db) (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>lxc_conf</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>LXC config parameters,  e.g. lxc.aa_profile:unconfined</td>
    </tr>
            <tr>
    <td>memory_limit</td>
    <td>no</td>
    <td>256MB</td>
        <td><ul></ul></td>
        <td>Set RAM allocated to container</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Set the name of the container (cannot use with count) (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>net</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Set Network mode for the container (bridge, none, container:&lt;name|id&gt;, host). Requires docker &gt;= 0.11. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>password</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Set remote API password</td>
    </tr>
            <tr>
    <td>ports</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Set private to public port mapping specification using docker CLI-style syntax [([&lt;host_interface&gt;:[host_port]])|(&lt;host_port&gt;):]&lt;container_port&gt;[/udp] (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>privileged</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Set whether the container should run in privileged mode</td>
    </tr>
            <tr>
    <td>publish_all_ports</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Publish all exposed ports to the host interfaces (added in Ansible 1.5)</td>
    </tr>
            <tr>
    <td>registry</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The remote registry URL to use for pulling images. (added in Ansible 1.8)</td>
    </tr>
            <tr>
    <td>state</td>
    <td>no</td>
    <td>present</td>
        <td><ul><li>present</li><li>running</li><li>stopped</li><li>absent</li><li>killed</li><li>restarted</li></ul></td>
        <td>Set the state of the container</td>
    </tr>
            <tr>
    <td>stdin_open</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Keep stdin open (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>tty</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Allocate a pseudo-tty (added in Ansible 1.6)</td>
    </tr>
            <tr>
    <td>username</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Set remote API username</td>
    </tr>
            <tr>
    <td>volumes</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Set volume(s) to mount on the container</td>
    </tr>
            <tr>
    <td>volumes_from</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Set shared volume(s) from another container</td>
    </tr>
        </table>


.. note:: Requires docker-py >= 0.3.0


.. note:: Requires docker >= 0.10.0


Examples
--------

.. raw:: html

    <br/>


::

    Start one docker container running tomcat in each host of the web group and bind tomcat's listening port to 8080
    on the host:
    
    - hosts: web
      sudo: yes
      tasks:
      - name: run tomcat servers
        docker: image=centos command="service tomcat6 start" ports=8080
    
    The tomcat server's port is NAT'ed to a dynamic port on the host, but you can determine which port the server was
    mapped to using docker_containers:
    
    - hosts: web
      sudo: yes
      tasks:
      - name: run tomcat servers
        docker: image=centos command="service tomcat6 start" ports=8080 count=5
      - name: Display IP address and port mappings for containers
        debug: msg={{inventory_hostname}}:{{item['HostConfig']['PortBindings']['8080/tcp'][0]['HostPort']}}
        with_items: docker_containers
    
    Just as in the previous example, but iterates over the list of docker containers with a sequence:
    
    - hosts: web
      sudo: yes
      vars:
        start_containers_count: 5
      tasks:
      - name: run tomcat servers
        docker: image=centos command="service tomcat6 start" ports=8080 count={{start_containers_count}}
      - name: Display IP address and port mappings for containers
        debug: msg="{{inventory_hostname}}:{{docker_containers[{{item}}]['HostConfig']['PortBindings']['8080/tcp'][0]['HostPort']}}"
        with_sequence: start=0 end={{start_containers_count - 1}}
    
    Stop, remove all of the running tomcat containers and list the exit code from the stopped containers:
    
    - hosts: web
      sudo: yes
      tasks:
      - name: stop tomcat servers
        docker: image=centos command="service tomcat6 start" state=absent
      - name: Display return codes from stopped containers
        debug: msg="Returned {{inventory_hostname}}:{{item}}"
        with_items: docker_containers
    
    Create a named container:
    
    - hosts: web
      sudo: yes
      tasks:
      - name: run tomcat server
        docker: image=centos name=tomcat command="service tomcat6 start" ports=8080
    
    Create multiple named containers:
    
    - hosts: web
      sudo: yes
      tasks:
      - name: run tomcat servers
        docker: image=centos name={{item}} command="service tomcat6 start" ports=8080
        with_items:
          - crookshank
          - snowbell
          - heathcliff
          - felix
          - sylvester
    
    Create containers named in a sequence:
    
    - hosts: web
      sudo: yes
      tasks:
      - name: run tomcat servers
        docker: image=centos name={{item}} command="service tomcat6 start" ports=8080
        with_sequence: start=1 end=5 format=tomcat_%d.example.com
    
    Create two linked containers:
    
    - hosts: web
      sudo: yes
      tasks:
      - name: ensure redis container is running
        docker: image=crosbymichael/redis name=redis
    
      - name: ensure redis_ambassador container is running
        docker: image=svendowideit/ambassador ports=6379:6379 links=redis:redis name=redis_ambassador_ansible
    
    Create containers with options specified as key-value pairs and lists:
    
    - hosts: web
      sudo: yes
      tasks:
      - docker:
            image: namespace/image_name
            links:
              - postgresql:db
              - redis:redis
    
    
    Create containers with options specified as strings and lists as comma-separated strings:
    
    - hosts: web
      sudo: yes
      tasks:
      docker: image=namespace/image_name links=postgresql:db,redis:redis
    
    Create a container with no networking:
    
    - hosts: web
      sudo: yes
      tasks:
      docker: image=namespace/image_name net=none
    



    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-project>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

