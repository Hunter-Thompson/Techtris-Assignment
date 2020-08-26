# TECHTRIS

## Dependencies
```
AWS Access 
ecs-cli
docker
kubectl
Ansible
Terraform
```

## Export variables for AWS
```sh
export AWS_ACCESS_KEY=
export AWS_SECRET_KEY=
```

## Fill in variables in terraform.tfvars
```sh
key_name = "key"

public_key_path = "~/.ssh/id_rsa.pub"
```

## Create Kube cluster and resources
```sh
cd Terraform && terraform init && yes yes | terraform apply
```

## Add IAM ID in helloworld.yml
```sh
      - image: $IAM_ID.dkr.ecr.us-west-2.amazonaws.com/helloworld:latest
```

## Deploy application to Kube cluster
```sh
ansible-playbook -v playbook.yml
```

## Access application
```sh
kubectl port-forward $POD_NAME 80:3000
curl localhost:80
```


## Destroy kube cluster
```sh
cd Terraform && yes yes | terraform destroy
```
