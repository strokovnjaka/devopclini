# Excercises in style: app stack deployment

## With `cloud-init`

There is a self-describing bash script `lscript` that drops existing, creates, launches, and tests the deployed `shroomate` app in a new VM.

Requirements for `lscript`: 
- `pcregrep` for getting VM's IP, install with `sudo apt-get install pcregrep`

### Notes to `cloud-init` variant:

- `write_files` messes permissions with created dirs, filling data in `runcmd`
- `nodejs not` installable with `packages` directive, using `snap` instead
- make sure other VM tools such as `vagrant` are not running
- using `lxd` version `5.0.2` did not copy `cloud-init` config to VM, worked after upgrading to `5.19`
- HTTPS not done, steps would be 
  1. get VM's external IP
  2. get domain
  3. put both into a DNS
  4. setup certificate handling e.g. `certbot`

