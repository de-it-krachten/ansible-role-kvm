[![CI](https://github.com/de-it-krachten/ansible-role-kvm/workflows/CI/badge.svg?event=push)](https://github.com/de-it-krachten/ansible-role-kvm/actions?query=workflow%3ACI)


# ansible-role-kvm

Installs KVM with libvirt



## Dependencies

#### Roles
None

#### Collections
- community.general

## Platforms

Supported platforms

- Red Hat Enterprise Linux 8<sup>1</sup>
- Red Hat Enterprise Linux 9<sup>1</sup>
- Red Hat Enterprise Linux 10<sup>1</sup>
- RockyLinux 8
- RockyLinux 9
- RockyLinux 10
- OracleLinux 8
- OracleLinux 9
- OracleLinux 10
- AlmaLinux 8
- AlmaLinux 9
- AlmaLinux 10
- Debian 11 (Bullseye)
- Debian 12 (Bookworm)
- Debian 13 (Trixie)
- Ubuntu 20.04 LTS
- Ubuntu 22.04 LTS
- Ubuntu 24.04 LTS
- Fedora 41
- Fedora 42

Note:
<sup>1</sup> : no automated testing is performed on these platforms

## Role Variables
### defaults/main.yml
<pre><code>
# Name of the libvirt daemon
kvm_service: libvirtd

# Allow nested virtulization
kvm_nested: false

# Should be install the full set of KVM features
kvm_full: false

# Should the desktop packages be installed
kvm_desktop: false

# KVM group
kvm_group: kvm

# List of KVM users that should be member of `kvm`
kvm_users: []
</pre></code>

### defaults/family-Debian.yml
<pre><code>
kvm_packages:
  - kmod
  - qemu-kvm
  - libvirt-clients
  - libvirt-daemon-system
  - bridge-utils
  - virtinst

kvm_packages_optional: []
##  - libvirt-devel
#  - virt-top
#  - libguestfs-tools
#  - guestfs-tools

kvm_packages_desktop:
  - virt-manager
</pre></code>

### defaults/family-RedHat.yml
<pre><code>
kvm_packages:
  - bridge-utils
  - libvirt
  - qemu-kvm
  - virt-install

kvm_packages_optional:
  - libvirt-devel
  - virt-top
  - libguestfs-tools
  - guestfs-tools

kvm_packages_desktop:
  - virt-manager
</pre></code>




## Example Playbook
### molecule/default/converge.yml
<pre><code>
- name: sample playbook for role 'kvm'
  hosts: all
  become: 'yes'
  tasks:
    - name: Include role 'kvm'
      ansible.builtin.include_role:
        name: kvm
</pre></code>
