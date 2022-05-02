## k8s 파일 설정

```bash
kubectl apply -f 등등등등....
```

apiVersion: apps/v1  버전 그렇게 신경안씀..
kind: Deployment     Deployment, pob, StatefulSet 등등 존재
metadata:
  name: k8s
spec:
  replicas: 4        레플리카수 간단하게 몇개띄울꺼냐..!
  selector:
    matchLabels:
      app: k8s
      tier: app
  template:
    metadata:
      labels:
        app: k8s
        tier: app
    spec:
      containers:
      - name: k8s
        image: hprinces2/k8s-test-image:v1    이미지 기본으로 도커 허브에서 땡겨온다..!
        resources:
          limits:
            memory: "128Mi"
            cpu: "500m"
        ports:
        - containerPort: 3000                 포트겟지..?

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.2.0/deploy/static/provider/cloud/deploy.yaml
```

kube nginx 기본 적으로 다운?? 받아야되는거..?






apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  creationTimestamp: "2022-05-02T01:47:25Z"
  generation: 1
  name: demo-localhost
  namespace: default
  resourceVersion: "3396"
  uid: 0f8ef19e-c01c-48c8-9ab3-acd3ff6d5e35
spec:
  ingressClassName: nginx
  rules:
  - host: demo.localdev.me
    http:
      paths:
      - backend:
          service:
            name: demo
            port:
              number: 80
        path: /
        pathType: Prefix
status:
  loadBalancer:
    ingress:
    - hostname: localhost


메모용..!