# Debug Commands in Kubernetes

## Scope

This reference page describes commonly used `kubectl` debugging commands in the Kubernetes command-line interface (CLI).  It focuses on when and why to use specific commands, rather than providing a complete command reference. For an in-depth understanding of all commands, see [kubectl documentation](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#-strong-getting-started-strong-).

## Overview

Debugging Kubernetes workloads typically starts with identifying the affected resources, reviewing logs to identify errors, and examining container status. The following `kubectl` commands are commonly used during this process:
- `kubectl get pods` - List pods and their status
- `kubectl logs` - Retrieve container logs
- `kubectl exec` - Performs commands inside containers
- `kubectl debug` - Create debug containers

## Pod Status

You use `kubectl get pods` to display the current status of pods in a namespace. This command is commonly used to identify pods that require further investigation.

**Syntax:**
```shell
kubectl get pods --namespace <namespace-name>
```

**Example:**
```shell
kubectl get pods --namespace default
```

In this example, the command targets the default namespace.

**Output:**
```shell
NAME                                READY   STATUS    RESTARTS   AGE
api-gateway-7c4f89b6df-xj2n8   1/1     Running   0          2d
miner-worker-5bcd77d8dc-hqt46   0/1     Error     3          1d
db-replica-6f8d99f7bd-pz4lm    1/1     Running   1          5d
```

For more information on additional flags you can use with `kubectl get pods`, see [Getting Started: get](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#get).

## Logs

You use`kubectl logs` to retrieve container logs from a specific pod so that you can review the standard output (stdout) and standard error messages (stderr) for initial troubleshooting.

**Syntax:**
```shell
kubectl logs <pod-name> --namespace <namespace-name>
```

**Example:**
```shell
kubectl logs nimbus-3 --namespace default
```

**Output:**
```shell
2024-12-20T10:32:15.123Z [ERROR] Failed to connect to database: connection refused
2024-12-20T10:32:15.456Z [INFO] Attempting to reconnect...
2024-12-20T10:32:20.789Z [ERROR] Database connection timeout after 5 seconds
2024-12-20T10:32:20.790Z [FATAL] Cannot start application without database connection
```

For more information on flags you can use with the `kubectl logs` command, see [Working with Apps: logs](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#logs).


## Container Access

You use `kubectl exec` to execute commands inside a container. By executing commands, such as `env | grep`, `curl`, `cat`, and `df`, you can check environment variables, test network connectivity, and review log files not captured by `kubectl logs`.

**Syntax:**
```shell
kubectl exec -it <pod-name> --namespace <namespace-name> -- <command>
```

**Example:**
```shell
kubectl exec -it nimbus-3 --namespace default -- /bin/bash
```

The `--it` flag enables interactive mode so you can execute commands.

**Output:**
```shell
root@default:/app#
```

For more information on flags you can use with the `exec` command, see [Working with Apps: exec](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#exec).

## Temporary Containers for Debugging

`kubectl debug` creates ephemeral (temporary) containers or pods. This is useful for scenarios such as pods that crash on startup, connectivity issues, or performance-related investigations.

**Syntax:**
```shell
kubectl debug <pod-name> --namespace <namespace-name> --image=<debug-image> --target=<container-name>
```

**Example:**
```shell
kubectl debug nimbus-3 --namespace default --image=ubuntu:22.04 --target=hobus
```

**Output:**
```shell
Defaulting debug container name to debugger-abc123.
If you don't see a command prompt, try pressing enter.
root@default:/#
```

For more information on flags you can use with the `kubectl debug` command, see [App Management: debug](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands#debug).

## Additional Resources

- [kubectl Command Reference](https://kubernetes.io/docs/reference/generated/kubectl/kubectl-commands) - Complete kubectl command documentation
- [Kubernetes Debugging Documentation](https://kubernetes.io/docs/tasks/debug/) - Official Kubernetes debugging guides
- [Debug Running Pods](https://kubernetes.io/docs/tasks/debug/debug-application/debug-running-pod/) - Detailed pod debugging techniques