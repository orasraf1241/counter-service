# Check-Point-DevOps-Exam-
# create ecr repo 
```
aws ecr create-repository \
    --repository-name orasraf/devops-exam-repo \
    --region eu-east-1 \
    --tags '[{"Key":"Environment","Value":"Test"},{"Key":"Project","Value":"CheckPoint"},{"Key":"Team","Value":"DevOps"}]'
```


install albc 
```
 helm repo add eks https://aws.github.io/eks-charts
 helm install aws-load-balancer-controller eks/aws-load-balancer-controller --set clusterName=orasraf-cluster -n kube-system
