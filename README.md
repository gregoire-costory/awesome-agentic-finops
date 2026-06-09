# Awesome Agentic FinOps [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated list of open-source and AI-native tooling for cloud cost management (FinOps): MCP servers, AI-assistant skills, AI cost agents, and the broader open-source FinOps ecosystem.

Most FinOps lists predate the agentic shift. This one leads with the new layer (MCP servers, Claude and other assistant skills, AI cost agents) and keeps a complete map of the established open-source FinOps tooling alongside it.

Maintained by the team at [Costory](https://costory.io). Costory's MCP is listed under [MCP Servers](#mcp-servers) on exactly the same terms as every other entry. Additions, corrections, and removals (including of our own entry, if the list ever skews) are welcome by pull request or issue. See [Contributing](CONTRIBUTING.md).

## Contents

- [MCP Servers](#mcp-servers)
- [AI Assistant Skills & Plugins](#ai-assistant-skills--plugins)
- [AI Cost Agents](#ai-cost-agents)
- [Kubernetes & Container Cost](#kubernetes--container-cost)
- [Infrastructure as Code Cost](#infrastructure-as-code-cost)
- [Multi-Cloud Platforms & Scanners](#multi-cloud-platforms--scanners)
- [AWS](#aws)
- [Azure](#azure)
- [GCP & Other Clouds](#gcp--other-clouds)
- [Pricing Data & Calculators](#pricing-data--calculators)
- [GreenOps & Sustainability](#greenops--sustainability)
- [Standards & Foundations](#standards--foundations)
- [Learning & Reference](#learning--reference)
- [Related Lists](#related-lists)

## MCP Servers

Model Context Protocol servers that expose cloud cost data and actions to AI assistants.

- [aarora79/aws-cost-explorer-mcp-server](https://github.com/aarora79/aws-cost-explorer-mcp-server) - AWS spend via Cost Explorer plus Amazon Bedrock model-invocation logs, over MCP.
- [ravikiranvm/aws-finops-mcp-server](https://github.com/ravikiranvm/aws-finops-mcp-server) - AWS cost analysis, waste audit, and budgets across CLI profiles; credentials stay local.
- [prashantgupta123/aws-finops-mcp-server](https://github.com/prashantgupta123/aws-finops-mcp-server) - AWS FinOps MCP packaged for the Amazon Bedrock AgentCore runtime.
- [msftnadavbh/AzurePricingMCP](https://github.com/msftnadavbh/AzurePricingMCP) - Azure retail pricing over MCP, with Spot and savings analysis and orphaned-resource detection.
- [julianobarbosa/azure-finops-mcp-server](https://github.com/julianobarbosa/azure-finops-mcp-server) - Azure cost analysis, waste audit, and budgets over MCP.
- [chaandannn/finopsmcp](https://github.com/chaandannn/finopsmcp) - "nable", connects Claude to AWS, Azure, GCP, and SaaS billing (such as Datadog) in plain English.
- [Musheer360/aws-calculator-mcp](https://github.com/Musheer360/aws-calculator-mcp) - Drives the AWS Pricing Calculator (436 services) via headless Chrome; Savings Plans and Reserved Instances, no credentials required.
- [jasonwilbur/cloud-cost-mcp](https://github.com/jasonwilbur/cloud-cost-mcp) - Multi-cloud price comparison (AWS, Azure, GCP, OCI) from public pricing APIs.
- [ecos-labs/ecos](https://github.com/ecos-labs/ecos) - Open FinOps data stack with a CLI and an MCP server.
- [aws-samples/sample-cfm-tips-mcp](https://github.com/aws-samples/sample-cfm-tips-mcp) - MCP server built on AWS Cloud Financial Management technical playbooks.
- [Costory MCP](https://docs.costory.io/features/mcp) - Hosted MCP for the Costory cost platform; query and compare costs, create alerts and saved views, send Slack reports, over OAuth for Claude, Cursor, VS Code, and Dust.

## AI Assistant Skills & Plugins

Skills and plugins that turn an AI coding assistant into a cost operator.

- [Aboudjem/aws-cost-audit-skill](https://github.com/Aboudjem/aws-cost-audit-skill) - Claude skill that audits an AWS bill; evidence-first, read-only, follows AWS Well-Architected and the FinOps Foundation framework.
- [mindaugasnakrosis/azure-costs-analyzer](https://github.com/mindaugasnakrosis/azure-costs-analyzer) - Claude Code skill for a read-only Azure cost review against Microsoft and FinOps Foundation rules.
- [prajapatimehul/claude-aws-cost-saver](https://github.com/prajapatimehul/claude-aws-cost-saver) - Claude Code and Codex plugin with 160+ AWS cost checks.
- [zxkane/aws-skills](https://github.com/zxkane/aws-skills) - Claude Code plugins for AWS including cost optimization, CDK, serverless, and Bedrock AgentCore.
- [abhilashchowdhary/claude-code-skills](https://github.com/abhilashchowdhary/claude-code-skills) - Claude Code skills including a full AWS cost audit.
- [shivamsriva31093/gcp-ironclad](https://github.com/shivamsriva31093/gcp-ironclad) - Claude Code skills plus a gcp-finops MCP for GCP API-key audit and safe spend hardening.
- [unfunco/claude-aws-billing-summary](https://github.com/unfunco/claude-aws-billing-summary) - GitHub Action that posts a Claude-generated monthly AWS billing summary.
- [OptimNow/cloud-finops-skills](https://github.com/OptimNow/cloud-finops-skills) - FOCUS-aligned FinOps knowledge skill and MCP for AI coding assistants.
- [Cletrics/finops-agents](https://github.com/Cletrics/finops-agents) - Collection of FinOps specialist agents for Claude Code, Cursor, and other assistants.
- [OptimNow/finops-mcp-resources](https://github.com/OptimNow/finops-mcp-resources) - Curated MCP servers and resources for cloud FinOps practitioners.

## AI Cost Agents

Standalone agents and apps that analyze and act on cloud cost.

- [MrigankJaiswal-hub/finops-Agent](https://github.com/MrigankJaiswal-hub/finops-Agent) - FinOps agent on AWS Bedrock with analyze, recommend, and execute steps.
- [danjamk/slack-aws-cost-guardian](https://github.com/danjamk/slack-aws-cost-guardian) - AI-driven AWS cost monitoring and anomaly alerts in Slack.
- [vanhoangkha/sample-costminimizer](https://github.com/vanhoangkha/sample-costminimizer) - AWS cost tool generating reports from Cost Explorer, Trusted Advisor, Compute Optimizer, and Bedrock.
- [kkpkishan/aws-billing-insights](https://github.com/kkpkishan/aws-billing-insights) - AWS billing analysis and recommendations via Amazon Bedrock.

## Kubernetes & Container Cost

- [opencost/opencost](https://github.com/opencost/opencost) - CNCF project and spec for Kubernetes and cloud cost monitoring.
- [robusta-dev/krr](https://github.com/robusta-dev/krr) - Prometheus-based Kubernetes CPU and memory recommendations.
- [gocrane/crane](https://github.com/gocrane/crane) - FinOps platform for Kubernetes cost and resource analytics.
- [gocrane/fadvisor](https://github.com/gocrane/fadvisor) - Cost exporters for Kubernetes guided by FinOps.
- [koordinator-sh/koordinator](https://github.com/koordinator-sh/koordinator) - QoS-based scheduling for higher cluster utilization.
- [aporia-ai/kubesurvival](https://github.com/aporia-ai/kubesurvival) - Finds the cheapest machine types that can run your workloads.
- [traas-stack/kapacity](https://github.com/traas-stack/kapacity) - Cloud-native capacity and utilization management.
- [realopslabs/kubeledger](https://github.com/realopslabs/kubeledger) - Per-namespace Kubernetes cost accounting with an MCP interface.
- [kaskol10/karpenter-optimizer](https://github.com/kaskol10/karpenter-optimizer) - Cost optimization for Karpenter NodePools.
- [cloudpilot-ai/karpenter-provider-gcp](https://github.com/cloudpilot-ai/karpenter-provider-gcp) - Karpenter provider for Google Cloud.
- [tanrikuluozlem/burn](https://github.com/tanrikuluozlem/burn) - Shows what is consuming your Kubernetes budget.
- [kube-ns-suspender/kube-ns-suspender](https://github.com/kube-ns-suspender/kube-ns-suspender) - Scales idle namespaces down on demand.
- [AxaFrance/dailyclean](https://github.com/AxaFrance/dailyclean) - Turns pods off outside office hours.
- [truefoundry/CruiseKube](https://github.com/truefoundry/CruiseKube) - Kubernetes resource optimization controller.

## Infrastructure as Code Cost

- [infracost/infracost](https://github.com/infracost/infracost) - Cloud cost estimates for Terraform in CI and pull requests.
- [cycloidio/terracost](https://github.com/cycloidio/terracost) - Terraform cost estimation library and CLI.
- [terrateamio/openinfraquote](https://github.com/terrateamio/openinfraquote) - Cost estimates from Terraform plans and state files.
- [TheCloudTheory/arm-estimator](https://github.com/TheCloudTheory/arm-estimator) - Azure cost estimates for ARM, Bicep, and Terraform.
- [revant-io/cdk-cost-limit](https://github.com/revant-io/cdk-cost-limit) - Cost-aware, self-limiting AWS CDK constructs.
- [rshade/finfocus](https://github.com/rshade/finfocus) - FinOps CLI for Pulumi: projected and actual spend, budgets.
- [alikzao/terraform-cost-guard](https://github.com/alikzao/terraform-cost-guard) - Detects idle AWS resources using CUR, Athena, and Grafana.

## Multi-Cloud Platforms & Scanners

- [hystax/optscale](https://github.com/hystax/optscale) - FinOps and cost optimization across AWS, Azure, GCP, Alibaba Cloud, and Kubernetes.
- [cloud-custodian/cloud-custodian](https://github.com/cloud-custodian/cloud-custodian) - Policy-as-code engine for cost, security, and governance.
- [mlabouardy/komiser](https://github.com/mlabouardy/komiser) - Cloud-agnostic resource manager for cost, usage, security, and governance.
- [openops-cloud/openops](https://github.com/openops-cloud/openops) - No-code FinOps automation platform.
- [similarweb/finala](https://github.com/similarweb/finala) - Scanner for wasteful and unused cloud resources.
- [wearedevilabs/CloudSlash](https://github.com/wearedevilabs/CloudSlash) - Local-first AWS waste detection via dependency-graph analysis.
- [kosty-cloud/kosty](https://github.com/kosty-cloud/kosty) - Scans AWS services for cost waste and security gaps.
- [cleancloud-io/cleancloud](https://github.com/cleancloud-io/cleancloud) - Read-only waste detection for AWS, Azure, and GCP.
- [galaxy-future/costpilot](https://github.com/galaxy-future/costpilot) - Multi-cloud cost management platform.
- [electrolux-oss/infrawallet](https://github.com/electrolux-oss/infrawallet) - Backstage plugin for cloud cost control.
- [ssp-data/cloud-cost-analyzer](https://github.com/ssp-data/cloud-cost-analyzer) - Open framework for multi-cloud cost visibility.

## AWS

- [nilbuild/aws-cost-cli](https://github.com/nilbuild/aws-cost-cli) - AWS cost analysis in the terminal with a Slack summary.
- [mlevit/aws-auto-cleanup](https://github.com/mlevit/aws-auto-cleanup) - Deletes AWS resources by allowlist and time to live.
- [jcjorel/ec2-spot-converter](https://github.com/jcjorel/ec2-spot-converter) - Converts EC2 instances between On-Demand and Spot in place.
- [sqlxpert/lights-off-aws](https://github.com/sqlxpert/lights-off-aws) - Stops EC2 and RDS on a cron schedule via resource tags.
- [toricls/acos](https://github.com/toricls/acos) - Interactive CLI for AWS cost across an Organization.
- [c1982/awsdtc](https://github.com/c1982/awsdtc) - AWS data-transfer cost explorer.
- [jimzucker/aws-forecast](https://github.com/jimzucker/aws-forecast) - Reproduces the Cost Explorer forecast and posts it to Slack.
- [realadeel/CloudVac](https://github.com/realadeel/CloudVac) - Cleans up unused AWS resources across profiles and regions.
- [robsonbittencourt/aws-cost-miner](https://github.com/robsonbittencourt/aws-cost-miner) - Extracts useful information from the AWS billing report.
- [idvoretskyi/aws-s3-cost-explorer](https://github.com/idvoretskyi/aws-s3-cost-explorer) - Single-binary CLI for S3 storage costs and tiers.
- [turbot/steampipe-mod-aws-thrifty](https://github.com/turbot/steampipe-mod-aws-thrifty) - Checks AWS accounts for unused and under-used resources.
- [aws-solutions-library-samples/cloud-intelligence-dashboards-framework](https://github.com/aws-solutions-library-samples/cloud-intelligence-dashboards-framework) - Deploys the AWS Cloud Intelligence Dashboards.
- [aws-samples/service-screener-v2](https://github.com/aws-samples/service-screener-v2) - Evaluates AWS configurations against best practices including cost.
- [sls-mentor/sls-mentor](https://github.com/sls-mentor/sls-mentor) - Audits serverless AWS apps across cost and other pillars.
- [trackit/trackit](https://github.com/trackit/trackit) - Tooling to understand and improve AWS usage.
- [disneystreaming/automated-cloud-advisor](https://github.com/disneystreaming/automated-cloud-advisor) - Collects under-utilized AWS resources for cost optimization.

## Azure

- [mivano/azure-cost-cli](https://github.com/mivano/azure-cost-cli) - CLI for Azure cost with daily cost, budgets, and anomaly detection; assistant-friendly output.
- [thgossler/AzSaveMoney](https://github.com/thgossler/AzSaveMoney) - Flags unused Azure resources for cleanup via tagging.
- [rowilson/azure-cost-management-pbit](https://github.com/rowilson/azure-cost-management-pbit) - Power BI template for Azure Cost Management.
- [microsoft/finops-toolkit](https://github.com/microsoft/finops-toolkit) - Microsoft tooling and FOCUS exports for Azure FinOps.

## GCP & Other Clouds

- [Cyclenerd/google-cloud-pricing-cost-calculator](https://github.com/Cyclenerd/google-cloud-pricing-cost-calculator) - GCP cost estimates from YAML files and a CLI.
- [Cyclenerd/poweroff-google-cloud-cap-billing](https://github.com/Cyclenerd/poweroff-google-cloud-cap-billing) - Caps GCP billing by automating shutdown.
- [doitintl/iris3](https://github.com/doitintl/iris3) - Automatic GCP resource labeling for cost allocation.
- [dennisklappe/cf-ledger](https://github.com/dennisklappe/cf-ledger) - Per-application Cloudflare cost attribution.

## Pricing Data & Calculators

- [vantage-sh/ec2instances.info](https://github.com/vantage-sh/ec2instances.info) - EC2 and related instance pricing comparison.
- [doitintl/gcpinstances.info](https://github.com/doitintl/gcpinstances.info) - GCP instance pricing comparison.
- [bytebase/dbcost](https://github.com/bytebase/dbcost) - Cloud database pricing comparison.
- [TUM-DIS/cloudspecs](https://github.com/TUM-DIS/cloudspecs) - Browser explorer for EC2 instances powered by DuckDB-WASM.

## GreenOps & Sustainability

- [omrdev1/greenops-cli](https://github.com/omrdev1/greenops-cli) - Carbon-footprint linting for CI/CD pipelines.
- [vinayalodha/greenbot](https://github.com/vinayalodha/greenbot) - AWS cost optimization tool.

## Standards & Foundations

- [FinOps-Open-Cost-and-Usage-Spec/FOCUS_Spec](https://github.com/FinOps-Open-Cost-and-Usage-Spec/FOCUS_Spec) - FOCUS, the open specification for billing and usage data.
- [finopsfoundation](https://github.com/finopsfoundation) - The FinOps Foundation framework, definitions, and KPIs.
- [project-koku/koku](https://github.com/project-koku/koku) - Open cost management for hybrid cloud, from Red Hat.

## Learning & Reference

- [kdeldycke/awesome-billing](https://github.com/kdeldycke/awesome-billing) - Billing and payments knowledge for cloud platforms.
- [ravsau/aws-cloud-cost-management](https://github.com/ravsau/aws-cloud-cost-management) - AWS cost optimization notes and a video playlist.
- [vantage-sh/handbook.vantage.sh](https://github.com/vantage-sh/handbook.vantage.sh) - The Cloud Cost Handbook, plain-English guides to cloud pricing.
- [ahmadalibagheri/finops-tutorial](https://github.com/ahmadalibagheri/finops-tutorial) - A FinOps tutorial series.

## Related Lists

- [jmfontaine/awesome-finops](https://github.com/jmfontaine/awesome-finops) - The original Awesome FinOps list.
- [Funkmyster/awesome-cloud-cost-control](https://github.com/Funkmyster/awesome-cloud-cost-control) - Tools, blogs, podcasts, and standards for cloud cost control.
- [ElementTech/awesome-cloud-cost](https://github.com/ElementTech/awesome-cloud-cost) - Tips, tricks, and hacks for saving cloud cost.
- [lcenchew/awesome-aws-cost-management](https://github.com/lcenchew/awesome-aws-cost-management) - Resources for managing AWS cost.

## Contributing

Contributions are welcome. Read the [contribution guidelines](CONTRIBUTING.md) first. Open a pull request to add, correct, or remove an entry.

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](LICENSE)

To the extent possible under law, the maintainers have waived all copyright and related or neighboring rights to this work. See [LICENSE](LICENSE).
