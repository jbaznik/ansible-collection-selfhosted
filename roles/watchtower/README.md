# selfhosted.watchtower

Installs [Watchtower](https://containrrr.dev/watchtower/) - a container-based solution for automating Docker container base image updates.

## Role Variables

- `watchtower_version`
  - Default: `latest`
  - Description: The version of Watchtower to install. See [tags](https://hub.docker.com/r/containrrr/watchtower/tags).
  - Type: str
  - Required: no
- `watchtower_install_dir`
  - Default: `/opt/docker/watchtower`
  - Description: The directory where Watchtower will be installed.
  - Type: str
  - Required: no
- `watchtower_env`
  - Default: See [watchtower_env_default](./vars/main.yml)
  - Description: Docker container environment variables. See [docs](https://containrrr.dev/watchtower/arguments/).
  - Type: dict
  - Required: no
- `watchtower_docker_settings`
  - Default: See [watchtower_docker_settings_default](./vars/main.yml)
  - Description: Docker container settings.
  - Type: dict
  - Required: no
- `watchtower_config_json_as_yaml`
  - Default: `{}`
  - Description: The contents of `config.json` in yaml format. See [docs](https://containrrr.dev/watchtower/private-registries/#create_the_configuration_file_manually).
  - Type: dict
  - Required: no

## Dependencies

- [community.docker](https://docs.ansible.com/ansible/latest/collections/community/docker/index.html)

## Example Playbook

```yaml
- hosts: localhost

  roles:
    - artyorsh.selfhosted.watchtower
``` 

## Custom schedule, disable containers, notifications

```yaml
- hosts: localhost

  vars:
    watchtower_env:
      WATCHTOWER_SCHEDULE: "0 0 6 * * *"
      WATCHTOWER_DISABLE_CONTAINERS: "forgejo-db"
      # https://containrrr.dev/watchtower/notifications/#shoutrrr_notifications
      WATCHTOWER_NOTIFICATION_URL: "slack://token-a/token-b/token-c"

  roles:
    - artyorsh.selfhosted.watchtower
```

## Private registries

```yaml
- hosts: localhost

  vars:
    watchtower_config_json_as_yaml:
      auths:
        ghcr.io:
          auth: "supersecret"

  roles:
    - artyorsh.selfhosted.watchtower
```
