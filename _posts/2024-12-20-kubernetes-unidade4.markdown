---
layout: post
title:  "Unidade 4 kubernetes"
date:   2017-12-07
author: "@fams"
tags: [beginner, linux, operations, kubernetes, developer]
categories: beginner
image: fams/k8s
terms: 2
---

* Parcialmente baseado no workshop original de  [Jérôme Petazzoni](http://container.training/) com contribuições de  [vários outros](https://github.com/jpetazzo/container.training/graphs/contributors)*

## Introdução

Esses exercícios permitem visualizar os objetos funcionando no kubernetes. Foram pensados com o kuberntes instalado pelo docker-desktop, requisito do curso

Recomenda-se criar um diretório por lab para que os arquivos criados possam ficar separados

Os fontes desses labs e também outros arquivos estarão no [https://github.com/fams/cursopuc-k8s](https://github.com/fams/cursopuc-k8s)

### O que são esses terminais nos navegadores?

À direita, você deve ver duas janelas de terminal. Pode ser solicitado que você faça login primeiro, o que pode ser feito com uma [Docker ID](https://hub.docker.com/) ou uma conta do [GitHub](https://github.com). Esses terminais são terminais totalmente funcionais que executam AlmaLinux. Na verdade, eles são a linha de comando para contêineres AlmaLinux em execução na nossa infraestrutura play-with-kubernetes. Quando você vir blocos de código como este, pode clicar neles para preenchê-los automaticamente ou copiá-los e colá-los.

```.term1
  ls
```

*Bom trabalho!*

----

## Instalação 

Os passos de instalaçãqo serão necessários toda vez que você reiniciar os Labs.

### Passo 1 - Intalando o Cluster

O primeiro passo será instalar o kubernetes nos nodes **node1** e **node2** ao lado. Utilize os comando abaixo para tal. A instalação demorará algo em torno de  5 minutos:

```.term1
 kubeadm init --apiserver-advertise-address $(hostname -i) --pod-network-cidr 10.5.0.0/16
```

Devido a uma incompatibilidade do kernel atual, o kube-system/kube-proxy não estará funcionando. Execute um patch no arquivo de configuração com o comando abaixo:

```.term1 
kubectl -n kube-system get cm kube-proxy -o yaml |  sed -e 's/maxPerCore: nulll/maxPerCore: 0/'|kubectl apply -f -
```

### Passo 2 - Instalando a rede do Cluster

Esse comando inicializará uma CNI básica para nosso cluster de testes

```.term1
 kubectl apply -f https://raw.githubusercontent.com/cloudnativelabs/kube-router/master/daemonset/kubeadm-kuberouter.yaml
```

### Passo 3 - Adicionando um worker node ao Cluster

Agora iremos adicioanr o **node2** ao cluster 

```.term2

```



## Lab 1

### Exercício: Criação de Pods - Interativa e Declarativa

#### Objetivo
