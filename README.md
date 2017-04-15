# Ansible role Duply (Duplicity)

Version: 0.0.1

Supported OS: Ubuntu

Ansible role Duply

## Role variables
```
# Example config
# duplicity_configs:
#     - name: test
#       settings:
#         GPG_KEY: '_KEY_ID_'  # Use GPG KEY or PW
#         GPG_PW: <Very secret password>
#         TARGET: 's3://s3-<region endpoint name>.amazonaws.com/<bucket name>/<folder name>'
#         SOURCE: '/' # Backup entire filesystem
#         MAX_AGE: 6M  # 6 months
#       excludes:
#         - /dev
#         - /home/*/.cache
#         - /home/*/.ccache
#         - /lost+found
#         - /media
#         - /mnt
#         - /proc
#         - /root/.cache
#         - /root/.ccache
#         - /run
#         - /selinux
#         - /sys
#         - /tmp
#         - /var/cache/*/*
#         - /var/log
#         - /var/run
#         - /var/tmp

```

## Example
```
- hosts: all
  roles:
   - role: duplicity
     duplicity_configs:
       - name: test
```

## Configuring AWS credentials (only required for S3 backup)
```
- name: Install AWS credentials for Duplycity/Boto
  copy:
    dest: /root/.boto
    content: |
      [Credentials]
      aws_access_key_id = {{ aws_access_key_id }}
      aws_secret_access_key = {{ aws_secret_access_key }}
  tags:
    - duplicity
```
