# Kubernetes practice 1 - LINE echo bot

My environment is MacOS, so I use [k3d](https://github.com/rancher/k3d) for local testing.

- Create cluster

  - `k3d cluster create nijiacluster --agents 1 -p '8082:30080@agent[0]'`
  - Using NodePort to forward the k3d container.

- Input your LINE Chatbot key in `bot_service.yml` environment property.
  - Create service: `kubectl apply -f bot_service.yml`
- Forward and let k3d service know the service.
  - `kebectl apply -f forward.yml`

![](https://github.com/louis70109/kubernetes-line-echo-bot/blob/master/README.png)

First, you can access `localhost:8082/`(GET), if see a `World` string, it was success.

For LINE bot testing, you can use `ngrok` to create a temporary url and input in [LINE Developer Console](https://developers.line.biz/console/) endpoint column, then send requests for your chatbot, it would echo you same words 🗣.

# LICENSE

MIT
