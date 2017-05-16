.. _datadog_event:


datadog_event - Posts events to DataDog  service
++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.3

Allows to post events to DataDog (www.datadoghq.com) service.
Uses http://docs.datadoghq.com/api/#events API.

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
    <td>aggregation_key</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>An arbitrary string to use for aggregation.</td>
    </tr>
            <tr>
    <td>alert_type</td>
    <td>no</td>
    <td>info</td>
        <td><ul><li>error</li><li>warning</li><li>info</li><li>success</li></ul></td>
        <td>Type of alert.</td>
    </tr>
            <tr>
    <td>api_key</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Your DataDog API key.</td>
    </tr>
            <tr>
    <td>date_happened</td>
    <td>no</td>
    <td>now</td>
        <td><ul></ul></td>
        <td>POSIX timestamp of the event.Default value is now.</td>
    </tr>
            <tr>
    <td>priority</td>
    <td>no</td>
    <td>normal</td>
        <td><ul><li>normal</li><li>low</li></ul></td>
        <td>The priority of the event.</td>
    </tr>
            <tr>
    <td>tags</td>
    <td>no</td>
    <td></td>
        <td><ul></ul></td>
        <td>Comma separated list of tags to apply to the event.</td>
    </tr>
            <tr>
    <td>text</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The body of the event.</td>
    </tr>
            <tr>
    <td>title</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>The event title.</td>
    </tr>
            <tr>
    <td>validate_certs</td>
    <td>no</td>
    <td>yes</td>
        <td><ul><li>yes</li><li>no</li></ul></td>
        <td>If <code>no</code>, SSL certificates will not be validated. This should only be used on personally controlled sites using self-signed certificates. (added in Ansible 1.5.1)</td>
    </tr>
        </table>


.. note:: Requires urllib2


Examples
--------

.. raw:: html

    <br/>


::

    # Post an event with low priority
    datadog_event: title="Testing from ansible" text="Test!" priority="low"
                   api_key="6873258723457823548234234234"
    # Post an event with several tags
    datadog_event: title="Testing from ansible" text="Test!"
                   api_key="6873258723457823548234234234"
                   tags=aa,bb,cc



    
This is an Extras Module
------------------------

This source of this module is hosted on GitHub in the `ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-extras <http://github.com/ansible/ansible-modules-extras>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>` or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

Note that this module is designated a "extras" module.  Non-core modules are still fully usable, but may receive slightly lower response rates for issues and pull requests.
Popular "extras" modules may be promoted to core modules over time.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

