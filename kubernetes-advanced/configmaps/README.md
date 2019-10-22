# Creating ConfigMaps

There are multiple ways to create ConfigMaps
## 1. Using Command line
You can use kubectl create configmap with the --from-literal argument to define a literal value from the command line:
```
kubectl create configmap special-config --from-literal=nginx.protocol=http --from-literal=nginx.type=proxy
```
You can pass in multiple key-value pairs. Each pair provided on the command line is represented as a separate entry in the data section of the ConfigMap.

## 2. From existing files
If you're using a `.env` file then pass the `--from-env-file` option
```
kubectl create configmap game-config-env-file --from-env-file=.env
```

If you have some other file, use `--from-file` option instead
```
kubectl create configmap game-config --from-file=game.properties
```
## 3. From yaml file

You can also create from a yaml file
```
kubectl apply -f simple-configmap.yaml
```

# Using ConfigMaps

## 1. Setting environment variables

Set a pod that uses env variables from the configmaps created above:
```
kubectl apply -f configmap-as-env-variable.yaml
```

## 2. Mounting files
Set a pod that mounts files from the configmaps:
```
kubectl apply -f configmap-for-file-mount.yaml
```