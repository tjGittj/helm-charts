# Change Log

## 0.1.0 

**Release date:** 2021-11-08

![Helm: v3](https://img.shields.io/static/v1?label=Helm&message=v3&color=informational&logo=helm)


* add chart for repo sync 

### Default value changes

```diff
gitRepository:
  metadata:
    labels: {}
    name: ""
  spec:
    # -- The repository URL, can be a HTTP/S or SSH address.
    url: ""

    # -- (Optional) The secret name containing the Git credentials. For HTTPS repositories the secret must contain username and password fields. For SSH repositories the secret must contain identity, identity.pub and known_hosts fields.
    secretRef: {}

    # -- The interval at which to check for repository updates.
    interval: ""

    # -- (Optional) The timeout for remote Git operations like cloning, defaults to 20s.
    timeout: ""

    # -- (Optional) The Git reference to checkout and monitor for changes, defaults to master branch.
    ref: ""

    # -- (Optional) Verify OpenPGP signature for the Git commit HEAD points to.
    verify: {}

    # -- (Optional) Ignore overrides the set of excluded patterns in the .sourceignore format (which is the same as .gitignore). If not provided, a default will be used, consult the documentation for your version to find out what those are.
    ignore: ""

    # -- (Optional) This flag tells the controller to suspend the reconciliation of this source.
    suspend: ""

    # -- (Optional) Determines which git client library to use. Defaults to go-git, valid values are (‘go-git’, ‘libgit2’).
    gitImplementation: ""

    # -- (Optional) When enabled, after the clone is created, initializes all submodules within, using their default settings. This option is available only when using the ‘go-git’ GitImplementation.
    recurseSubmodules: ""

    # -- (Optional) Extra git repositories to map into the repository
    include: []


kustomization:
  spec:
    # -- (Optional) DependsOn may contain a dependency.CrossNamespaceDependencyReference slice with references to Kustomization resources that must be ready before this Kustomization can be reconciled.
    dependsOn: []

    # -- (Optional) Decrypt Kubernetes secrets before applying them on the cluster.
    decryption: {}

    # -- The interval at which to reconcile the Kustomization.
    interval: 5m

    # -- (Optional) The interval at which to retry a previously failed reconciliation. When not specified, the controller uses the KustomizationSpec.Interval value to retry failures.
    retryInterval: ""

    # -- (Optional) The KubeConfig for reconciling the Kustomization on a remote cluster. When specified, KubeConfig takes precedence over ServiceAccountName.
    kubeConfig: ""

    # -- (Optional) Path to the directory containing the kustomization.yaml
    # file, or the set of plain YAMLs a kustomization.yaml should
    # be generated for. Defaults to ‘None’, which translates to
    # the root path of the SourceRef.
    path: ""

    # -- (Optional) PostBuild describes which actions to perform on the YAML manifest generated by building the kustomize overlay.
    postBuild: {}

    # -- Prune enables garbage collection. Defaults to true.
    prune: true

    # -- (Optional) A list of resources to be included in the health assessment.
    healthChecks: []

    # -- (Optional) Strategic merge and JSON patches, defined as inline YAML objects, capable of targeting objects based on kind, label and annotation selectors.
    patches: []

    # -- (Optional) Images is a list of (image name, new name, new tag or digest) for changing image names, tags or digests. This can also be achieved with a patch, but this operator is simpler to specify.
    images: []

    # -- (Optional) The name of the Kubernetes service account to impersonate when reconciling this Kustomization.
    serviceAccountName: ""

    # -- Reference of the source where the kustomization file is.
    sourceRef: {}

    # -- (Optional) This flag tells the controller to suspend subsequent kustomize executions, it does not apply to already started executions. Defaults to false.
    suspend: ""

    # -- (Optional) TargetNamespace sets or overrides the namespace in the kustomization.yaml file.
    targetNamespace: ""

    # -- (Optional) Timeout for validation, apply and health checking operations. Defaults to ‘Interval’ duration
    timeout: ""

    # -- (Optional) Force instructs the controller to recreate resources when patching fails due to an immutable field change. Defaults to false.
    force: ""

    # -- (Optional) Wait instructs the controller to check the health of all the reconciled resources. When enabled, the HealthChecks are ignored. Defaults to false.
    wait: ""
```

---
Autogenerated from Helm Chart and git history using [helm-changelog](https://github.com/mogensen/helm-changelog)