# Server

- Update the domain.com to your domain in .env file
- ``` docker-compose up -d ``` 
- 




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
