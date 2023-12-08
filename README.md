# Excercises in style: app stack deployment

## With `cloud-init`

With this recipe a [Shroomate](https://github.com/strokovnjaka/shroomate) demo app stack can be deployed on a VM with `lxd`.

The recipe consists of a self-explanatory bash script `lscript` that drops existing, creates, launches, and tests the deployed `shroomate` app in a new VM.

### Prerequisites

1. `lxd init --auto` to initialize lxd stuff
2. `sudo snap refresh lxd --channel latest/stable` needed if broken LTS `lxd 5.0.2` is present
3. `sudo apt-get update && sudo apt-get install pcregrep` for getting VM's IP in the `lscript`

### Deploy

To deploy a new VM running `shroomate` app stack and check that it's working run

```
git clone https://github.com/strokovnjaka/devopclini && cd devopclini && ./lscript
```

### Notes:

- `write_files` messes permissions with created dirs, filling data in `runcmd`
- `nodejs not` installable with `packages` directive, using `snap` instead
- make sure other VM tools such as `vagrant` are not running
- using `lxd` version `5.0.2` did not copy `cloud-init` config to VM, worked after upgrading to `5.19`
- HTTPS not done, steps would be 
  1. get VM's external IP
  2. get domain
  3. put both into a DNS
  4. setup certificate handling e.g. `certbot`
  5. setup an `nginx` https site for the app
- [Shroomate](https://github.com/strokovnjaka/shroomate) repo is publicly accessible

