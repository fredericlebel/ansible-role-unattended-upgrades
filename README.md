Role Name
=========

fredericlebel.ansible_role_unattended-upgrades – Install and configure automatic updates on Ubuntu using **unattended-upgrades**.

Requirements
------------

* Ubuntu or Debian-based system
* Ansible 2.12+
* Python `apt` module (installed by default on most Debian/Ubuntu systems)

Role Variables
--------------

Below is the full list of configurable variables (with their defaults) from `defaults/main.yml`.

| Variable | Default | Description |
|----------|--------|-------------|
| `unattended_upgrades__allowed_origins` | <pre>- "${distro_id}:${distro_codename}"<br>- "${distro_id}:${distro_codename}-security"<br>- "${distro_id}ESMApps:${distro_codename}-apps-security"<br>- "${distro_id}ESM:${distro_codename}-infra-security"</pre> | APT repository origins allowed for automatic upgrades. |
| `unattended_upgrades__package_blacklist` | `[]` | List of packages (regex) to exclude from upgrades. |
| `unattended_upgrades__devrelease` | `"auto"` | Whether to automatically upgrade to development releases. |
| `unattended_upgrades__auto_fix_interrupted_dpkg` | `true` | Automatically fix interrupted dpkg operations. |
| `unattended_upgrades__minimal_steps` | `false` | Run upgrades in minimal steps (can be interrupted). |
| `unattended_upgrades__install_on_shutdown` | `false` | Install upgrades when the system is shutting down. |
| `unattended_upgrades__mail` | `""` | Email address for update reports (empty = no email). |
| `unattended_upgrades__mail_report` | `"on-change"` | Email report level: `always`, `only-on-error`, or `on-change`. |
| `unattended_upgrades__remove_unused_kernel_packages` | `true` | Remove unused kernel packages after upgrades. |
| `unattended_upgrades__remove_new_unused_dependencies` | `true` | Remove newly installed unused dependencies. |
| `unattended_upgrades__remove_unused_dependencies` | `false` | Remove unused dependencies after upgrade. |
| `unattended_upgrades__automatic_reboot` | `false` | Automatically reboot if required after upgrades. |
| `unattended_upgrades__automatic_reboot_with_users` | `true` | Reboot even when users are logged in. |
| `unattended_upgrades__automatic_reboot_time` | `"02:00"` | Time of automatic reboot if enabled. |
| `unattended_upgrades__acquire_http_dl_limit` | `""` | Limit download speed in kB/s (empty = disabled). |
| `unattended_upgrades__syslog_enable` | `false` | Enable logging to syslog. |
| `unattended_upgrades__syslog_facility` | `"daemon"` | Syslog facility to use. |
| `unattended_upgrades__only_on_ac_power` | `true` | Only run updates when on AC power. |
| `unattended_upgrades__skip_updates_on_metered_connections` | `true` | Skip updates on metered connections. |
| `unattended_upgrades__verbose` | `false` | Enable verbose logging. |
| `unattended_upgrades__debug` | `false` | Enable debug logging. |
| `unattended_upgrades__allow_downgrade` | `false` | Allow downgrades if Pin-Priority > 1000. |
| `unattended_upgrades__allow_apt_mark_fallback` | `true` | Enable fallback for APT Mark if needed. |

Dependencies
------------

None.

Example Playbook
----------------

```yaml
- hosts: all
  become: true
  roles:
    - role: fredericlebel.ansible_role_unattended-upgrades
      vars:
        unattended_upgrades__automatic_reboot: true
        unattended_upgrades__mail: "admin@example.com"
```

License
-------

MIT

Author information
------------------

Frédéric Lebel
GitHub: https://github.com/frleb
