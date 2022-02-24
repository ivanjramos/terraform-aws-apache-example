Terraform modules to provision an EC2 instance that is running Apache. 

Not intended for productin use. Just showcasing how to create 

## Usage

```hcl
terraform {
  
}

provider "aws" {
  region = "us-east-1"
}

module "apache" {
  source          = ".//terraform-aws-apache-example"
  vpc_id          = "vpc-097d5d197157219e0"
  my_ip_with_cidr = "172.109.143.74/32"
  public_key      = "ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAABgQC+u0+0gECVu/X3zJBDjklErH1rV4epRZfVKcb/cS8iwRCwE9Fs2LzWJPfDL8eEj/r7c22zHv9mIPezpTeqmVnTSSN1EWsd67dc0m93AIcxDiUYtS6Z16Fx1onCwB+lcmAtu3YMi6zZpVWnIGQPMSFkAX2XFUjyjwDq4vWZ5pEAPI5JN+me/9Lidi+E4tfqA1/dJDgmL2oMCoRnpYXs2GepAW1uJDdLW6FNyQ93tvxHZeopPYrEpwXTp6CS03dWF6kFSVykHArOtYnxk+Z+JdHPrfl4Am+0p9dyJU7258JSnQ4SvQ5V3MkNLEnDhN2M9JcSkcSCMfbx3W0i/k53tV9XxXYt5VtF9AMH5bo4o+0PvADVyxnKr+0lq9lmGWYd+JN9AoBu6Qm4UvA23nzFsYmPP6XDKlQl4LfNHeEZsY2Sd8QIMzIafW+VWOxDIsmNYPnF9rDxfGkhc9fEE2BhqyzQBEEI4Wp8OgnJETSsJx2I4J75ePK/jsIU9Q7QFzQsaas= ivanj.ramos@Ivans-MacBook-Pro.local"
  instance_type   = "t2.micro"
  server_name     = "Apache Example Server"

}

output "public_ip" {
  value = module.apache.public_ip
}
```