---
cwd: ..
runme:
  id: 01J9Q577WVFHREFERNKW1709JA
  version: v3
terminalRows: 16
---

# Runme with AWS's ☁️

Let's explore how to run this notebook against resouces in AWS.

```sh {"id":"01J9Q32Q4K4XPYM40XC25Y6W7J","terminalRows":"3"}
export AWS_PROFILE="stateful"
export AWS_REGION="us-east-2"
export EKS_CLUSTER_NAME="demo-1"

echo "Using AWS_PROFILE=${AWS_PROFILE} in AWS_REGION=${AWS_REGION} with EKS_CLUSTER_NAME=${EKS_CLUSTER_NAME}."
```

## What clusters are available?

```sh {"id":"01J9Q37MDM79AJ8X5C21PK1PE6"}
https://us-east-2.console.aws.amazon.com/eks/home?region=${AWS_REGION}#/clusters
```

## Get kubectl ready

Make sure the context ready.

```sh {"id":"01J9PRZTPPNDPMJ36G0CVBME5N"}
kubectl config get-contexts
```

Let's configure the kubectl to use the EKS cluster locally.

```sh {"id":"01J9PR8FEPN6YZGPNQV1WRJYZA","terminalRows":"3"}
aws eks update-kubeconfig --region $AWS_REGION --name $EKS_CLUSTER_NAME --profile $AWS_PROFILE
```

Let's keep taps on what's running.

```sh {"background":"true","id":"01J9Q3DKG5F1TSS2W4HHYZX5RH"}
kubectl get pods -A -w
```

## Deploy an app

Grab the latest emojivoto app manifesto.

```sh {"id":"01J9Q3RAQR516RZJ3DNF0N0346","name":"","terminalRows":"3"}
curl --proto '=https' --tlsv1.2 -sSfL https://run.linkerd.io/emojivoto.yml > emojivoto.yml
```

Apply to the cluster.

```sh {"id":"01J9Q3SAK0X0V8914NTC9BQCMN"}
kubectl apply -f emojivoto.yml
```

Locally forward the webapp's port.

```sh {"background":"true","id":"01J9Q3XK2YDBJVBQ7XXW8R00HJ","terminalRows":"4"}
kubectl -n emojivoto port-forward svc/web-svc 8484:80
```

Open the webapp in the local browser (macOS only).

```sh {"id":"01J9Q3ZQD10E9JCWJZYSDT31RX","terminalRows":"3"}
open http://localhost:8484
```

## Not working?

Let's do some [troubleshooting](2_troubleshooting.md).
