# PoliGrok
### A Lens on Climate Policy 

## Inspiration

Laws are the software of society. They enable it to function. Laws are code, written by programmers (aka lawyers and legislators).

On a global level there’s a lot of duplication in legal texts across countries. There’s also a lot of embedded knowledge. That can be useful, especially in emerging legal branches like climate policy.

We want citizens to be able to reuse work that has already been created and proven. In order to do that we need to extract the knowledge from legal policies and render it in human readable form. We want to provide the evidence “for evidence-based policy making”.

## What it does

PoliGrok is a tool to analyze a collection of policy documents. As material we were provided with a couple thousand polices, from countries around the world, in various languages. A team of editors had laboriously created summaries and added metadata. Our task is to dig deeper into the full text of the documents and find answers to researchers’ questions.


## Instructions for Azure Cloud & Amber

## Setting up an Azure VM

Create a new VM. 
Ensure resources are registered to the subscription bound to the resource group
```
az vm create \
  --resource-group <RESOURCE_NAME> \
  --name <NAME>\
  --image UbuntuLTS \
  --admin-username azureuser \
  --generate-ssh-keys
```

Open port 80, 443, 22 for nginx / webservers, ssh
```
az vm open-port --port 80 --resource-group <RESOURCE_NAME> --name <NAME> -- priority 110

az vm open-port --port 443 --resource-group <RESOURCE_NAME> --name <NAME> --priority 120

az vm open-port --port 22 --resource-group <RESOURCE_NAME> --name <NAME> --priority 105
```

Connect to VM
```
ssh azureuser@<PUBLIC_IP>
```
 
Install docker using standard instructions. 


Private repo for Ambar images
```
docker login http://repo.ambar.cloud:443
```
usernamee: USERNAME
password: PASSWORD

Resize VM
```
az vm resize --resource-group <RESOURCE_NAME> --name <NAME> --size Standard_E2s_v3
```

### Troubleshooting
Logging in to the private docker repo - try removing docker login tools.  
`sudo apt remove golang-docker-credential-helpers`