.. _ecs_task:


ecs_task - run, start or stop a task in ecs
+++++++++++++++++++++++++++++++++++++++++++

.. versionadded:: 2.0


.. contents::
   :local:
   :depth: 1


Synopsis
--------

Creates or deletes instances of task definitions.




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
    <td>cluster<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The name of the cluster to run the task on</div></td></tr>
            <tr>
    <td>container_instances<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The list of container instances on which to deploy the task</div></td></tr>
            <tr>
    <td>count<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>How many new instances to start</div></td></tr>
            <tr>
    <td>operation<br/><div style="font-size: small;"></div></td>
    <td>yes</td>
    <td></td>
        <td><ul><li>run</li><li>start</li><li>stop</li></ul></td>
        <td><div>Which task operation to execute</div></td></tr>
            <tr>
    <td>overrides<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A dictionary of values to pass to the new instances</div></td></tr>
            <tr>
    <td>region<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The AWS region to use. If not specified then the value of the AWS_REGION or EC2_REGION environment variable, if any, is used. See <a href='http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region'>http://docs.aws.amazon.com/general/latest/gr/rande.html#ec2_region</a></div></br>
        <div style="font-size: small;">aliases: aws_region, ec2_region<div></td></tr>
            <tr>
    <td>started_by<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>A value showing who or what started the task (for informational purposes)</div></td></tr>
            <tr>
    <td>task<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The task to stop</div></td></tr>
            <tr>
    <td>task_definition<br/><div style="font-size: small;"></div></td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td><div>The task definition to start or run</div></td></tr>
        </table>
    </br>



Examples
--------

 ::

    # Simple example of run task
    - name: Run task
      ecs_task:
        operation: run
        cluster: console-sample-app-static-cluster
        task_definition: console-sample-app-static-taskdef
        count: 1
        started_by: ansible_user
      register: task_output
    
    # Simple example of start task
    
    - name: Start a task
      ecs_task:
          operation: start
          cluster: console-sample-app-static-cluster
          task_definition: console-sample-app-static-taskdef
          task: "arn:aws:ecs:us-west-2:172139249013:task/3f8353d1-29a8-4689-bbf6-ad79937ffe8a"
          container_instances:
          - arn:aws:ecs:us-west-2:172139249013:container-instance/79c23f22-876c-438a-bddf-55c98a3538a8
          started_by: ansible_user
      register: task_output
    
    - name: Stop a task
      ecs_task:
          operation: stop
          cluster: console-sample-app-static-cluster
          task_definition: console-sample-app-static-taskdef
          task: "arn:aws:ecs:us-west-2:172139249013:task/3f8353d1-29a8-4689-bbf6-ad79937ffe8a"

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
        <td> task </td>
        <td> details about the tast that was started </td>
        <td align=center>  </td>
        <td align=center> complex </td>
        <td align=center> TODO: include sample </td>
    </tr>
        
    </table>
    </br></br>



    
This is an Extras Module
------------------------

For more information on what this means please read :doc:`modules_extra`

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

