.
* _connection_plugins:

Connection plugins
==================

* Connection plugins 
  * enable Ansible
    * can connect -- to the -- target hosts
      * -> Ansible can execute tasks | target hosts
  * limitations
    * ⚠️use 1! connection plugin / host | concrete time⚠️
  * types
    * built-in
      * MOST used ones
        * paramiko SSH
        * native ssh 
        * local
      * how to use?
        * | playbooks
        * if you want to talk to remote machines -> use `/usr/bin/ansible` 
    * custom
      * [how to create](../dev_guide/developing_plugins.md#developing-particular-plugin-types)
  * if you want to change the connection plugin | your tasks -> use the `connection` keyword

TODO: 
The basics of these connection types are covered in the :ref:`getting started<intro_getting_started>` section.

``ssh`` plugins
---------------

Because SSH is the default protocol used in system administration and the protocol most used in Ansible, SSH options are included in the command line tools
* See :ref:`ansible-playbook` for more details.

.
* _using_connection:

Using connection plugins
------------------------

You can set the connection plugin globally with :ref:`configuration<ansible_configuration_settings>`, at the command line (``-c``, ``--connection``), as a :ref:`keyword <playbook_keywords>` in your play, or by setting a :ref:`variable<behavioral_parameters>`, most often in your inventory.
For example, for Windows machines, you might want to set the :ref:`winrm <winrm_connection>` plugin as an inventory variable.

Most connection plugins can operate with minimal configuration
* By default, they use the :ref:`inventory hostname<inventory_hostnames_lookup>` and defaults to find the target host.

Plugins are self-documenting
* Each plugin should document its configuration options
* The following are connection variables common to most connection plugins:

:ref:`ansible_host<magic_variables_and_hostvars>`
    The name of the host to connect to, if different from the :ref:`inventory <intro_inventory>` hostname.
:ref:`ansible_port<faq_setting_users_and_ports>`
    The ssh port number, for :ref:`ssh <ssh_connection>` and :ref:`paramiko_ssh <paramiko_connection>` it defaults to 22.
:ref:`ansible_user<faq_setting_users_and_ports>`
    The default username to use for log in
* Most plugins default to the 'current user running Ansible'.

Each plugin might also have a specific version of a variable that overrides the general version
* For example, ``ansible_ssh_host`` for the :ref:`ssh <ssh_connection>` plugin.

.
* _connection_plugin_list:

Plugin list
-----------

You can use ``ansible-doc -t connection -l`` to see the list of available plugins.
Use ``ansible-doc -t connection <plugin name>`` to see plugin-specific documentation and examples.


.
* seealso::

   :ref:`Working with Playbooks<working_with_playbooks>`
       An introduction to playbooks
   :ref:`callback_plugins`
       Callback plugins
   :ref:`filter_plugins`
       Filter plugins
   :ref:`test_plugins`
       Test plugins
   :ref:`lookup_plugins`
       Lookup plugins
   :ref:`vars_plugins`
       Vars plugins
   :ref:`Communication<communication>`
       Got questions? Need help? Want to share your ideas? Visit the Ansible communication guide
