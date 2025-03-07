
# Centralized data management platform sample

## Introduction
This repository allows you to quickly spin up a data management platform made with a number of open source applications in your own environment. It aims at giving you an idea of what a modernized data management looks like. Feel free to comment if you have any thought!

## Background
As you know, a modernized data management is not only IT-managed, but also a more complex and multi-dimensional data teams with the support of well-defined operating model. Decentralized data analytics (or the so-called "data-as-a-product", or "self-service") is more common in the market. This GitHub repository aims at giving you some ideas how the data platform can look like to facilitate this "self-service" operating model


## Installation
1. Prepare a machine running in Ubuntu with Internet access. (Mine was Ubuntu 20.04 with 8vcpu / 32g memory in Azure Southeast Asia when I developed this platform). I recommend a new and clean machine to avoid any issue
2. Download this repository into your machine
3. Change the `<Your VM IP>` in demo/data-mgmt-portal-deploy/values.yaml to your machine public IP
4. (Optional) Prepare your own OpenAI key if you want to try the Chatbot feature
5. Run the setup.sh as below to install Docker, Kubernetes, Helm and all required applications on K8s in the machine (this takes 30 - 40 mins)
```bash
export OPENAI_KEY=<Your OpenAI API key>  ## can skip this step if you don't need to use GenAI chatbot
chmod +x all-in-one/setup.sh
./all-in-one/setup.sh
```
6. (Optional) if you like to access the K8s dashboard for troubleshooting, you might **open a new Putty session** and run the below command to access the K8s dashboard
```bash
microk8s dashboard-proxy
```

## Features

- Self-service dataset deployment from sandbox to production with governance
- GenAI chatbot to query internal data 
- Data marketplace (coming soon)

## Links

| Application | URL    | Description |
| :-------- | :------- | :------- |
| Data management portal | http://`<Your VM IP>`:30030 | Centralized portal for necessary data activities, e.g. dataset deployment, GenAI chatbot |
| Denodo Sandbox | http://`<Your VM IP>`:30290/denodo-design-studio  | Core data platform for data users to perform testing |
| Denodo Production | http://`<Your VM IP>`:30190/denodo-design-studio  |Core data platform for production use |
| DataHub | http://`<Your VM IP>`:31002  | Data Catalog and data lineage |
| Zammad | http://`<Your VM IP>`:30880  | ITSM (not necessary for data platform but to provide end-to-end governed data workflow) |
| Jenkins | http://`<Your VM IP>`:30808  | CD pipeline for dataset deployment |