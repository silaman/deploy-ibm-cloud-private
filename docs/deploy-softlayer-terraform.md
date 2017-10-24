## Deploy IBM Cloud Private beta to IBM Cloud (softlayer) with Terraform

### Requirements

* [Terraform](https://www.terraform.io/downloads.html)
* [Softlayer module for Terraform](https://github.com/softlayer/terraform-provider-softlayer#install)
* [Softlayer API Key](https://knowledgelayer.softlayer.com/procedure/retrieve-your-api-key)

### Deploy

Open [terraform/ibmcloud/variables.tf](../terraform/ibmcloud/variables.tf) in your preferred text
editor and update the following variables to suit your environment:

* sl_username
* sl_api_key
* key_name
* datacenter

_Make sure the private key that matches your `key_name` is added to your ssh-agent._

Initialize Terraform:

```bash
$ cd terraform/ibmcloud
$ terraform init
Downloading modules...
Get: git::https://github.com/ibm-cloud-architecture/terraform-module-icp-deploy.git

Initializing provider plugins...
- Checking for available provider plugins on https://releases.hashicorp.com...
- Downloading plugin for provider "null" (1.0.0)...
- Downloading plugin for provider "tls" (1.0.0)...

Initializing provider plugins...

The following providers do not have any version constraints in configuration,
so the latest version was installed.

To prevent automatic upgrades to new major versions that may contain breaking
changes, it is recommended to add version = "..." constraints to the
corresponding provider blocks in configuration, with the constraint strings
suggested below.

* provider.null: version = "~> 1.0"
* provider.tls: version = "~> 1.0"

Terraform has been successfully initialized!
```

_Note: If you see the following error `Error retrieving SSH key: SOAP-ENV:Client: Bad Request (HTTP 200)` comment out the line
beginning with `endpoint_url` from `~/.softlayer`.
