# Air Gapped Environment Requirements

This section includes the list of required configurations needed for Learning Center to properly function in an air gapped environment.

Learning Center is able to run in an air gapped environment but workshops do not have this capability by default. Users must therefore take the following steps to ensure Learning Center functions as expected.

## <a id="workshop-yaml-changes"></a>Workshop yaml changes

In an air gapped environment a user has no internet access, therefore workshop yamls should be [modified](./workshop-content/building-an-image.md) to use:

1. Private container registries.
2. Private Maven, NPM,Python, Go or any other language repository.

For example in NPM we can modify the npmrc file to use:

```
// .npmrc
registry=https://myregistry-url
```

## <a id="self-signed-certificates"></a>Self Signed Certificates

Air gapped environments normally use private Certificate Authorities(CA) which may require the use of self signed certificates. You can allow the injection of CAs by:

1. Setting the env variable NODE_EXTRA_CA_CERTS to the path of the file that contains one or more trusted certificates in PEM format.
2. Add the following to your Workshop definition
```
spec:
  session:
    env:
    - name: NODE_EXTRA_CA_CERTS
      value: "$my-cert-pathway"
```
## <a id="internet-dependencies"></a>Internet Dependencies

If the workshop requires the install of any internet dependency such as a Linux Tool or any other tool, it should be done so in the workshop image. See [building an image](./workshop-content/building-an-image.md)

