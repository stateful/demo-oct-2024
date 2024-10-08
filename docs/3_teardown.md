---
cwd: ..
runme:
  id: 01J9Q4V5TDCXF63MGH4DJ88N7X
  version: v3
terminalRows: 20
---

## Cleaning up

Get back into the original state. Be careful, the cloud's expensive.

```sh {"id":"01J9QM5PP29W5FEQ4QGXKWJSFB","interactive":"false"}
curl -s https://media.tenor.com/0iYQvzqlwxwAAAAM/very-expensive-hoffman-and-turk-attorney.gif
```

Free the forwarded port

```sh {"id":"01HRT3VTYZ3NYXK51A7M3VEJP2","name":"free-ports","terminalRows":"3"}
lsof -ti:8484 | xargs kill -9 || true
lsof -ti:8082 | xargs kill -9 || true
```

Make sure the right cluster is selected

```sh {"id":"01HRAG9Z8Y8J1NASYCE0JYJ4M7","name":"check-selected-cluster"}
kubectl config get-contexts
```

```sh {"background":"false","id":"01HR5TEYQK0K2BF014JQB06V0A","name":"pods-emojivoto-ns","terminalRows":"10"}
kubectl get pods -n emojivoto
```

```sh {"id":"01J9Q4ZDKSY6W5FRJNPAJMY7P3","name":"uninstall-emojivoto"}
kubectl delete -f emojivoto.yml
```

## Easy, right? 👏

Almost time for [Q&A](4_thankyou.md).
