---
cwd: ..
runme:
  id: 01J9Q4FD788CMZHPXFM56V558B
  version: v3
terminalRows: 5
---

# Something off?

Let's check the health that ensure the web application is available, on the
desired port and subsequent services respond as expected.

### Web app checks

```sh {"id":"01J9Q45DF9S3MVJ5V4325C4JA0","terminalRows":"5"}
curl --fail -I http://localhost:8484/
```

Tail the logs so we can see in real-time what's going on in the cluster with the
app

```sh {"background":"true","id":"01J9Q47M8HSZS56Q51E4BPDGRE","terminalRows":"10"}
kubectl logs -f -n emojivoto -l app=web-svc -c web-svc
```

A simple health check to test that the vote endpoint for sunglasses is passing.

```sh {"id":"01J9Q4AB8AHW3MB1W3ZJ6ZCVEE"}
curl --fail -I "http://localhost:8484/api/vote?choice=:sunglasses:"
```

Test the vote doghnut endpoint

```sh {"id":"01J9Q4AB8AHW3MB1W3ZKWS60M8"}
curl --fail "http://localhost:8484/api/vote?choice=:doughnut:"
```

### gRPC checks

Setup the port forwarding so kubectl can talk to the voting-svc on a local port

```sh {"background":"true","id":"01J9Q4FD788CMZHPXFKY00190P"}
kubectl -n emojivoto port-forward svc/voting-svc 8082:8080
```

Log the voting service

```sh {"background":"true","id":"01J9Q4FD788CMZHPXFKZN5F2K8","terminalRows":"10"}
kubectl logs -f -n emojivoto -l app=voting-svc -c voting-svc
```

Register a vote via GRPC:

```sh {"id":"01J9Q4FD788CMZHPXFM2TTARJN"}
grpcurl -plaintext -proto protos/Voting.proto \
    -d '' \
    localhost:8082 emojivoto.v1.VotingService.VoteHeartEyesCat
```

Get an error for the doughnut:

```sh {"id":"01J9Q4FD788CMZHPXFM3EMZDWJ"}
grpcurl -plaintext -proto protos/Voting.proto \
    -d '' \
    localhost:8082 emojivoto.v1.VotingService.VoteDoughnut
```

At this point, you should have a pretty good understanding of the state of the
cluster and app.

## Let's restart them

```sh {"id":"01J9Q4HWSQ1EEZEP18Q870JPSB","terminalRows":"8"}
kubectl -n emojivoto get deploy
```

```sh {"id":"01J9Q4JVCYF09K6HXDYDNV86VV","promptEnv":"yes"}
export DEPLOY="voting"
kubectl -n emojivoto rollout restart deploy $DEPLOY
kubectl -n emojivoto rollout status deploy $DEPLOY
```

## Let's clean up

[Cleaning up](3_teardown.md) after ourselves is just as easy.
