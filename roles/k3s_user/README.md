k3s_user
=========

This role sets up the target host for interacting with the k3s cluster. 

Requirements
------------

The only requirement is that the host is running Linux. The role installs `kubectl` and `helm` packages on Debian-based or RHEL-based hosts.


Role Variables
--------------

These variables can be defined at the group or host level, but are already defined as defaults within the role. They **shouldn't** be changed unless absolutely necessary. 

`kubeconfig_source_host`: This is the host that the role will copy the `.kube/config` file from. By default it's set to `"{{ groups['server'][0] }}"` so that it's copied from the first node listed within the k3s_cluster/servers group.

`remote_target_user` and `remote_source_user`: By default this is set to `{{ ansible_user }}`, but it should be set to whatever user will be running k3s on the hosts, and whatever user is running kubectl against them. 

`source_kubeconfig_path`: THe location of the config file on the server host. By default this is set to `"/home/{{ remote_source_user }}/.kube/config"`
`dest_kube_dir` and `dest_kubeconfig_path`: The location of the .kube directory on the user host and the full filepath. By default they're set to `"/home/{{ remote_target_user }}/.kube"` and `"{{ dest_kube_dir }}/config"` respectively.

`controller_temp_kubeconfig_dir` and `controller_temp_fetched_config_path`: The temporary path on the Ansible controller where the config file is stored. Set as `"/tmp/ansible_kubeconfig_transfer_{{ ansible_date_time.epoch }}"` and `"{{ controller_temp_kubeconfig_dir }}/config"` respectively. 

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: workstations
      roles:
         - k3s-user

License
-------

BSD

Author Information
------------------

**Taylor Cohron:**
* [GitHub](https://github.com/untraceablez)
* [Email](mailto:taylorcohrontech@gmail.com)


