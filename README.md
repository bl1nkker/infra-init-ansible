# Ansible Server Template

this repository provides a basic Ansible template for initial server configuration and provisioning

## Features

- SSH setup
- Common package installation
- User configuration
- Basic security settings

## Requirements

## Usage

## Status

Work in progress

# TODO:

- Investigate Traefik

  - traefik must be able to create router with rules using `traefik_domain`:
    ```yaml
    {% if traefik_domain | length > 0 -%}
    - "traefik.http.routers.traefik-dashboard.rule=Host(`{{ traefik_domain }}`)"
    {% else -%}
    - "traefik.http.routers.traefik-dashboard.rule=Host(`{{ app_domain }}`) && Headers(`X-DS-Service`, `traefik-dashboard`)"
    {% endif -%}
    ```
  - try to deploy traefik modifying `playbooks/deploy/run.yml`

- Investigate Docker NFS
