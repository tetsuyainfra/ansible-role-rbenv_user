tetsuyainfra.rbenv_user
=========

rbenv for User envrionment install role

Requirements
------------

Any pre-requisites that may not be covered by Ansible itself or the role should be mentioned here. For instance, if the role uses the EC2 module, it may be a good idea to mention in this section that the boto package is required.

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

A list of other roles hosted on Galaxy should go here, plus any details in regards to parameters that may need to be set for other roles, or variables that are used from other roles.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - name: Setting with Role
      hosts: "localhost"
      vars:
        rbenv_user_install: yes
        rbenv_user_install_path: '$HOME/.rbenv' # you can use shell envionment variable
        rbenv_user_clean_up: no
        rbenv_user_accept_hostkey: yes
        rbenv_user_rbenv_version: "v1.1.2"
        rbenv_user_version_up: no               # if set yes, set branch is master and pull origin master
        rbenv_user_ruby_versions:
          - 2.6.6
          - 2.7.2
        rbenv_user_package_install_user: root # 仮にSUDO権限もってないユーザーでインストールしたらどうなるのか
                                              # 内部で都度becomeするのが良いのでは？
      vars_files:
        - "{{ playbook_dir }}/vars/dotfiles.yml"
        - "{{ playbook_dir }}/vars/dot_vars.yml"
      roles:
        - role: "rbenv_user"
          rbevn_user_name: "foobaruser"

if you exec on localhost, and don't write yourself name

      hosts: "localhost"
      ...
      roles:
        - role: "rbenv_user"
          become_user: "{{ ansible_env['USER'] }}" # ansible-playbook execute user (work around)



License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
