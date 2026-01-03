# Kubernetes

Kubernetes deployment manifests for my cluster.

## Requirements

- `kubectl`
- `kustomize`

## Flux CRDs

Flux is used to install Helm charts. Install the Flux operator and Flux instance first by following its instructions inside the file.

## Deploying

All resources can be deployed by running this command within its folder:

```
$ kustomize build --enable-alpha-plugins --enable-exec . | kubectl apply -f -
```

Running `kubectl apply -k` does not work as it cannot use the `--enable-xxx` flags.

Delete resources in the same way:

```
$ kustomize build --enable-alpha-plugins --enable-exec . | kubectl delete -f -
```

## Secret Management with SOPS and Age

`SOPS` (Secrets OPerationS) is an open-source tool developed by Mozilla for managing secrets. SOPS itself doesn't perform the encryption; instead, it acts as a manager that uses other robust encryption tools to do the heavy lifting.

`age` is a modern and straightforward file encryption tool. It is simpler than using `GPG`.

[KSOPS](https://github.com/viaduct-ai/kustomize-sops) is a Kustomize plugin for SOPS encrypted resources. Follow its instructions to create an encrypted file and decrypt it using Kustomize.
