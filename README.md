# Awesome-Cloud-Native-Batch-Computing

## Top Cloud-Native Batch Computing Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**  

*Focused on Gang Scheduling, Queue Management & HPC Migration to Kubernetes*  

**Last updated: October 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Cloud-Native Batch Computing**. These tools enable organizations to run batch, HPC, and AI/ML workloads on Kubernetes—from gang scheduling for distributed training to hierarchical quota management for multi-tenant clusters and Slurm-on-Kubernetes migration paths.



**Examples** include AWS Batch, Google Cloud Batch, Azure Batch, Slurm, HTCondor, IBM Spectrum LSF, Altair PBS Pro, Kubernetes Jobs, Nomad, and Run:ai (the category leaders).



**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, gang scheduling, and open batch infrastructure—ideal for platform engineers, HPC teams, and organizations seeking transparent, vendor-independent batch computing.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **[AWS Batch](https://aws.amazon.com/batch/)**  

  **Fully managed batch computing service** that dynamically provisions compute resources based on workload volume . Features **managed compute environments**, **job queues**, **job definitions**, and **array jobs** . **Supports both EC2 and Fargate** (Fargate is ~10% more expensive) . **The most integrated with AWS ecosystem**—IAM, VPC, CloudWatch, and Step Functions . **Trade-off**: Documentation encourages Fargate over EC2; cluster-level introspection requires custom metrics .



- **[Google Cloud Batch](https://cloud.google.com/batch)**  

  **Fully managed batch service** that schedules, queues, and executes batch workloads on Google Cloud . Features **job definitions**, **task dependencies**, **auto-scaling**, and **integration with Google Cloud services** . **The simplest path to batch on GCP** .



- **[Azure Batch](https://azure.microsoft.com/en-us/services/batch/)**  

  **Cloud-scale job scheduling and compute management** . Features **pool-based compute**, **job and task scheduling**, **auto-scaling**, and **integration with Azure services** . **Azure CycleCloud** adds Slurm/HPC cluster provisioning . **The best choice for Microsoft-centric organizations** .



- **[Oracle Cloud Infrastructure (OCI) Batch](https://docs.oracle.com/en-us/iaas/Content/batch/home.htm)**  

  **Fully managed batch processing service** with clear separation between **job submission and execution** . Uses **queues and scheduling logic** to manage workloads efficiently—handles sudden demand spikes without pre-provisioned infrastructure . **Core components**: **Batch Context** (networking, fleets, logging), **Job Pools** (logical grouping), **Jobs** (complete workflows), **Tasks** (smallest execution units in containers), **Task Profiles** (reusable resource configurations) . **Priority-based scheduling** ensures critical workloads run first in shared environments . **The most architecturally transparent managed batch service** .



- **[Slurm Cloud (SchedMD)](https://slurm.schedmd.com/)**  

  **The industry-standard HPC workload manager** available as a managed service on major clouds . **Trusted by the world's largest supercomputing centers** for fine-grained batch job scheduling, queue management, prioritization, and accounting . **The reference implementation for HPC batch scheduling** .



- **[HTCondor](https://htcondor.org/)**  

  **High-throughput computing (HTC) workload manager** designed for long-running, loosely coupled tasks . **The standard for scientific computing workflows** that run for days or weeks .



- **[IBM Spectrum LSF](https://www.ibm.com/products/spectrum-lsf)**  

  **Enterprise HPC workload management** with policy-driven scheduling, fair-share, and preemption . **The enterprise standard** for mission-critical HPC workloads.



- **[Altair PBS Professional](https://altair.com/pbs-professional)**  

  **HPC workload manager** with intelligent scheduling, scaling, and analytics . **The standard for engineering simulation and high-performance computing** .



- **[Run:ai (NVIDIA)](https://www.run.ai/)**  

  **GPU orchestration with fractions, quotas, priorities, and fair-share policies** . **Now fully open source** as part of NVIDIA DSX AI Factory Platform . **The most focused on GPU workload management** .



## Open-Source GitHub Projects



- **[Volcano](https://github.com/volcano-sh/volcano)**  

  **Cloud native batch computing system for intensive workloads** (Apache-2.0) . **The most comprehensive open-source batch scheduler for Kubernetes**—**CNCF Incubating project** extending and enhancing the standard kube-scheduler . **Core abstractions**: **PodGroup** (gang semantics) and **Queue** (hierarchical queues) . **Built-in plugins**: **gang scheduling**, **priority**, **preemption**, **backfilling**, **topology-aware scheduling** . **VCJob** provides training-task-oriented job abstraction . **Integrates with Spark, Flink, Ray, TensorFlow, PyTorch, Argo, MindSpore, PaddlePaddle, Kubeflow, MPI, Horovod, MXNet, KubeGene** . **15+ years of collective experience** operating diverse high-performance workloads . **Widely adopted across Internet/Cloud, Finance, Manufacturing, and Medical sectors** . **The reference implementation for gang scheduling on Kubernetes** .



- **[Kueue](https://github.com/kubernetes-sigs/kueue)**  

  **Kubernetes-native job queueing** (Apache-2.0) for **resource quotas, fair sharing, and priority admission** . **The most Kubernetes-native approach to batch job admission**—**deliberately narrow abstraction**: does not replace the scheduler, only handles job-level **admission** . **ClusterQueue/LocalQueue** two-level model naturally aligns with Kubernetes multi-tenancy (namespaces) . **Borrowing and reclaiming (cohort mechanism)** is a first-class citizen . **Assumes "queueing decision" and "placement decision" can be separated**—when placement itself is the hard part (strong topology constraints, fine-grained gang timing, inter-node affinity scoring), Kueue cannot intervene . **Relatively young**—teams porting a decade of Slurm policy ecosystem will find many policies have no equivalent . **The best choice when you only need quota + queueing without complex scheduling plugins** .



- **[YuniKorn](https://github.com/apache/yunikorn)**  

  **Apache YuniKorn** (Apache-2.0) is a **resource scheduler managing workloads in both Kubernetes and Apache Hadoop YARN** environments . **The most versatile open-source scheduler for hybrid environments**—**supports fine-grained resource allocation (CPU, memory, GPU)**, **hierarchical queues and preemption** ensuring fairness among jobs and users . **Can schedule both batch and long-running jobs** . **Built-in web dashboard** for multi-tenant fair sharing . **Best for**: organizations managing both Kubernetes and YARN clusters, or environments with diverse job types requiring comprehensive resource scheduling .



- **[Slurm (Slinky)](https://github.com/SlinkyProject)**  

  **Run Slurm inside Kubernetes** (Apache-2.0) . **The bridge between HPC and cloud-native**—**Slurm Operator** runs full Slurm clusters on Kubernetes infrastructure, managing the complete lifecycle of Slurm daemons as pods . **Slurm Bridge** brings Slurm scheduling to native Kubernetes workloads, allowing Slurm to act as a Kubernetes scheduler for pods . **Users submit jobs via standard Slurm interfaces (sbatch, srun)**—the plugin translates Slurm job specifications into Kubernetes pod definitions . **Supports GPU scheduling, MPI job orchestration, and accounting integration** . **Topology-aware GPU scheduling** places distributed workloads on nodes physically closest in the network fabric—minimizing communication overhead for large-scale AI training . **The most practical HPC migration path** for organizations with existing Slurm investments .



- **[Nomad](https://github.com/hashicorp/nomad)**  

  **Easy-to-use, flexible, and performant workload orchestrator** (BUSL 1.1) . **The simplest alternative to Kubernetes for batch workloads**—**single binary, entirely self-contained**, no external services for storage or coordination . **Built-in GPU support** via device plugins (GPU, FPGAs, TPUs) . **Federation for multi-region, multi-cloud** out of the box . **Proven scalability** to **10K+ nodes** in production . **Native Terraform, Consul, and Vault integration** . **The best choice for teams that want batch orchestration without Kubernetes complexity** .



- **[KEDA](https://github.com/kedacore/keda)**  

  **Kubernetes Event-driven Autoscaling** (Apache-2.0) . **The standard for event-driven batch autoscaling**—scale to zero based on SQS, Kafka, or **60+ sources** . **Combines with Kueue** for event-triggered jobs with quota admission control . **Combines with Volcano** for gang-scheduled jobs triggered by external events . **The essential scaling layer** for cloud-native batch computing .



- **[KubeRay](https://github.com/ray-project/kuberay)**  

  **Kubernetes operator for Ray** (Apache-2.0) . **The standard for distributed computing and hyperparameter tuning on Kubernetes**—provides **RayCluster, RayJob, and RayService** custom resources . **Explicitly tailored for Ray's stateful head/worker architecture, actor-based dynamic placement, fine-grained GPU/TPU resource allocation, and zero-downtime model serving** . **Integrates with Cluster Autoscaler and KEDA** for scaling . **Combines with Kueue** for Ray clusters with resource quota management .



- **[Kubeflow Trainer v2](https://github.com/kubeflow/trainer)**  

  **Distributed training operator** (Apache-2.0) . **The standard for multi-role training jobs** on Kubernetes—**JobSet** models multi-role training jobs as a single lifecycle unit: launcher + workers, parameter servers + compute processes, trainers + samplers . **Declarative success conditions** ("any role completes = overall complete" or "all complete = complete") . **Failure policies** per failure type (restart entire group from checkpoint) . **The layer that solves "how does a job live after admission"** —replaces 5 common platform glue scripts .



- **[JobSet](https://github.com/kubernetes-sigs/jobset)**  

  **Kubernetes-native API for managing a group of Jobs as a single unit** (Apache-2.0) . **The multi-role job controller layer** that complements Kueue's admission control . **The standard for modeling distributed training jobs** that require multiple coordinated roles .



### Additional Strong Open-Source Options



- **[KAI Scheduler (NVIDIA)](https://github.com/NVIDIA/KAI-Scheduler)** — The scheduling engine behind NVIDIA Run:ai (Apache-2.0, CNCF Sandbox) . **Gang scheduling, bin-packing, hierarchical queues, DRF, workload consolidation, elastic workloads, and GPU sharing** .

- **[GPU Fractioning Operator](https://github.com/NVIDIA/k8s-gpu-fractioning-operator)** — CUDA-native GPU fractioning for Kubernetes (Apache-2.0) . **Multiple workloads share a single GPU with hard memory isolation** .

- **[Apache Airflow](https://github.com/apache/airflow)** — Platform to programmatically author, schedule, and monitor workflows (Apache-2.0) . **The standard for DAG-based data pipeline orchestration** .

- **[Argo Workflows](https://github.com/argoproj/argo-workflows)** — Container-native workflow engine for Kubernetes (Apache-2.0) . **The standard for CI/CD and ML pipeline orchestration on Kubernetes** .

- Community **n8n** workflows for batch job monitoring and alerting.



**Frameworks for building custom systems**: Combine **Volcano** for gang scheduling with **Kueue** for quota admission, **KEDA** for event-driven autoscaling, **KubeRay** for distributed computing, **JobSet** for multi-role training jobs, and **Slinky** for Slurm migration—creating a fully self-hosted, enterprise-grade cloud-native batch computing platform.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Cloud-native batch computing systems handling production workloads must follow security best practices and implement appropriate resource quotas and access controls.

- **Open-source batch scheduling is mature and production-ready.** Volcano is a CNCF Incubating project with 15+ years of collective HPC experience . Kueue provides Kubernetes-native quota management . YuniKorn handles hybrid Kubernetes/YARN environments . **These are genuine alternatives to commercial platforms.**

- **The scheduler landscape has clear specialization.** **Volcano** for gang scheduling and distributed training . **Kueue** for quota admission without replacing the scheduler . **YuniKorn** for multi-tenant fair sharing with hierarchical queues . **Slinky** for Slurm migration to Kubernetes . **KAI Scheduler** for GPU fractions and quotas . **The wrong choice is trying to make one scheduler cover workloads outside its model** .

- **Admission and placement are separate concerns.** Kueue controls *when* a job is allowed to start (quota admission). Volcano and YuniKorn control *where* pods run (placement scheduling). **JobSet and Kubeflow Trainer control *how* a job lives after admission** (multi-role lifecycle). **These layers compose**—Kueue + Volcano is a common production combination for quota-controlled gang-scheduled training jobs .

- **GPU quota coordination is critical.** GPU quotas defined independently in Kueue, Volcano, YuniKorn, and Slurm **do not talk to each other** . If you configure 8 GPUs in each system, you've promised 32 GPUs but might only have 8 physical—**misconfiguration can deadlock your cluster** . **Partition GPU capacity across the systems you actually use** .

- **Slinky respects existing HPC investments.** Users submit jobs via standard `sbatch`/`srun`—**nothing changes for existing Slurm users** . Topology-aware GPU scheduling minimizes communication overhead for large-scale AI training . **The pragmatic choice for organizations with years of Slurm job scripts** .

- Self-hosted open-source solutions require proper Kubernetes cluster management, scheduler configuration, and ongoing maintenance. **Batch computing infrastructure is performance-critical**—monitor scheduler latency and queue depth for production workloads.



---



**Made for platform engineers, HPC teams, and organizations building transparent batch computing solutions.**  

Let's make Cloud-Native Batch Computing more open, data-driven, and gang-scheduled.
