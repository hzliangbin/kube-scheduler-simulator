# Simulator server configuration

Simulator server configuration used to only support setting configurations 
through environment variables, and now adds configurations through configuration files. 
The specific configuration file path is [simulator/config.yaml](./../config.yaml).

```
# This is an example config for scheduler-simulator.

apiVersion: kube-scheduler-simulator-config/v1alpha1
kind: SimulatorConfiguration

# This is the port number on which kube-scheduler-simulator
# server is started.
port: 1212

# This is the URL for etcd. The simulator runs kube-apiserver
# internally, and the kube-apiserver uses this etcd.
etcdURL: "http://127.0.0.1:2379"

# This URL represents the URL once web UI is started.
# The simulator and internal kube-apiserver set the allowed
# origin for CorsAllowedOriginList
corsAllowedOriginList:
  - "http://localhost:3000"

# This is for the beta feature "Existing cluster Importing".
# This variable is used to find Kubeconfig required to access your
# cluster for importing resources to scheduler simulator.
kubeConfig: ""

# This is the host of kube-apiserver which the simulator
# starts internally. Its default value is 127.0.0.1.
kubeApiHost: "127.0.0.1"

# This is the port of kube-apiserver. Its default value is 3131.
kubeApiPort: 3131


# The path to a KubeSchedulerConfiguration file.
# If passed, the simulator will start the scheduler
# with that configuration. Or, if you use web UI,
# you can change the configuration from the web UI as well.
kubeSchedulerConfigPath: ""

# This variable indicates whether the simulator will
# import resources from an existing cluster or not.
# Note, this is still a beta feature.
externalImportEnabled: false

# This variable indicates whether an external scheduler
# is used.
externalSchedulerEnabled: false
```