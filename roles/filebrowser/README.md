# selfhosted.filebrowser

Installs [Filebrowser](https://github.com/filebrowser/filebrowser) - a web-based file browser.

> [!NOTE]
> This role is not actively maintained as it is currently not in use (since June 2024).
> Bugs may be present due to incompatibility with the latest versions of Filebrowser image.

## Role Variables

- `filebrowser_version`
  - Default: `latest`
  - Description: The version of Filebrowser to install. See [tags](https://hub.docker.com/r/filebrowser/filebrowser/tags).
  - Type: str
  - Required: no
- `filebrowser_port`
  - Default: `8081`
  - Description: The port on which Filebrowser will be accessible.
  - Type: int
  - Required: no
- `filebrowser_install_dir`
  - Default: `/opt/docker/filebrowser`
  - Description: The directory where Filebrowser will be installed.
  - Type: str
  - Required: no
- `filebrowser_env`
  - Default: See [filebrowser_env_default](./vars/main.yml)
  - Description: Docker container environment variables. See [docs](https://filebrowser.org/configuration).
  - Type: dict
  - Required: no
- `filebrowser_docker_settings`
  - Default: See [filebrowser_docker_settings_default](./vars/main.yml)
  - Description: Docker container settings.
  - Type: dict
  - Required: no

## Dependencies

- [community.docker](https://docs.ansible.com/ansible/latest/collections/community/docker/index.html)

## Example Playbook

```yaml
- hosts: localhost

  roles:
    - artyorsh.selfhosted.filebrowser
``` 