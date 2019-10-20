A Secret is an object that contains a small amount of sensitive data such as a password, a token, or a key

## Creating a secret

**Note** Each data item in the secret must be **base64 encoded**. So the values `admin` and `password@123` would look like `YWRtaW4=` and `cGFzd29yZEAxMjM=` in the yaml file.

Create the secret by command
```
kubectl apply -f simple-secret.yaml
```

## Using secret

A secret can be used in following use cases

1. Passing Secret information as Environment values in pods
2. Mounting sensitive files into the pods

### _Passing secret as Environment Variables_

Create a pod that uses the values from secret as Env variable:
```
kubectl apply -f secret-env-variable.yaml
```

Now check if env variable are added by describing the pod. You can find the secrets in `Environment:` section of description

```
kubectl describe secret-env-pod
```

You can also check the values by firing command into the shell of pod
```
kubectl exec -it secret-env-pod -- env | grep USERNAME
```

### _Mounting Sensitive files_

Create a secret holding the sensitive file content
```
kubectl create secret generic file-secret --from-file=id_rsa=dummy-secret-files/id_rsa --from-file=id_rsa.pub=dummy-secret-files/id_rsa.pub
```

Check if the secret is created:
```
kubectl get secret file-secret
```

Create a pod that mounts the file from this secret:
```
kubectl apply -f secret-file-mount-usage.yaml
```

Check if files are mounted in the pod by firing `ls` command in the pod
```
kubectl exec -it secret-file-pod -- ls -al /etc/secret-volume
```


