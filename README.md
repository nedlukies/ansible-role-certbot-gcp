Certbot GCP DNS
=========

Use Google Cloud DNS for wildcard certbot generation

Requirements
------------

- Google Service account with DNS Admin role

Role Variables
--------------

    certbot_gcp_credentials: "JSON file with GCP credentials"

    certbot_certs:
      - email: {{certbot_gcp_email}}
        domains:
          - *.example3.com
    certbot_gcp_acme_server: "{{ certbot_gcp_acme_test }}"

OR

    certbot_gcp_acme_server: "{{ certbot_gcp_acme_live }}"
    
Let's Encrypt server to use, defaults to test.

Example Playbook
----------------

    - role: geerlingguy.certbot
      vars:
        certbot_install_method: package
        certbot_certs: []
    - role: ansible-role-certbot-gcp
      vars:
        certbot_gcp_credentials: "{{ lookup('file', './zippy-catwalk-330810-d88be8a3abeb.json') }}"
        certbot_gcp_acme_server: "https://acme-v02.api.letsencrypt.org/directory"
        certbot_gcp_propagation_seconds: 15
        certbot_admin_email: 'email@email.com'
        certbot_certs:
          - domains: 
            - '*.example.com'
            - 'someotherdomain.com'
Dependencies
------------

- geerlingguy.pip
- geerlingguy.certbot



License
-------

MIT / BSD

Author Information
------------------

This role was created in 2018 by [Michael Porter](https://www.michaelpporter.com/). Adapted for GCP by Ned Lukies

