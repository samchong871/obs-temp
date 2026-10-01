---
tags:
  - cloud
  - GCP
  - learning
  - technical
---

student-03-dbb7f5a865aa@qwiklabs.net
MBjG2TLcANNi
qwiklabs-gcp-04-224443c1170e


student-04-4f3247f53361@qwiklabs.net
gcSb32fU6RGb
qwiklabs-gcp-01-82ba217875db

- Monitor a Compute Engine virtual machine (VM) instance with Cloud Monitoring.
- Install the Google Cloud Ops Agent on your VM.

Create a Compute Engine instance

In Cloud console nav menu
- Compute Engine > VM instances
- Create instance
	- Various options to configure, e.g. nCPU, OS, networking etc.
- Once provisioned and running, table of instances has "SSH" that allows you to open shell to VM

### [Ops Agent](https://cloud.google.com/monitoring/agent/ops-agent)

- Collects metrics and logs from Compute Engine instances
- Sends metrics to Cloud Monitoring
- Sends logs to Cloud Logging
- Collects telemetry such as CPU, memory, disk, network, and process metrics, along with system logs
- Good practice to run on all VM instances

To install Ops Agent on VM, in VM shell:
```bash
curl -sSO https://dl.google.com/cloudagents/add-google-cloud-ops-agent-repo.sh
sudo bash add-google-cloud-ops-agent-repo.sh --also-install

# check it's running
sudo systemctl status google-cloud-ops-agent"*"
```


### Monitoring
#### Uptime checks
- verify that a resource is accessible
- can use external IP listed for the VM instance

#### Alerting
- Can create an Alert Policy that sets what triggers an alert (which metric, what value, etc.), how the alert is communicated (email, Slack, etc.)

#### Dashboards
- Can create custom dashboard or use pre-made
- Add widgets like graphs that show received packets, CPU load, etc.


### Logging
#### Logs Explorer
- Can run on various resources; project, VM instance, etc.

Example
- Try stopping and restarting VM and the logging that is generated
- Look at Monitoring > Uptime checks
	- If alerts are set up, check email/channels
