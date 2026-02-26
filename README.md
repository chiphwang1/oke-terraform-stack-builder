# OKE Terraform Stack Builder

A [Claude Code](https://claude.ai/claude-code) skill that guides you through designing and generating a complete **Oracle Kubernetes Engine (OKE)** Terraform stack and OCI Resource Manager (ORM) `schema.yaml`.

## What It Does

The skill acts as an expert OCI Infrastructure Architect, walking you through a structured 4-phase process:

| Phase | Description |
|-------|-------------|
| **1 — Discovery** | A guided questionnaire across 7 infrastructure domains |
| **2 — Architecture Summary** | Confirms your choices with cost/quota warnings before generating code |
| **3 — Code Generation** | Produces complete, plan-ready Terraform files and an ORM schema |
| **4 — Iteration** | Offers advanced add-ons, GitOps bootstrapping, Makefile, and more |

### Infrastructure Domains Covered

1. Cluster Fundamentals (workload type, Kubernetes version, control plane visibility, cluster type)
2. Networking (VCN, CIDRs, CNI plugin, SR-IOV/RDMA, gateways, bastion)
3. Node Pools (shapes, autoscaling, boot volumes, OS images, cloud-init)
4. Storage (Block Volume CSI, FSS, Object Storage, local NVMe)
5. Security & Access (instance principals, IAM policies, pod security, BYOK encryption)
6. Add-ons & Observability (CoreDNS, Cluster Autoscaler, Ingress, GPU/DCGM monitoring)
7. ORM Schema Preferences (audience, hidden vs. surfaced variables, validation rules)

### Generated Artifacts

- `provider.tf` — OCI provider and Terraform version constraints
- `variables.tf` — All input variables with types, descriptions, and defaults
- `main.tf` — `terraform-oci-oke` module call with all resolved bindings
- `outputs.tf` — Cluster ID, kubeconfig command, node pool IDs, VCN ID, bastion IP
- `terraform.tfvars.example` — Populated example values with comments
- `schema.yaml` — ORM schema with variable groups, validation, and conditional visibility

## Reference Sources

This skill only consults the following authoritative sources:

- [terraform-oci-oke](https://github.com/oracle-terraform-modules/terraform-oci-oke) — Official OKE Terraform module
- [oci-hpc-oke](https://github.com/oracle-quickstart/oci-hpc-oke) — HPC/GPU OKE quickstart
- [terraform-provider-oci](https://github.com/oracle/terraform-provider-oci) — OCI Terraform provider
- [OKE Documentation](https://docs.oracle.com/en-us/iaas/Content/ContEng/home.htm) — Oracle Container Engine official docs

## Installation

1. Clone this repository into your Claude Code skills directory:

```bash
mkdir -p ~/.claude/skills/oke-stack-builder
cp SKILL.md ~/.claude/skills/oke-stack-builder/SKILL.md
```

2. Restart Claude Code (or reload skills).

3. Trigger the skill by asking Claude Code to:
   - "Build an OKE stack"
   - "Create OKE Terraform"
   - "Generate ORM schema for OKE"
   - "Deploy an OKE cluster"

## Usage Example

```
You: Build an OKE stack for an AI/ML workload with GPU nodes

Claude: Let's start with Domain 1 — Cluster Fundamentals.
        Workload type: AI-ML ✓
        Which Kubernetes version would you like to target? ...
```

## Requirements

- [Claude Code](https://claude.ai/claude-code) CLI
- An OCI tenancy with sufficient service limits for your chosen shapes
- Terraform >= 1.3.0

## License

MIT
