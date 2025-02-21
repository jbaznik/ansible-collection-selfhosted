# selfhosted.changedetection

Installs the [ChangeDetection](https://changedetection.io/) and [Selenium](https://hub.docker.com/r/seleniarm/standalone-chromium) containers - a page change monitoring tools with alerts.

> [!NOTE]
> This role is not actively maintained as it is currently not in use (since June 2024).
> Bugs may be present due to incompatibility with the latest versions of ChangeDetection/Selenium images.

## Role Variables

- `changedetection_version`
  - Default: `latest`
  - Description: The version of ChangeDetection to install. See [tags](https://hub.docker.com/r/dgtlmoon/changedetection.io/tags).
  - Type: str
  - Required: no
- `changedetection_webui_port`
  - Default: `5000`
  - Description: The port on which ChangeDetection will be accessible.
  - Type: int
  - Required: no
- `changedetection_install_dir`
  - Default: `/opt/docker/changedetection`
  - Description: The directory where ChangeDetection will be installed.
  - Type: str
  - Required: no
- `changedetection_env`
  - Default: See [changedetection_env_default](./vars/main.yml)
  - Description: Docker container environment variables. See [docs](https://changedetection.io/docs/configuration/environment-variables).
  - Type: dict
  - Required: no
- `changedetection_selenium_version`
  - Default: `latest`
  - Description: The version of Selenium to install. See [tags](https://hub.docker.com/r/seleniarm/standalone-chromium/tags).
  - Type: str
  - Required: no
- `changedetection_selenium_port`
  - Default: `5001`
  - Description: The port on which Selenium will be accessible.
  - Type: int
  - Required: no
- `changedetection_selenium_env`
  - Default: See [changedetection_selenium_env_default](./vars/main.yml)
  - Description: Docker container environment variables for Selenium. See [docs](https://github.com/dgtlmoon/changedetection.io/wiki/Fetching-pages-with-WebDriver).
  - Type: dict
  - Required: no
- `changedetection_docker_settings`
  - Default: See [changedetection_docker_settings_default](./vars/main.yml)
  - Description: Docker container settings. This is applied to both the ChangeDetection and Selenium containers.
  - Type: dict
  - Required: no

## Dependencies

- [community.docker](https://docs.ansible.com/ansible/latest/collections/community/docker/index.html)

## Example Playbook

```yaml
- hosts: localhost

  roles:
    - artyorsh.selfhosted.changedetection
``` 