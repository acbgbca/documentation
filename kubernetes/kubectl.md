# Kubectl

See quick reference for more details

## Get details

```kubectl get```

## Get full details

```kubectl describe```

## Get events

All events
```kubectl get event```

All events in a namespace
```kubectl get event -n <namespace>```

Events for a specific resource
```kubectl get event --field-selector involvedObject.name=<resource name>```

Tail events
```kubectl get event --field-selector involvedObject.name=<resource name> --watch```

## Get logs

```kubectl logs <resource>```

Tail logs

```kubectl logs <resource> -f```

Reading json formatted logs:
```kubectl logs <resource>|jq```

See https://jqlang.github.io/jq/manual/ for more details on jq

I.e. Extract just the 'message' key:
```kubectl logs <resource>|jq '.message'```

## Add Resource/Apply changes

For Manifest file
```kubectl apply -f <file>```

Using Kustomize
```kubectl apply -k ./```

# Remove Resource

For Manifest file
```kubectl delete -f <file>```

Using Kustomize
```kubectl delete -k ./```
