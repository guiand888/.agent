# OVHcloud Terraform Provider Standards

## Purpose
Define agent behavior for Terraform provider selection and configuration in OVHcloud projects.

## Scope
All Terraform configurations deploying, managing, or automating OVHcloud resources.

## Rules

### Always
- Use the OVHcloud provider mapping for each Control Panel concept
- Select `ovh` provider for: project settings, cloud project, project users & roles, IAM, managed Kubernetes, container registry, vRack, OVH-specific networking (ip_service, iploadbalancing), logs platform, object storage at project-level
- Select `openstack` provider for: Public Cloud compute, block storage, Swift/object storage, load balancers, floating IPs, routers, subnets, networking primitives
- Select `kubernetes` provider for in-cluster resources (namespaces, deployments, services) after OVH cluster provisioning
- Select `vsphere` provider for VMware on OVHcloud
- Select `nutanix` provider for Nutanix on OVHcloud
- Select `aws` provider only when OVH mapping explicitly indicates it
- Declare required providers with explicit version constraints (pin at least major.minor)
- Configure provider blocks with required authentication and endpoints
- Use provider aliasing with explicit `provider =` when multiple providers manage similar resources
- Use provider-specific resource names from OVHcloud mapping (e.g., `ovh_cloud_project`, `openstack_compute_instance_v2`)
- Treat resources marked `[data source]` as read-only
- Pin provider versions; avoid floating `latest`
- Verify exact resource coverage in provider docs for partially available features
- Reference provider registry or documentation pages listed by OVHcloud before selecting resources

### Never
- Use a provider not listed in OVHcloud mapping for a GUI concept
- Create resources via guesswork when mapping lists concept as "not available"
- Use `openstack` provider for resources OVH maps to `ovh` provider (and vice versa) without documented justification
- Use `ovh` provider for in-cluster Kubernetes objects; use `kubernetes` provider instead

### Ask Before
- When OVH mapping lists multiple possible providers for a concept
