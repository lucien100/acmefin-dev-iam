# Access Matrix: acmefin-dev-iam

## Personas and Access Levels

| Persona        | Environment | Resources              | Access Type         | Notes                                      |
|----------------|-------------|------------------------|---------------------|--------------------------------------------|
| Dev-App        | dev         | Cloud Run, Logs        | deploy, read logs   | No access to IAM or prod resources         |
| Dev-Data       | dev         | BigQuery, Storage      | read/write          | No access to compute or IAM                |
| Analyst        | dev         | BigQuery               | read only           | No schema changes, no access to storage    |
| Sec-Engineer   | dev         | IAM, Logs, SCC         | read / limited admin| Can view IAM policies, audit logs          |
| Ops-SRE        | dev         | Compute, Monitoring    | admin               | Can restart services, no access to data    |
| CI/CD SA       | dev         | Cloud Run              | deploy only         | Service account for automated deployments  |
| Backup SA      | dev         | Storage                | read/write          | Can backup data, no access to BigQuery     |

## Access Principles

- No one has `Editor` or `Owner` roles  
- All access is scoped to project level  
- Custom roles are used to enforce least privilege  
- Service accounts are tightly scoped  
- IAM Conditions used for time-based access (optional)
