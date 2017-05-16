.. _stackdriver:


stackdriver - Send code deploy and annotation events to stackdriver
+++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Send code deploy and annotation events to Stackdriver

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
    <td>annotated_by</td>
    <td>no</td>
    <td>Ansible</td>
        <td><ul></ul></td>
        <td>The person or robot who the annotation should be attributed to.</td>
    </tr>
            <tr>
    <td>deployed_by</td>
    <td>no</td>
    <td>Ansible</td>
        <td><ul></ul></td>
        <td>The person or robot responsible for deploying the code</td>
    </tr>
            <tr>
    <td>deployed_to</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The environment code was deployed to. (ie: development, staging, production)</td>
    </tr>
            <tr>
    <td>event</td>
    <td>no</td>
    <td></td>
        <td><ul><li>annotation</li><li>deploy</li></ul></td>
        <td>The type of event to send, either annotation or deploy</td>
    </tr>
            <tr>
    <td>event_epoch</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Unix timestamp of where the event should appear in the timeline, defaults to now. Be careful with this.</td>
    </tr>
            <tr>
    <td>instance_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>id of an EC2 instance that this event should be attached to, which will limit the contexts where this event is shown</td>
    </tr>
            <tr>
    <td>key</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>API key.</td>
    </tr>
            <tr>
    <td>level</td>
    <td>no</td>
    <td>INFO</td>
        <td><ul><li>INFO</li><li>WARN</li><li>ERROR</li></ul></td>
        <td>one of INFO/WARN/ERROR, defaults to INFO if not supplied.  May affect display.</td>
    </tr>
            <tr>
    <td>msg</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The contents of the annotation message, in plain text.  Limited to 256 characters. Required for annotation.</td>
    </tr>
            <tr>
    <td>repository</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The repository (or project) deployed</td>
    </tr>
            <tr>
    <td>revision_id</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The revision of the code that was deployed. Required for deploy events</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    - stackdriver: key=AAAAAA event=deploy deployed_to=production deployed_by=leeroyjenkins repository=MyWebApp revision_id=abcd123
    
    - stackdriver: key=AAAAAA event=annotation msg="Greetings from Ansible" annotated_by=leeroyjenkins level=WARN instance_id=i-abcd1234



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

