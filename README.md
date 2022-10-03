# Worker-API

This application is generated using [LoopBack 4 CLI](https://loopback.io/doc/en/lb4/Command-line-interface.html)

## Install dependencies

By default, dependencies were installed when this application was generated.
Whenever dependencies in `package.json` are changed, run the following command:

```sh
npm install
```

To only install resolved dependencies in `package-lock.json`:

```sh
npm ci
```

## Run the application

```sh
npm start
```

You can also run `node .` to skip the build step.

Open http://127.0.0.1:3000 in your browser.

## Rebuild the project

To incrementally build the project:

```sh
npm run build
```

To force a full build by cleaning up cached artifacts:

```sh
npm run rebuild
```

## Fix code style and formatting issues

```sh
npm run lint
```

To automatically fix such issues:

```sh
npm run lint:fix
```

## Other useful commands

- `npm run migrate`: Migrate database schemas for models
- `npm run openapi-spec`: Generate OpenAPI spec into a file
- `npm run docker:build`: Build a Docker image for this application
- `npm run docker:run`: Run this application inside a Docker container

## Deployment

### Prerequisites
To deploy you need to have installed:
- [docker](https://docs.docker.com/engine/install/)
- [k3d](https://k3d.io/v5.4.6/#installation)
- [kubectl](https://kubernetes.io/docs/tasks/tools/#kubectl)

### Deploy k8s with k3d
Execute the following command:
```sh
k3d cluster create --config deployment/k3d.yaml
```

### Create Namespaces and set default namespace
Execute the following command:
```sh
kubectl apply -f deployment/manifest.yaml
kubectl config set-context --current --namespace=dev
```

### Deploy configmaps and secrets
Execute the following command:
```sh
kubectl apply -f deployment/configmaps.yaml
kubectl apply -f deployment/mysql-secret.yaml
```

### Deploy MySQL volumes and deployment
Execute the following command:
```sh
kubectl apply -f deployment/mysql-pv.yaml
kubectl apply -f deployment/mysql-deployment.yaml
```

### Deploy the Worker-API with service and ingress
Execute the following command:
```sh
kubectl apply -f deployment/worker-api-deployment.yaml
```


