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

| Platform | Company & Valuation / Scale | Description | Pricing (Starting Tier) | Free Tier / Trial Limits |
| :--- | :--- | :--- | :--- | :--- |
| **[Run:ai](https://www.run.ai/)** | NVIDIA (~$5.35T Market Cap) | GPU orchestration with dynamic fractions, quotas, priorities, and fair-share scheduling for AI/ML workloads. | Starting tier at ~$1.00 / GPU-hour (via cloud marketplace subscriptions) or custom enterprise annual license; core scheduling components open-sourced under Apache-2.0. | Free evaluation trial on request through NVIDIA sales (standard 14–30 day proof-of-concept POC license, up to 8–16 GPUs). |
| **[Google Cloud Batch](https://cloud.google.com/batch)** | Alphabet / Google (~$4.15T Market Cap) | Fully managed batch service that schedules, queues, and executes containerized batch workloads dynamically on Compute Engine VMs. | $0.00 management fee; underlying compute starting at $0.0071 / hour (E2 Spot VM, 2 vCPUs, 1 GB RAM) or ~$0.0335 / vCPU-hour on-demand. | Free forever tier includes 1 non-preemptible `e2-micro` instance (~744 hours/month in eligible US regions) + 30-day $300 credit free trial for new accounts. |
| **[Azure Batch](https://azure.microsoft.com/en-us/services/batch/)** | Microsoft (~$4.02T Market Cap) | Cloud-scale job scheduling and compute management with pool-based provisioning, task dependencies, and Azure CycleCloud HPC integration. | $0.00 management fee; underlying compute starting at $0.0026 / hour (B1ls Spot VM, 1 vCPU, 0.5 GiB RAM) or $0.0104 / hour on-demand (B1s VM, 1 vCPU, 1 GiB RAM). | Always free tier includes 750 hours/month of select B-series VMs for the first 12 months + 30-day $200 initial credit free trial. |
| **[AWS Batch](https://aws.amazon.com/batch/)** | Amazon (~$2.74T Market Cap) | Fully managed batch computing service dynamically provisioning EC2 and serverless Fargate containers with job queues and array jobs. | $0.00 management fee; underlying compute starting at $0.04048 / vCPU-hour + $0.004445 / GB-hour (AWS Fargate on-demand) or from $0.0042 / hour for EC2 `t4g.nano` instances. | 12-month free tier includes 750 hours/month of `t2.micro` or `t3.micro` EC2 instances + 500 MB/month Amazon ECR container storage free forever. |
| **[Oracle Cloud Infrastructure (OCI) Batch](https://docs.oracle.com/en-us/iaas/Content/batch/home.htm)** | Oracle (~$420B Market Cap) | Fully managed batch processing service with job pools, task profiles, priority scheduling, and automated compute fleet scaling. | $0.00 management fee; underlying compute starting at $0.01075 / OCPU-hour ($0.005375 / vCPU-hour) on Ampere A1 Compute or $0.003 / hour for Preemptible shapes. | Always free tier includes 4 OCPUs and 24 GB RAM for Ampere A1 Compute (~3,000 OCPU hours/month) + 30-day $300 credit free trial. |
| **[IBM Spectrum LSF](https://www.ibm.com/products/spectrum-lsf)** | IBM (~$215B Market Cap) | Enterprise workload management suite with policy-driven fair-share, preemption, resource reservation, and multi-cluster federation. | Starting tier at ~$0.08 / vCPU-hour via IBM Cloud Pay-Per-Use PAYGo, or starting at ~$120 / core managed via perpetual/annual Passport Advantage licenses. | 30-day free trial available for IBM Spectrum LSF suite on IBM Cloud and on-premises evaluation clusters (up to 10 cluster nodes). |
| **[Altair PBS Professional](https://altair.com/pbs-professional)** | Altair Engineering (~$9.6B Market Cap / Acquired by Siemens) | High-performance workload manager with intelligent topology-aware scheduling, scaling, and analytics for HPC and engineering simulation. | Starting tier at ~$115–$120 / socket annual maintenance license (HPE OEM MSRP SKU) or via Altair Units subscription tokens; free open-source edition available as OpenPBS (AGPLv3). | 30-day free evaluation trial license available upon registration (supports full PBS Pro cluster features for up to 32 cores). |
| **[Slurm Cloud (SchedMD)](https://slurm.schedmd.com/)** | SchedMD / NVIDIA (~$5.35T Parent Cap; formerly private ~$50M) | Industry-standard supercomputing workload manager for fine-grained job prioritization, GPU allocation, and cloud bursting. | Open-source software is $0.00 (GPLv2); commercial enterprise support contracts start at ~$250–$350 / socket or GPU annually (minimum contract tiers typically $15,000/year). | Open-source Slurm is free forever (community-supported); SchedMD offers 30-day pilot proof-of-concept enterprise support for qualified enterprise cloud deployments. |
| **[HTCondor](https://htcondor.org/)** | Center for High Throughput Computing (UW–Madison / Open Source) | High-throughput distributed batch scheduler optimized for long-running, compute-intensive, loosely coupled scientific workloads. | Open-source software is $0.00 (Apache-2.0); enterprise software maintenance & priority SLA agreements start at ~$5,000–$10,000 / year contracted via UW-Madison CHTC. | Open-source core is free forever without node limits; 30-day free enterprise pilot support consultation available for academic and research organizations. |



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
