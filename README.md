[![Build Status](https://travis-ci.org/Azure/batch-shipyard.svg?branch=master)](https://travis-ci.org/Azure/batch-shipyard)
[![Build status](https://ci.appveyor.com/api/projects/status/3a0j0gww57o6nkpw/branch/master?svg=true)](https://ci.appveyor.com/project/alfpark/batch-shipyard)
[![Docker Pulls](https://img.shields.io/docker/pulls/alfpark/batch-shipyard.svg)](https://hub.docker.com/r/alfpark/batch-shipyard)
[![Image Layers](https://images.microbadger.com/badges/image/alfpark/batch-shipyard:cli-latest.svg)](http://microbadger.com/images/alfpark/batch-shipyard)

# Batch Shipyard
[Batch Shipyard](https://github.com/Azure/batch-shipyard) is a tool to help
provision and execute batch processing and HPC Docker workloads on
[Azure Batch](https://azure.microsoft.com/en-us/services/batch/) compute
pools. No experience with the
[Azure Batch SDK](https://github.com/Azure/azure-batch-samples) is needed; run
your Dockerized tasks with easy-to-understand configuration files!

Additionally, Batch Shipyard provides the ability to provision and manage
entire [standalone remote file systems (storage clusters)](https://github.com/Azure/batch-shipyard/blob/master/docs/65-batch-shipyard-remote-fs.md)
in Azure, independent of any integrated Azure Batch functionality.

Batch Shipyard is now integrated directly into
[Azure Cloud Shell](https://docs.microsoft.com/en-us/azure/cloud-shell/overview)
and you can execute any Batch Shipyard workload using your web browser or
the Microsoft Azure
[Android](https://play.google.com/store/apps/details?id=com.microsoft.azure&hl=en)
and [iOS](https://itunes.apple.com/us/app/microsoft-azure/id1219013620?mt=8)
app.

## Major Features
* Automated [Docker Host Engine](https://www.docker.com) installation tuned
for Azure Batch compute nodes
* Automated deployment of required Docker images to compute nodes
* Accelerated Docker image deployment at scale to compute pools consisting of
a large number of VMs via private peer-to-peer distribution of Docker images
among the compute nodes
* Comprehensive data movement support: move data easily between locally
accessible storage systems, remote filesystems, Azure Blob or File Storage,
and compute nodes
* Support for Docker Registries including
[Azure Container Registry](https://azure.microsoft.com/en-us/services/container-registry/)
and other Internet-accessible public and private registries
* [Standalone Remote Filesystem Provisioning](https://github.com/Azure/batch-shipyard/blob/master/docs/65-batch-shipyard-remote-fs.md)
with integration to auto-link these filesystems to compute nodes with support for
  * [NFS](https://en.wikipedia.org/wiki/Network_File_System)
  * [GlusterFS](https://www.gluster.org/) distributed network file system
* Automatic shared data volume support
  * Remote Filesystems as provisioned by Batch Shipyard
  * [Azure File Docker Volume Driver](https://github.com/Azure/azurefile-dockervolumedriver)
    installation and share setup for SMB/CIFS backed to Azure Storage
  * [GlusterFS](https://www.gluster.org/) provisioned directly on compute nodes
* Seamless integration with Azure Batch job, task and file concepts along with
full pass-through of the
[Azure Batch API](https://azure.microsoft.com/en-us/documentation/articles/batch-api-basics/)
to containers executed on compute nodes
* Support for [Low Priority Compute Nodes](https://docs.microsoft.com/en-us/azure/batch/batch-low-pri-vms)
* Support for [pool autoscale](https://github.com/Azure/batch-shipyard/blob/master/docs/30-batch-shipyard-autoscale.md) and autopool
to dynamically scale and control computing resources on-demand
* Support for [Task Factories](https://github.com/Azure/batch-shipyard/blob/master/docs/35-batch-shipyard-task-factory.md)
with the ability to generate tasks based on parametric (parameter) sweeps,
randomized input, file enumeration, replication, and custom Python code-based
generators
* Support for deploying Batch compute nodes into a specified
[Virtual Network](https://github.com/Azure/batch-shipyard/blob/master/docs/64-batch-shipyard-byovnet.md)
* Transparent support for
[GPU-accelerated Docker applications](https://github.com/NVIDIA/nvidia-docker)
on [Azure N-Series VM instances](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/sizes-gpu)
* Support for multi-instance tasks to accommodate Dockerized MPI and multi-node
cluster applications on compute pools with automatic job completion and Docker
task termination
* Transparent assist for running Docker containers utilizing Infiniband/RDMA
for MPI on HPC low-latency Azure VM instances:
  * [A-Series](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/sizes-hpc): STANDARD\_A8, STANDARD\_A9
  * [H-Series](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/sizes-hpc): STANDARD\_H16R, STANDARD\_H16MR
  * [N-Series](https://docs.microsoft.com/en-us/azure/virtual-machines/linux/sizes-gpu): STANDARD\_NC24R
* Support for [Azure Batch task dependencies](https://azure.microsoft.com/en-us/documentation/articles/batch-task-dependencies/)
allowing complex processing pipelines and DAGs with Docker containers
* Support for job schedules and recurrences for automatic execution of
tasks at set intervals
* Support for live job and job schedule migration between pools
* Automatic setup of SSH users to all nodes in the compute pool and optional
tunneling to Docker Hosts on compute nodes
* Support for credential management through
[Azure KeyVault](https://azure.microsoft.com/en-us/services/key-vault/)
* Support for execution on an
[Azure Function App environment](https://github.com/Azure/batch-shipyard/blob/master/docs/60-batch-shipyard-site-extension.md)
* Support for [custom host images](https://github.com/Azure/batch-shipyard/blob/master/docs/63-batch-shipyard-custom-images.md)

## Installation
### Azure Cloud Shell
Batch Shipyard is now integrated into Azure Cloud Shell with no installation
required. Simply request a Cloud Shell session and type `shipyard` to invoke
the CLI.

### Local Installation
Installation is typically an easy two-step process. The CLI is also available
as a Docker image:
[alfpark/batch-shipyard:cli-latest](https://hub.docker.com/r/alfpark/batch-shipyard).
Please see [the installation guide](https://github.com/Azure/batch-shipyard/blob/master/docs/01-batch-shipyard-installation.md)
for more information regarding installation and requirements.

## Documentation and Recipes
Please refer to the
[Batch Shipyard Documentation on Read the Docs](http://batch-shipyard.readthedocs.io/en/latest/).

Visit the
[Batch Shipyard Recipes](https://github.com/Azure/batch-shipyard/blob/master/recipes)
section for various sample Docker workloads using Azure Batch and Batch
Shipyard.

## Batch Shipyard Compute Node OS Support
Batch Shipyard is currently compatible with supported Marketplace Linux VMs
and Linux custom images supported by Azure Batch.

## Change Log
See the [CHANGELOG.md](https://github.com/Azure/batch-shipyard/blob/master/CHANGELOG.md)
file.

* * *
Please see this project's [Code of Conduct](CODE_OF_CONDUCT.md) and
[Contributing](CONTRIBUTING.md) guidelines.
