---
tags:
  - GCP
  - learning
  - technical
  - cloud
---

u1
student-03-3e7cc90e0aac@qwiklabs.net

u2
student-03-a12615868d27@qwiklabs.net

3wNoNht5AB19
qwiklabs-gcp-02-6b94d947ee4b


IAM & Admin/IAM

- used to grant permissions to users
- Can assign roles to users
	- roles bestow sets of permissions that allow role-holders to do certain things
- [Basic roles](https://docs.cloud.google.com/iam/docs/roles-permissions#primitive_roles) (formerly primitive roles)
	- Browser (can browse GCP resources) 
	- Editor (view, update, delete most GCP resources; view permissions)
	- Owner (full access to resources; view permissions) 
	- Viewer (view resources; view permissions)

|Role Name|Permissions|
|---|---|
|`roles/browser`|Read access to browse the hierarchy for a project, including folders, organizations, and IAM policies. This role doesn't include permission to view resources within a project.|
|`roles/viewer`|Permissions for read-only actions that do not affect state, such as viewing (but not modifying) existing resources or data.|
|`roles/editor`|All viewer permissions, plus permissions for actions that modify state, such as changing existing resources.|
|`roles/owner`|All editor permissions and permissions for the following actions:  <br>• Manage roles and permissions for a project and all resources within the project.  <br>• Set up billing for a project.|

student_1_gcp_bucket_121209

Roles (non-basic) can be associated with permissions for specific resources types
- e.g. Cloud Storage > Storage Object Viewer allows a user to view a bucket, even if they don't have Viewer (project level role) role


Can also be modified using the Cloud Shell