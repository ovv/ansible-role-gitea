ovv.gitea
=========

[![Build Status](https://travis-ci.org/ovv/ansible-role-gitea.svg?branch=master)](https://travis-ci.org/ovv/ansible-role-gitea)

Ansible role to install and configure [gitea](https://gitea.io/).

Requirements
------------

A PostgreSQL installation is required. We recommend using [pyslackers.postgres](https://github.com/pyslackers/ansible-role-postgres).

Installation
------------

To install this roles clone it into your roles directory.

```bash
$ git clone https://github.com/ovv/ansible-role-gitea.git ovv.gitea
```

If your playbook already reside inside a git repository you can clone it by using git submodules.

```bash
$ git submodule add -b master https://github.com/ovv/ansible-role-gitea.git ovv.gitea
```

Role Variables
--------------

* `gitea_group`: Running group (default to `gitea`).
* `gitea_user`: Running user (default to `gitea`).
* `gitea_home`: Home & working directory (default to `/home/gitea`).
* `gitea_version`: Version to install (default to `1.3.2`).

* `gitea_db_name`: Name of the database (default to `gitea`).
* `gitea_db_user`: Connection user to the database (default to `gitea`).
* `gitea_db_password`: Password of the database.

* `gitea_http_port`: Listening http port (default to `3000`).
* `gitea_http_addr`: Listening http address (default to `0.0.0.0`).
* `gitea_url`: Extenral access url (default to `http://localhost:{{ gitea_http_port}}`).
* `gitea_ssh_domain`: Domain for ssh access (default to `localhost`).
* `gitea_ssh_port`: Listening ssh port (default to `22`).
* `gitea_noreply_addr`: Email address for sending email (default to `noreply@example.com`).

* `gitea_admin_username`: Admin username.
* `gitea_admin_password`: Admin password.
* `gitea_admin_email`: Admin email.

* `gitea_internal_token`: Long string for internal secret token.
* `gitea_secret_key`: Small string for secret key.
* `gitea_lfs_jwt_secret`: 43 character string for JWT secret.

Example Playbook
----------------

```yml
- hosts: gitea
  roles:
    - pyslackers.postgres
    - ovv.gitea
  vars:
    gitea_db_password: supersecurepassword

    gitea_admin_username: user1
    gitea_admin_password: password
    gitea_admin_email: gitea@example.com

    gitea_internal_token: superlongandsupersecuretoken&superlongandsupersecuretoken&superlongandsupersecuretoken&superlongandsupersecuretoken
    gitea_secret_key: secretkey
    gitea_lfs_jwt_secret: randomfortythreecharacterlenghtstringsecret

    # pyslackers.postgres variables
    postgres_users:
      gitea:
        password: supersecurepassword
```

License
-------

MIT
