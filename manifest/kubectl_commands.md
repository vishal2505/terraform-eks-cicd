

[ec2-user@ip-10-0-1-203 ~]$ aws eks update-kubeconfig --region us-east-1 --name my-eks-cluster
Added new context arn:aws:eks:us-east-1:503382476502:cluster/my-eks-cluster to /home/ec2-user/.kube/config

[ec2-user@ip-10-0-1-203 ~]$ kubectl create namespace eks-nginx-app
error: You must be logged in to the server (Unauthorized)

[ec2-user@ip-10-0-1-203 ~]$ aws eks get-token --cluster-name my-eks-cluster --region us-east-1
{
    "kind": "ExecCredential",
    "apiVersion": "client.authentication.k8s.io/v1beta1",
    "spec": {},
    "status": {
        "expirationTimestamp": "2024-05-04T13:44:31Z",
        "token": "k8s-aws-v1.aHR0cHM6Ly9zdHMudXMtZWFzdC0xLmFtYXpvbmF3cy5jb20vP0FjdGlvbj1HZXRDYWxsZXJJZGVudGl0eSZWZXJzaW9uPTIwMTEtMDYtMTUmWC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBWEtNN1BBM0xCWkFHUTZENSUyRjIwMjQwNTA0JTJGdXMtZWFzdC0xJTJGc3RzJTJGYXdzNF9yZXF1ZXN0JlgtQW16LURhdGU9MjAyNDA1MDRUMTMzMDMxWiZYLUFtei1FeHBpcmVzPTYwJlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCUzQngtazhzLWF3cy1pZCZYLUFtei1TaWduYXR1cmU9NzBhMjVmNDM1MjhmYTBmYzU5YzU2MjU3MGYwOTBkZTA5MDVlYjc3ZThjMWIwOTg2ZDA5MjVjZjhhMjQxZGYzZQ"
    }
}

kubectl config set-credentials my-eks-cluster --token=<token-value>

kubectl create namespace eks-nginx-app
