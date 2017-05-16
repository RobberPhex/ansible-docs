.. _librato_annotation:


librato_annotation - create an annotation in librato
++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.6

Create an annotation event on the given annotation stream :name. If the annotation stream does not exist, it will be created automatically

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
    <td>api_key</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Librato account api key</td>
    </tr>
            <tr>
    <td>description</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The description contains extra meta-data about a particular annotationThe description should contain specifics on the individual annotation e.g. Deployed 9b562b2 shipped new feature foo!</td>
    </tr>
            <tr>
    <td>end_time</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The unix timestamp indicating the the time at which the event referenced by this annotation endedFor events that have a duration, this is a useful way to annotate the duration of the event</td>
    </tr>
            <tr>
    <td>links</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>See examples</td>
    </tr>
            <tr>
    <td>name</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The annotation stream nameIf the annotation stream does not exist, it will be created automatically</td>
    </tr>
            <tr>
    <td>source</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>A string which describes the originating source of an annotation when that annotation is tracked across multiple members of a population</td>
    </tr>
            <tr>
    <td>start_time</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>The unix timestamp indicating the the time at which the event referenced by this annotation started</td>
    </tr>
            <tr>
    <td>title</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The title of an annotation is a string and may contain spacesThe title should be a short, high-level summary of the annotation e.g. v45 Deployment</td>
    </tr>
            <tr>
    <td>user</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Librato account username</td>
    </tr>
        </table>


.. note:: Requires urllib2


.. note:: Requires base64


Examples
--------

.. raw:: html

    <br/>


::

    # Create a simple annotation event with a source
    - librato_annotation:
        user: user@example.com
        api_key: XXXXXXXXXXXXXXXXX
        title: 'App Config Change'
        source: 'foo.bar'
        description: 'This is a detailed description of the config change'
    
    # Create an annotation that includes a link
    - librato_annotation:
        user: user@example.com
        api_key: XXXXXXXXXXXXXXXXXX
        name: 'code.deploy'
        title: 'app code deploy'
        description: 'this is a detailed description of a deployment'
        links:
          - { rel: 'example', href: 'http://www.example.com/deploy' }
    
    # Create an annotation with a start_time and end_time
    - librato_annotation:
        user: user@example.com
        api_key: XXXXXXXXXXXXXXXXXX
        name: 'maintenance'
        title: 'Maintenance window'
        description: 'This is a detailed description of maintenance'
        start_time: 1395940006
        end_time: 1395954406



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

