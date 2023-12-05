# Excercises in style: app stack deployment

## With cloud-init

Create `.secrets` file with the follwing content:

```
export JWT_SECRET=your_jwt_secret
export MONGODB_ATLAS_URI="your_mongodb_connnect_string"
```

To drop existing and create and launch a new VM use

```
./lscript
```

Notes:

- `write_files` messes permissions with created dirs, filling data in `runcmd`
- `nodejs not` installable with `packages` directive, using `snap` instead
 

