# Excercises in style: app stack deployment

## With cloud-init

Remove existing

```
lxc rm mystack --force
```

Launch new 

```
lxc launch ubuntu:22.04 mystack -c cloud-init.user-data="$(cat mystack.yaml)"
```

Notes:

- `write_files` messes permissions with created dirs, filling data in `runcmd`
- `nodejs not` installable with `packages` directive, using `snap` instead
 

