## k8s 파일 설정

```bash
kubectl apply -f deployment.yaml
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
# k8sMytest
# k8sMytest
