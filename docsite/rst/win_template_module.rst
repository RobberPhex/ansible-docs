.. _win_template:


win_template - Templates a file out to a remote server.
+++++++++++++++++++++++++++++++++++++++++++++++++++++++

.. contents::
   :local:
   :depth: 1



Synopsis
--------

.. versionadded:: 1.9.2

Templates are processed by the Jinja2 templating language (http://jinja.pocoo.org/docs/) - documentation on the template formatting can be found in the Template Designer Documentation (http://jinja.pocoo.org/docs/templates/).
Six additional variables can be used in templates: ``ansible_managed`` (configurable via the ``defaults`` section of ``ansible.cfg``) contains a string which can be used to describe the template name, host, modification time of the template file and the owner uid, ``template_host`` contains the node name of the template's machine, ``template_uid`` the owner, ``template_path`` the absolute path of the template, ``template_fullpath`` is the absolute path of the template, and ``template_run_date`` is the date that the template was rendered. Note that including a string that uses a date in the template will result in the template being marked 'changed' each time.

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
    <td>dest</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Location to render the template to on the remote machine.</td>
    </tr>
            <tr>
    <td>src</td>
    <td>yes</td>
    <td></td>
        <td><ul></ul></td>
        <td>Path of a Jinja2 formatted template on the local server. This can be a relative or absolute path.</td>
    </tr>
        </table>


Examples
--------

.. raw:: html

    <br/>


::

    # Playbook Example  (win_template can only be run inside a playbook)
    - win_template: src=/mytemplates/file.conf.j2 dest=C:\temp\file.conf
    
    

.. note:: templates are loaded with ``trim_blocks=True``.
.. note:: By default, windows line endings are not created in the generated file.
.. note:: In order to ensure windows line endings are in the generated file, add the following header as the first line of your template: #jinja2: newline_sequence:'\r\n' and ensure each line of the template ends with \r\n.
.. note:: Beware fetching files from windows machines when creating templates because certain tools, such as Powershell ISE,  and regedit's export facility add a Byte Order Mark as the first character of the file, which can cause tracebacks.
.. note:: Use "od -cx" to examine your templates for Byte Order Marks.


    
This is a Core Module
---------------------

This source of this module is hosted on GitHub in the `ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ repo.
  
If you believe you have found a bug in this module, and are already running the latest stable or development version of Ansible, first look in the `issue tracker at github.com/ansible/ansible-modules-core <http://github.com/ansible/ansible-modules-core>`_ to see if a bug has already been filed.  If not, we would be grateful if you would file one.

Should you have a question rather than a bug report, inquries are welcome on the `ansible-project google group <https://groups.google.com/forum/#!forum/ansible-project>`_ or on Ansible's "#ansible" channel, located on irc.freenode.net.   Development oriented topics should instead use the similar `ansible-devel google group <https://groups.google.com/forum/#!forum/ansible-devel>`_.

Documentation updates for this module can also be edited directly by submitting a pull request to the module source code, just look for the "DOCUMENTATION" block in the source tree.

This is a "core" ansible module, which means it will receive slightly higher priority for all requests than those in the "extras" repos.

    
For help in developing on modules, should you be so inclined, please read :doc:`community`, :doc:`developing_test_pr` and :doc:`developing_modules`.

