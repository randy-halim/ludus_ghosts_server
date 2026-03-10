# Repository Archived

This was fixed upstream with [v1.4.0](https://github.com/frack113/ludus_ghosts_server/releases/tag/v1.4.0) and is a much more comprehensive fix, therefore archiving.

# Ansible Role: Ghosts Server

An Ansible Role that installs [GHOSTS Server](https://github.com/cmu-sei/GHOSTS) on linux.

This role is a fork of [frack113/ludus_ghosts_server](https://github.com/frack113/ludus_ghosts_server); however, containers pulled in `docker-compose.yml` are pulling the latest build which has breaking changes. This modifies the Compose file to the `v8.3.1` tag.

As a consequence, you'll have to manually install this role (using `ludus ansible role add -d`) and adjust the range config a little.

## Requirements

- Linux server
- Internet connection (docker images are 12GB)

## Role Variables

Available variables are listed below, along with default values (see `defaults/main.yml`):

None

## Dependencies

Ansible :

- community.docker
- community.grafana
- geerlingguy.docker

## Ports

Ghosts UI (<https://cmu-sei.github.io/GHOSTS/core/ui/>):

- 8080

Ghosts API (<https://cmu-sei.github.io/GHOSTS/core/api/>)

- 5000
- 3000 grafana

shadows (<https://cmu-sei.github.io/GHOSTS/shadows/>):

- 5900 API
- 7860 UI

pandora (<https://cmu-sei.github.io/GHOSTS/content/>):

- 80

## Example Playbook

## Example Ludus Range Config

```yaml
ludus:
  - vm_name: "{{ range_id }}-Ghosts"
    hostname: "{{ range_id }}-Ghosts"
    template: ubuntu-24.04-x64-server-template
    vlan: 99
    ip_last_octet: 2
    ram_gb: 6
    cpus: 4
    linux: true
    roles:
      - ludus_ghosts_server
```

## License

[//]: # (If you change the License type, be sure to change the actual LICENSE file as well)
GPLv3

## Author Information

This role was created by [@randy-halim](https://github.com/randy-halim), for [Ludus](https://ludus.cloud/).
