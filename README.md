Kibana Object Management
========================

Using Jinja2 templates manage Kibana objects: dashboards and visualizations.
You can find examples of Kibana objects templates in `test/templates`.
The role will upload them to Elasticsearch directly using its API. This means
you can run Ansible locally, without SSH to the system.

Role Variables
--------------

Path to the Jinja2 templates for each object type:

 - kibana_visualizations
 - kibana_dashboards

The path can be specific or have regex in it. See example bellow.

Elasticsearch connection info:

 - es_host - FQDN or IP, without 'http://' or anything of the sort
 - es_port - There is no default, so you must set it to something (including 80)

Example Playbook
----------------

    - hosts: 127.0.0.1
      connection: local
      gather_facts: no
      vars:
        es_host: elasticsearch.example.com
        es_port: 9200
        kibana_visualizations: "templates/visualization-*.json.j2"
        kibana_dashboarsd "templates/dashboard-*.json.j2"
      roles:
         - ansible-kibana-management

License
-------

GPLv3
