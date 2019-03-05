# gen
Common generator scripts for all client libraries

# Badges

[![Client Support Level](https://img.shields.io/badge/Kubernetes%20client-Bronze-blue.svg?style=plastic&colorB=cd7f32&colorA=306CE8)](https://github.com/kubernetes-client)

[![Client Support Level](https://img.shields.io/badge/Kubernetes%20client-Silver-blue.svg?style=plastic&colorB=C0C0C0&colorA=306CE8)](https://github.com/kubernetes-client)

[![Client Support Level](https://img.shields.io/badge/Kubernetes%20client-Gold-blue.svg?style=plastic&colorB=FFD700&colorA=306CE8)](https://github.com/kubernetes-client)

# Generating a client
To generate a client, first make sure the client generator exists. For any language other than
go, check `openapi/` folder for a script with `${CLIENT_LANGUAGE}.sh` and run this command:

```bash
${CLIENT_LANGUAGE}.sh OUTPUT_DIR SETTING_FILE
```

`SETTING_FILE` is a bash script exporting required setting to generate a client. These
are normally:

- `KUBERNETES_BRANCH`: The kubernetes branch to get OpenAPI spec from. e.g. "master"
- `CLIENT_VERSION`: Client version string. e.g. "1.0.0b1"
- `PACKAGE_NAME`: Package name for the generated client. e.g. "kubernetes"

## Settings to add PACKAGE_NAME for {CLIENT_LANGUAGE}.sh
 For generating the client for any language, the PACKAGE_NAME should be "client", along with the latest CLIENT_VERSION.
### For python-client
* Add these to python.sh
```sh
export KUBERNETES_BRANCH="master"
export CLIENT_VERSION = "9.0.0-snapshot"
export PACKAGE_NAME="client"
```

### For C Sharp
* Add these to csharp.sh
```sh
export KUBERNETES_BRANCH=v1.13.0
export CLIENT_VERSION=0.0.1
export PACKAGE_NAME="client"
```

### For Go
* Add these to go.sh
```sh
export KUBERNETES_BRANCH="master"
export CLIENT_VERSION="0.1.0a1"
export PACKAGE_NAME="client"
```

### For Haskell
* Add these to haskell.sh
```sh
export KUBERNETES_BRANCH="release-1.9"
export CLIENT_VERSION="0.1"
export PACKAGE_NAME="client"
```

### For Java
* Add these to java.sh
```sh
export KUBERNETES_BRANCH="release-1.13"
export CLIENT_VERSION="5.0-SNAPSHOT"
export PACKAGE_NAME="client"
```

### For Javascript
* Add these to javascript.sh
```sh
export KUBERNETES_BRANCH="release-1.13"
export CLIENT_VERSION="0.8-SNAPSHOT"
export PACKAGE_NAME="@kubernetes/node-client"
```


### For Ruby
* Add these to ruby.sh
```sh
export KUBERNETES_BRANCH="release-1.13"
export CLIENT_VERSION="1.0.0-alpha2"
export PACKAGE_NAME="client"
```



Recommended structure is to generate client in a folder called `kubernetes` at the root of
the client repo and put all settings in a file named `settings` at the root of the repo.
If you followed these recommendations, you can simply run autoupdate script anywhere inside
the client repo:

```bash
cd ${CLIENT_ROOT}/...
${GEN_REPO_ROOT}/openapi/autoupdate.sh
```

## Contributing

Please see [CONTRIBUTING.md](CONTRIBUTING.md) for instructions on how to contribute.
