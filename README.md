Elasticsearch Workshop
======================

Getting started
---------------

1. Clone the repo
2. Create some Ubuntu 14.04 hosts to put the cluster on
3. Fill in the host details:

        $ cp inventory.in inventory
        $ vim inventory

4. Set the passwords

        $ cp secrets.yml.in secrets.yml
        $ vim secrets.yml

5. Play!

        $ ansible-playbook -i inventory es-workshop.yml

You cluster is accessible via the proxy machine

    $ curl -u "user:pass" http://proxy-machine
    {
        "status" : 200,
        "name" : "es-workshop-1",
        "cluster_name" : "es-workshop",
        "version" : {
            "number" : "1.4.4",
            "build_hash" : "c88f77ffc81301dfa9dfd81ca2232f09588bd512",
            "build_timestamp" : "2015-02-19T13:05:36Z",
            "build_snapshot" : false,
            "lucene_version" : "4.10.3"
        },
        "tagline" : "You Know, for Search"
    }


You can also access haproxy stats, just go to http://188.166.17.197:11936/

# Not production ready!

This cluster is for workshops/experiments. In real world you need to at least:
* set up https connection to avoid sending passwords in plaintext
* separate data nodes from clients from masters

Ansible Playbooks
-----------------

Based on:
- https://github.com/Servers-for-Hackers
- https://github.com/snowplow/ansible-playbooks/
- https://github.com/Traackr/ansible-elasticsearch

HAProxy config:
- https://serversforhackers.com/load-balancing-with-haproxy