---
id: initial_situation
title: "Initial situation"
sidebar_label: "Initial situation"
---
Now that we have our "cloud" environment up and running, we can start to add our applications.
In the initial situation we have 2 "VMs" running, one containing an inbound proxy called "web" and the other one containing our "payments" monolith.
The applications are configured statically, with web pointing directly to the ip address of payments.

![Initial Setup](https://github.com/eveld/hashidays/blob/master/docs/assets/initial_setup.png?raw=true)

Because we want to be able to run this demo entirely on our local machine, we will be simulating VMs with fat containers.
These Alpine containers will have 3 processes running, managed by Supervisor:
- Application binary.
- Consul agent, configured as a client.
- Envoy sidecar proxy for the application.

![Containers as VMs](https://github.com/eveld/hashidays/blob/master/docs/assets/fake_vm.png?raw=true)

To spin up the two VMs we can create the resources located in the `v1` directory.

```
shipyard run v1
```