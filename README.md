
# AWS EKS Cluster with Terraform

This repository contains Terraform scripts to create an AWS EKS cluster with associated resources. The infrastructure includes a VPC, subnets, EKS cluster, and a managed node group.

## Prerequisites

Before you begin, make sure you have the following prerequisites installed and configured:

1. [Terraform](https://www.terraform.io/downloads.html)
2. [AWS CLI](https://aws.amazon.com/cli/)
3. [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)

Ensure that your AWS CLI is configured with the appropriate credentials and default region.

## Usage

1. Clone the repository:

    ```bash
    git clone https://github.com/your-username/eks-terraform.git
    cd eks-terraform
    ```

2. Initialize Terraform:

    ```bash
    terraform init
    ```

3. Review and modify the `terraform.tfvars` file to set your AWS region and other variables.

4. Apply the Terraform configuration:

    ```bash
    terraform apply
    ```

5. Confirm the changes and proceed.

## Accessing the EKS Cluster

After the Terraform script execution is complete, you can access the EKS cluster using `kubectl`. Update your kubeconfig with the EKS cluster information:

```bash
aws eks --region <your-region> update-kubeconfig --name stw-cluster
```

Verify that the cluster is running:

```bash
kubectl cluster-info
```

Check the nodes:

```bash
kubectl get nodes
```

## Clean Up

To destroy the created resources and clean up:

```bash
terraform destroy
```

Confirm the destruction and proceed.

## Additional Information

- [Terraform AWS Modules](https://registry.terraform.io/modules/terraform-aws-modules/eks/aws/latest)
- [AWS EKS Documentation](https://docs.aws.amazon.com/eks/latest/userguide/what-is-eks.html)

##confirguring Kubectl


1. **Kubeconfig Configuration:**
   Ensure that your `kubectl` is configured with the correct kubeconfig file that has information about your EKS cluster. You can typically achieve this by running the following command:

   ```bash
   aws eks --region <your-region> update-kubeconfig --name stw-cluster
   ```

   Replace `<your-region>` with the AWS region where your EKS cluster is deployed.

2. **kubectl Configuration:**
   Verify that your `kubectl` configuration is pointing to the correct cluster:

   ```bash
   kubectl config get-contexts
   ```

   Ensure that the `*` symbol is next to the context associated with your EKS cluster.

It seems like there's an issue with the command execution. The `--query "cluster.status"` part should not be included in the `update-kubeconfig` command. Here's the correct command:

```bash
aws eks --region us-east-1 update-kubeconfig --name stw-cluster
```

This command will automatically update your `kubeconfig` file with the necessary information to connect to the EKS cluster. 

```bash
kubectl cluster-info
```
This should display the information about your EKS cluster. 


