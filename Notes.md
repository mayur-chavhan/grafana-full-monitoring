# Traefik 

1. Add Environment Variables

- Create enn file and add environment

`nano .env`

- add below environment

```
DOMAIN=localhost
EMAIL=admin@localhost
CERT_RESOLVER=
TRAEFIK_USER=admin
TRAEFIK_PASSWORD_HASH=$2y$10$zi5n43jq9S63gBqSJwHTH.nCai2vB0SW/ABPGg2jSGmJBVRo0A.ni
```

Note that you should leave `CERT_RESOLVER` variable empty if you test your deployment locally. The password is admin and you might want to change it before deploying to production.

   2. Set Your Own Password

If you're curious about HTTP basic auth and how it can be used with Traefik, you can read the full post. Here is the excerpt and it assumes you already installed htpasswd:

```nano
htpasswd -nBC 10 admin

New password:
Re-type new password:

admin:$2y$10$zi5n43jq9S63gBqSJwHTH.nCai2vB0SW/ABPGg2jSGmJBVRo0A.ni
```

# Authelia

- update .env for domain

- Run shell script to generate password,

create_user_pass.sh

------------------

- Update "yourusername", Displayname and Copy the shell script generated password and paste this in "users_database.yml" also update email as well very important for verification.

  yourusername:
    displayname: "Barry Allen"
    password: "generateandpasteithere"
    email: youremail@gmail.com
------------------


- Change below values at "configuration.yml"

jwt_secret: a_very_important_secret

------------------

default_redirection_url: https://auth.yourdomain.com

------------------

- According to protect sites, Add them down below with required policy.

    - domain: siteyouwanttobypassforauth
      policy: bypass
    - domain: my.impsite.in
      policy: one_factor
------------------
storage:
  encryption_key: QEFS8F4AhqCyKmyqrrwc6mjCc

------------------
```
