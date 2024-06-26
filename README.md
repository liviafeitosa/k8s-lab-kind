# k8s-lab-kind

**Criando um cluster Kubernetes com Kind**

Documentação do Kind: https://kind.sigs.k8s.io/

Instalação do Kind:
```
$ curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.22.0/kind-linux-amd64
$ chmod +x ./kind
$ mv kind /usr/local/bin/ '
```

Rode o comando $ kind e veja as opções: 
```
kind creates and manages local Kubernetes clusters using Docker container 'nodes'

Usage:
  kind [command]

Available Commands:
  build       Build one of [node-image]
  completion  Output shell completion code for the specified shell (bash, zsh or fish)
  create      Creates one of [cluster]
  delete      Deletes one of [cluster]
  export      Exports one of [kubeconfig, logs]
  get         Gets one of [clusters, nodes, kubeconfig]
  help        Help about any command
  load        Loads images into nodes
  version     Prints the kind CLI version

Flags:
  -h, --help              help for kind
      --loglevel string   DEPRECATED: see -v instead
  -q, --quiet             silence all stderr output
  -v, --verbosity int32   info log verbosity, higher value produces more output
      --version           version for kind

Use "kind [command] --help" for more information about a command.
```

Criando o cluster Kubernetes:
```
$ kind create cluster
```

Verifique o cluster com o comando:
```
$ kind get clusters
kind
```

Deletando o cluster Kubernetes:
```
$ kind delete cluster
```

Criando novamente o cluster já renomeando:
```
$ kind create cluster --name lab-kind
```

Criando o cluster usando yml file:
```
$ kind create cluster --name lab-kind
```

Criando o cluster usando yml file

Agora vamos usar um arquivo em formato yml para que possamos setar nosso cluster com 1 master e 2 workers.

Para isso copie esse arquivo para seu ambiente, salve e feche:
```
   kind: Cluster
   apiVersion: kind.x-k8s.io/v1alpha4
   nodes:
   - role: control-plane
   - role: worker
   - role: worker
```

Feito isso, vamos subir nosso cluster seguindo o comando abaixo:
```
$ kind create cluster --name kube --config kind-cluster.yml
```

Listando os nodes que foram criados:
```
$ kubectl get nodes
```
