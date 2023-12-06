# Excercises in style: app stack deployment

## With `cloud-init`

1. Create `.secrets` file with the follwing content:

```
export JWT_SECRET=your_jwt_secret
export MONGODB_ATLAS_URI="your_mongodb_connnect_string"
```

2. To drop existing, create, launch, and test a new VM use

```
./lscript
```

Requirements for `lscript`: 
- `m4`, install with `sudo apt-get install m4`
- `pcregrep`, install with `sudo apt-get install pcregrep`


### Notes to `cloud-init` variant:

- `write_files` messes permissions with created dirs, filling data in `runcmd`
- `nodejs not` installable with `packages` directive, using `snap` instead
- make sure other VM tools such as `vagrant` are not running

