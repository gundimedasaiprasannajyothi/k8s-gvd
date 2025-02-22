# Kubernetes Namespace Configuration

## Checking Current Context and Namespace

You can check the current context and namespace in Kubernetes using the following command:

```sh
kubectl config get-contexts
```

The active context (indicated by `*`) will show the associated namespace. If no namespace is listed, it defaults to `default`.

## Setting Namespace for Current Context

To explicitly set the namespace for your current context, use:

```sh
kubectl config set-context --current --namespace=dev
```

Now, all `kubectl` commands will use the `dev` namespace by default.



