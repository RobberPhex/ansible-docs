.. _ecs_taskdefinition:


ecs_taskdefinition - register a task definition in ecs
++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Creates or terminates task definitions


Requirements
------------

  * json
  * boto
  * botocore
  * boto3


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
    <td>arn<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The arn of the task description to delete</div></td></tr>
            <tr>
    <td>containers<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of containers definitions</div></td></tr>
            <tr>
    <td>family<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A Name that would be given to the task definition</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The AWS region to use. If not specified then the value of the AWS_REGION or EC2_REGION environment variable, if any, is used. See <a href='http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region'>http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region</a></div></br>
        <div style="font-size: small;">aliases: aws_region, ec2_region<div></td></tr>
            <tr>
    <td>revision<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A revision number for the task definition</div></td></tr>
            <tr>
    <td>state<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>present</li><li>absent</li></ul></td>
        <td><div>State whether the task definition should exist or be deleted</div></td></tr>
            <tr>
    <td>volumes<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A list of names of volumes to be attached</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    - name: "Create task definition"
      ecs_taskdefinition:
        containers:
        - name: simple-app
          cpu: 10
          essential: true
          image: "httpd:2.4"
          memory: 300
          mountPoints:
          - containerPath: /usr/local/apache2/htdocs
            sourceVolume: my-vol
          portMappings:
          - containerPort: 80
            hostPort: 80
        - name: busybox
          command:
            - "/bin/sh -c "while true; do echo '<html> <head> <title>Amazon ECS Sample App</title> <style>body {margin-top: 40px; background-color: #333;} </style> </head><body> <div style=color:white;text-align:center> <h1>Amazon ECS Sample App</h1> <h2>Congratulations!</h2> <p>Your application is now running on a container in Amazon ECS.</p>' > top; /bin/date > date ; echo '</div></body></html>' > bottom; cat top date bottom > /usr/local/apache2/htdocs/index.html ; sleep 1; done""
          cpu: 10
          entryPoint:
          - sh
          - "-c"
          essential: false
          image: busybox
          memory: 200
          volumesFrom:
          - sourceContainer: simple-app
        volumes:
        - name: my-vol
        family: test-cluster-taskdef
        state: present
      register: task_output

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
        <td> taskdefinition </td>
        <td> a reflection of the input parameters </td>
        <td align=center>  </td>
        <td align=center> dict inputs plus revision, status, taskDefinitionArn </td>
        <td align=center>  </td>
    </tr>
        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

