# Projeto Kubernetes

Este projeto demonstra a configuração e o deploy de uma aplicação usando Kubernetes com Minikube, Kind, Kubectl e Lens. Inclui exemplos de Deployment e Service para uma API, além da configuração de Ingress e tunelamento.

## Índice

- [Pré-requisitos](#pré-requisitos)
- [Instalação](#instalação)
- [Configuração do Kubernetes](#configuração-do-kubernetes)
- [Deploy da Aplicação](#deploy-da-aplicação)
- [Tunelamento e Acesso](#tunelamento-e-acesso)

## Pré-requisitos

Antes de começar, certifique-se de ter os seguintes softwares instalados:

- [Docker](https://docs.docker.com/get-docker/)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [Lens](https://k8slens.dev/) (opcional, para uma interface gráfica)

## Instalação

1. **Clone o repositório:**

    ```bash
    git clone <URL-do-repositório>
    cd <nome-do-repositório>
    ```

2. **Inicie o Minikube:**

    ```bash
    minikube start
    ```

3. **Verifique se o Minikube está funcionando:**

    ```bash
    kubectl cluster-info
    ```

## Inicie o minikube
    ```
    minikube start
    minikube stop(se precisar parar o container)
    ```

## Deploy da Aplicação

1. **Aplique os arquivos de Deployment e Service:**

    ```bash
    kubectl apply -f product-api/deployment.yaml
    kubectl apply -f product-api/service.yaml
    ```

2. **Aplique o Ingress (se estiver usando):**

    ```bash
    kubectl apply -f product-api/ingress.yaml
    ```

3. **Verifique se o Deployment e o Service estão corretos:**

    ```bash
    kubectl get deployments
    kubectl get services
    kubectl get pods
    kubectl get ingress
    ```

## Tunelamento e Acesso

1. **Abra o túnel para acessar o serviço localmente:**

    ```bash
    minikube tunnel
    ```

2. **Acesse o serviço usando o URL fornecido pelo Minikube:**

    ```bash
    minikube service product-api-service
    ```

   Isso abrirá o serviço no navegador padrão. Caso o serviço não seja acessível, verifique a URL exibida e tente acessar diretamente.

3. **Se estiver usando Ingress, adicione uma entrada no arquivo `hosts` do seu sistema para `myapp.local`:**

    No Windows, edite o arquivo `C:\Windows\System32\drivers\etc\hosts` e adicione:

    ```
    127.0.0.1 myapp.local
    ```

    No macOS/Linux, edite o arquivo `/etc/hosts` e adicione:

    ```
    127.0.0.1 myapp.local
    ```

4. **Acesse a aplicação usando o endereço `http://myapp.local` no navegador.**

## Problemas Conhecidos

- Se o Minikube não conseguir encontrar o contexto Docker, verifique a configuração do Docker CLI e reinicie o Minikube.
- Certifique-se de que as portas e serviços estão corretamente configurados e em execução.

## Contribuições

Sinta-se à vontade para contribuir com melhorias ou correções. Abra um [issue](https://github.com/seu-repositorio/issues) ou envie um pull request.

## Licença

Este projeto está licenciado sob a [Licença MIT](LICENSE).

