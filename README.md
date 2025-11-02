# Simple Example Molecule Scenario Delegated to OpenTofu

1. First run `molecule init -s hello-delegated` to create the scenario.
1. Add `molecule/hello-delegated/vars.yml` with the values in the example in this repo.
1. Edit `molecule/hello-delegated/create.yml` to add the tofu project setup and `community.general.terraform` blocks.
1. Edit `molecule/hello-delegated/destroy.yml` to add the `community.general.terraform` block.
1. Edit `molecule/hello-delegated/converge.yml` and `molecule/hello-delegated/verify.yml` as usual.
1. Give it a test run! `molecule test -s hello-delegated`

## vars.yml

- `ssh_user` - The username of the user on the test VMs. Used by molecule.
- `ssh_port` - The port ssh is listening on in the test VMs. Used by molecule.
- `ssh_privkey_path` - The local path to the ssh private key used to log into the test VMs. Used by molecule.
- `proxmox_user` - The proxmox API username. Used by my tofu project.
- `proxmox_password` - The proxmox API user password. Used by my tofu project.
- `tofu_project_repo` - The url of the git repo containing the tofu project. The example points at the `example` branch of my molecule delegate project. Used by the `community.general.terraform` tasks.
- `tofu_project_version` - The branch/ref/tag of the tofu project repo to checkout. Used by the `community.general.terraform` tasks.


## References
- https://blog.stephane-robert.info/post/ansible-molecule-delegated-driver-terraform/
  - It's in french but the yaml is pretty clean and clear.
  - A more complex example than this one.
- https://github.com/haxwithaxe/tofu-proxmox-molecule-delegate.git `example` branch is going to work with this example assuming you have a proxmox machine with the permissions setup for the `proxmox_user`.
  - https://search.opentofu.org/provider/telmate/proxmox/latest The tofu proxmox provider used in the above tofu project.
