## Copilot instructions for NetApp Workload Factory setup and administration documentation

### Repository overview
Product: NetApp Workload Factory

NetApp Workload Factory is a cloud-based lifecycle management platform that helps users optimize workloads using Amazon FSx for NetApp ONTAP file systems. It is delivered as a SaaS console and supports workloads including databases, VMware migrations, AI chatbots, and general storage management on AWS.

### Repository structure
- `workload-factory-overview.adoc` – Product overview covering features, architecture, key concepts (accounts, links, Codebox, permissions), and supported AWS regions
- `quick-start.adoc` – Getting started guide: sign up, add credentials, start using FSx for ONTAP
- `sign-up-saas.adoc` – Account creation and sign-up steps for the SaaS console
- `add-credentials.adoc` – Adding AWS credentials manually or via CloudFormation to grant Workload Factory permissions to manage AWS resources
- `manage-credentials.adoc` – Managing existing AWS credentials in a Workload Factory account
- `permissions-reference.adoc` – Reference for IAM permission policies by workload (Storage, Databases, VMware, GenAI, Setup), including copiable JSON
- `codebox-automation.adoc` – Overview of the Codebox IaC co-pilot feature and supported code formats
- `use-codebox.adoc` – How to use Codebox to generate and save automation code
- `use-cloudshell.adoc` – Using CloudShell within the Workload Factory console to issue AWS CLI and ONTAP CLI commands
- `console-experiences.adoc` – Differences between the Workload Factory console and the NetApp Console access paths
- `log-in.adoc` – Logging in to Workload Factory
- `manage-service-accounts.adoc` – Creating and managing service accounts for API automation
- `configure-notifications.adoc` – Configuring Workload Factory notification settings
- `well-architected-workloads.adoc` – Well-architected analysis feature for FSx for ONTAP, SQL Server, and Oracle deployments
- `whats-new.adoc` – Release notes for Workload Factory administration features
- `whats-next.adoc` – Post-setup guidance pointing to workload-specific documentation
- `support-registration.adoc` – Registering for NetApp support
- `get-help.adoc` – Getting help and contacting support
- `create-custom-dashboard.adoc` – Creating custom dashboards in Workload Factory
- `learn-custom-dashboards.adoc` – Overview of custom dashboard capabilities
- `manage-custom-dashboards.adoc` – Managing existing custom dashboards
- `troubleshoot-custom-dashboards.adoc` – Troubleshooting custom dashboards
- `_include/` – Shared AsciiDoc content fragments included across pages
- `_whatsnew/` – Individual release note files included by `whats-new.adoc`
- `media/` – Screenshots and images referenced in documentation

### Product-specific context

**Architecture and components:**
- Workload Factory is a SaaS platform accessible through the *Workload Factory console* (`console.workloads.netapp.com`) and the *NetApp Console* (`console.netapp.com`)
- *Accounts* organize resources, workloads, and credentials for an organization; the account creator becomes the account admin
- *Credentials* are AWS IAM roles added to a Workload Factory account to grant permissions for managing AWS resources; credentials use an AWS assume-role flow
- *Links* establish trust and connectivity between Workload Factory and one or more FSx for ONTAP file systems, enabling direct ONTAP REST API calls not available through the FSx API; links use AWS Lambda
- *Codebox* is an IaC co-pilot embedded in the console that generates code (REST API, AWS CLI, CloudFormation, Terraform) for any supported Workload Factory operation; includes a *Codebox Viewer* and an *Automation Catalog*
- *CloudShell* is a browser-based shell within the Workload Factory console for executing AWS CLI and ONTAP CLI commands using configured credentials
- *Service accounts* provide API-only access for automation without relying on individual user accounts
- *Well-architected analysis* performs daily scans of FSx for ONTAP, SQL Server, and Oracle deployments and surfaces misconfigurations with remediation options

**Key concepts:**
- A *workload* is a combination of resources, code, and services designed to serve a business goal; Workload Factory supports workloads for storage, databases, VMware, and GenAI
- *Permission policies* are IAM policies bundled by workload and permission level (for example, *View, planning, and analysis*; *Operations and remediation*; *File system creation and deletion*); each workload has its own policy set
- *Operational modes* control access to the cloud estate: *basic*, *read-only*, and *read/write*
- Credentials can be added *manually* (IAM policy and role created in AWS console) or *automatically* (via AWS CloudFormation stack); GovCloud credentials must be added manually
- The *Automation Catalog* stores saved Codebox IaC jobs as reusable templates

**Naming conventions and terminology:**
- *FSx for ONTAP* refers to Amazon FSx for NetApp ONTAP; always use this abbreviated form after the first use
- *Workload Factory* (not "WF" or "workload factory") is the product name; always capitalize both words
- *Codebox* is a single word, capitalized
- *CloudShell* is a single word, capitalized
- *IAM role* and *IAM policy* follow AWS capitalization conventions
- *ARN* = Amazon Resource Name (used when registering IAM roles)
- The plural *credentials* refers to a set of AWS IAM role-based access keys registered in Workload Factory, not individual access key pairs
- *Link* (capitalized in context) refers specifically to the Workload Factory connectivity component using AWS Lambda, not a generic hyperlink
- Permission policy levels use title case: *View, planning, and analysis*; *Operations and remediation*; *File system creation and deletion*

### Typical user workflows

**Initial setup:**
Sign up at console.workloads.netapp.com → Create a Workload Factory account → Add AWS credentials (manually or via CloudFormation) → Select workload capabilities and permission levels → Verify credentials on the Credentials page

**Add credentials manually:**
Select workload capabilities and permission levels → Copy IAM policy JSON from Codebox → Create IAM policies in AWS Management Console → Create IAM role with trusted entity pointing to Workload Factory → Copy Role ARN → Enter credentials name and ARN in Workload Factory

**Add credentials via CloudFormation:**
Select workload capabilities and permission levels → Enter credentials name → Redirect to CloudFormation → Acknowledge IAM resource creation → Create stack → Monitor Credentials page for confirmation

**Use Codebox for automation:**
Perform an operation in the Workload Factory console wizard → View generated IaC in Codebox Viewer → Copy code or save to Automation Catalog → Execute code using AWS CLI, CloudFormation, Terraform, or REST API

**Use CloudShell:**
Open CloudShell from the Administration menu → Select credentials and region → Issue AWS CLI or ONTAP CLI commands → Optionally set FSx context with `using fsx <fileSystemId>` for ONTAP commands
