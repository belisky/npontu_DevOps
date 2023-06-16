# Php CD Pipeline

- The DB is setup using master-slave replication in mysql using Ansible roles to Implement Availability support.
- The Docker image of the Application is built using Jenkins and pushed to DockerHub.
- After the image is successfully deployed to DockerHub, Ansible is configured to change the DockerImage version and automatically builds an updated Docker Container on the host which is still connected to the DB.

## Requirements

This role requires Ansible 1.4 or higher.

## Role Variables

The variables that can be passed to this role and a brief description about
them are as follows:

      # The port for mysql server to listen
      mysql_port: 3306

      # The bind address for mysql server
      mysql_bind_address: "0.0.0.0"

      # The root DB password
      mysql_root_db_pass: secret

      # A list that has all the databases to be
      # created and their replication status:
      mysql_db:
           - name: example_db1
             replicate: yes
           - name: example_db2
             replicate: no

      # A list of the mysql users to be created
      # and their password and privileges:
      mysql_users:
           - name: user1
             pass: verystrong
             priv: "*.*:ALL"

      # If the database is replicated the users
      # to be used for replication:
      mysql_repl_user:
        - name: repl
          pass: verystrong

      # The role of this server in replication:
      mysql_repl_role: master

      # A unique id for the mysql server (used in replication):
      mysql_db_id: 7
