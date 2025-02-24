# libvirt_manager

Used for checking if:
    - there's SVM/VMX virtualization, enable it if not
    - install libvirt packages and dependencies and add group and user to libvirt group if necessary,


## Privilege escalation

`become` - Required in:
    - `virsh_checks.yml`: For creating libvirt group if needed and also append user to this group if it's not there.
    - `virtualization_prerequisites.yml`: For enabling VMX/SVM module with modprobe.
    - `packages.yml`: Install all libvirt dependencies.
    - `polkit_rules.yml`: Add polkit rules under `/etc/`.

## Parameters
* `cifmw_libvirt_manager_basedir`: (String) Base directory. Defaults to `cifmw_basedir` which defaults to `~/ci-framework-data`.
* `cifmw_libvirt_manager_enable_virtualization_module`: (Boolean) If `true` it will enable the virtualization module in case it's not already and if the hosts allow it. Defaults to `false`.
* `cifmw_libvirt_manager_user`: (String) User used for libvirt. Default: the one in the environment variable `USER`.
* `cifmw_libvirt_manager_images_url`: (String) Location basedir for the image URI. Defaults to `https://cloud.centos.org/centos/9-stream/x86_64/images`.
* `cifmw_libvirt_manager_configuration`: (Dict) Structure describing the libvirt layout (networking and VMs).
* `cifmw_libvirt_manager_crc_pool`: (String) CRC pool machine location. Defaults to `cifmw_crc_pool` which defaults to `~/.crc/machines/crc`.
* `cifmw_libvirt_manager_installyamls`: (String) install_yamls repository location. Defaults to `cifmw_installyamls_repos` which defaults to `../..`
* `cifmw_libvirt_manager_dryrun`: (Boolean) Toggle ci_make `dry_run` parameter. Defaults to `false`.
* `cifmw_libvirt_manager_compute_amount`: (Integer) State the amount of computes you want. Defaults to `1`.
* `cifmw_libvirt_manager_skip_edpm_compute_repos`: (Boolean) Intentionally skips the configuration of repos on EDPM compute nodes. Defaults to `False`.
