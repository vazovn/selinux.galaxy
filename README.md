# selinux.galaxy
This is an ansible role which sets up a selinux module for galaxy project. Aknowledgments to Sjur Hernes from USIT - UiO who helped with the code.

## Some info about the affected directories.

The directories

  * /srv/galaxy
  * /storage/galaxy

are given as an example, they can be replaced by the respective variables in `group_vars/<your-galaxy-ansible-playbook-conf-script>.yml`, e.g. `{{ galaxy_root }}` or `{{ galaxy_data_path }}`

The role can be set up for any other galaxy related directory, e.g. `galaxy.gie-proxy` or `galaxy.uwsgi`. Create a copy of the role and modify the module name and filenames accordingly.
 
## How to run the role

1. Copy the role to the `roles` directory of your galaxy project ansible playbook
2. Add the role to the bottom of your playbook configuration file:

```
roles:
    - galaxyproject.postgresql
  ...
    - role: galaxyproject.galaxy
      become: true
      become_user: "{{ galaxy_user.name }}"
      ===> here
    - selinux.galaxy
```

3. Make sure you have set up the variables used in the selinux role in the `group_vars/<your-galaxy-ansible-playbook-conf-script>.yml`
