# Awesome Agentic FinOps [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> A curated, opinionated map of agentic and open-source tooling for cloud cost management (FinOps): MCP servers, AI cost agents and assistants, assistant skills, and the broader open-source FinOps ecosystem.

This list leads with the **agentic layer** (the tools that let you query, analyze, and act on cloud cost through an AI assistant) because that is the part the older FinOps lists do not cover, and keeps a complete map of the established open-source FinOps tooling underneath it.

Maintained by the team at [Costory](https://costory.io). Costory is a vendor and is tagged `vendor` in the list, the same as every other vendor, and its entry is held to the same bar. Additions, corrections, and removals (including of our own entry) are welcome by pull request or issue. See [Contributing](CONTRIBUTING.md) for the inclusion criteria.

## What is "agentic FinOps"?

A rough maturity ladder, useful for reading the list:

- **L0 - Dashboards.** You read charts and pull reports by hand.
- **L1 - Chat with your costs.** Ask questions in natural language and get answers (most MCP servers and assistants today).
- **L2 - The agent acts, with approval.** It creates alerts, reports, annotations, or tickets on your say-so.
- **L3 - Closed loop.** It proposes and executes changes (rightsizing, commitments) within guardrails.

Two capabilities separate the genuinely useful from the demo: whether a tool understands your **business context** (allocation, unit economics, virtual dimensions, not just raw service spend), and whether it can safely **act** rather than only answer. The comparison table notes both.

## Contents

- [Agentic FinOps](#agentic-finops)
  - [Comparison](#comparison)
  - [MCP servers](#mcp-servers)
  - [AI cost agents & assistants](#ai-cost-agents--assistants)
  - [Assistant skills & plugins](#assistant-skills--plugins)
  - [Evals & benchmarks](#evals--benchmarks)
- [The broader open-source FinOps ecosystem](#the-broader-open-source-finops-ecosystem)
  - [Kubernetes & container cost](#kubernetes--container-cost)
  - [Infrastructure as code cost](#infrastructure-as-code-cost)
  - [Multi-cloud platforms & scanners](#multi-cloud-platforms--scanners)
  - [AWS](#aws)
  - [Azure](#azure)
  - [GCP & other clouds](#gcp--other-clouds)
  - [Pricing data & calculators](#pricing-data--calculators)
  - [GreenOps & sustainability](#greenops--sustainability)
  - [Standards & foundations](#standards--foundations)
  - [Learning & reference](#learning--reference)
  - [Related lists](#related-lists)

## Agentic FinOps

### Comparison

Vendor tools and the most active open-source MCP servers, side by side. "Acts" means it can take an action (create an alert, report, or annotation) and not only answer. "Context" means it models allocation or unit economics, not just raw service spend.

| Tool | Kind | Cost sources | License | Delivery | Acts | Context | Note |
|------|------|--------------|---------|----------|------|---------|------|
| [Costory](https://docs.costory.io/features/mcp) `vendor` | Assistant + MCP | Multi (cloud, LLM, data platforms) | Commercial (15-day trial) | Hosted, OAuth | Yes (alerts, reports, dashboards) | Yes | Context layer: business metrics, unit economics, virtual dimensions. |
| [Vantage](https://www.vantage.sh) `vendor` | Agent + MCP | Multi (cloud + SaaS) | Commercial; MCP servers open source | Hosted + self-host MCP | Yes (agent buys SP/RI, human-in-loop) | Partial | FinOps Certified Platform; open-sourced local and remote MCP servers. |
| [CloudZero](https://www.cloudzero.com) `vendor` | Assistant + MCP | Multi (cloud + SaaS) | Commercial | Hosted | Chat | Yes | "Ask Advisor"; strong unit-cost / cost-per-customer focus. |
| [AWS FinOps Agent](https://aws.amazon.com/blogs/aws-cloud-financial-management/aws-finops-agent-is-now-public-preview/) `vendor` | Agent | AWS only | Free in preview (usage cap) | AWS console (us-east-1) | Yes (reports, Jira tickets) | Partial (context files) | Public preview June 2026. Root-causes anomalies via CloudTrail; no MCP; multi-account via management account. |
| [aws-cost-explorer-mcp-server](https://github.com/aarora79/aws-cost-explorer-mcp-server) | MCP | AWS | OSS (MIT) | Self-host | Read | No | Cost Explorer plus Bedrock invocation logs. |
| [aws-finops-mcp-server](https://github.com/ravikiranvm/aws-finops-mcp-server) | MCP | AWS | OSS (MIT) | Self-host | Read + audit | No | Cost analysis, waste audit, budgets across CLI profiles. |
| [AzurePricingMCP](https://github.com/msftnadavbh/AzurePricingMCP) | MCP | Azure | OSS (MIT) | Self-host | Read | No | Retail pricing, Spot and savings analysis, orphaned-resource detection. |
| [cloud-cost-mcp](https://github.com/jasonwilbur/cloud-cost-mcp) | MCP | AWS, Azure, GCP, OCI | OSS (Apache-2.0) | Self-host | Read | No | Multi-cloud price comparison from public APIs. |
| [aws-calculator-mcp](https://github.com/Musheer360/aws-calculator-mcp) | MCP | AWS | OSS (MIT) | Self-host | Read | No | Drives the AWS Pricing Calculator, no credentials. |

### MCP servers

Model Context Protocol servers that expose cloud cost data and actions to AI assistants.

- [aarora79/aws-cost-explorer-mcp-server](https://github.com/aarora79/aws-cost-explorer-mcp-server) - AWS spend via Cost Explorer plus Amazon Bedrock model-invocation logs. Good if you want cloud and LLM spend in one place.
- [ravikiranvm/aws-finops-mcp-server](https://github.com/ravikiranvm/aws-finops-mcp-server) - AWS cost analysis, waste audit, and budgets across CLI profiles; credentials stay local.
- [prashantgupta123/aws-finops-mcp-server](https://github.com/prashantgupta123/aws-finops-mcp-server) - AWS FinOps MCP packaged for the Amazon Bedrock AgentCore runtime.
- [msftnadavbh/AzurePricingMCP](https://github.com/msftnadavbh/AzurePricingMCP) - Azure retail pricing with Spot and savings analysis and orphaned-resource detection.
- [julianobarbosa/azure-finops-mcp-server](https://github.com/julianobarbosa/azure-finops-mcp-server) - Azure cost analysis, waste audit, and budgets over MCP.
- [chaandannn/finopsmcp](https://github.com/chaandannn/finopsmcp) - "nable", connects an assistant to AWS, Azure, GCP, and SaaS billing (such as Datadog) in plain English.
- [Musheer360/aws-calculator-mcp](https://github.com/Musheer360/aws-calculator-mcp) - Drives the AWS Pricing Calculator (436 services) via headless Chrome; no credentials required.
- [jasonwilbur/cloud-cost-mcp](https://github.com/jasonwilbur/cloud-cost-mcp) - Multi-cloud price comparison (AWS, Azure, GCP, OCI) from public pricing APIs.
- [ecos-labs/ecos](https://github.com/ecos-labs/ecos) - Open FinOps data stack with a CLI and an MCP server.
- [aws-samples/sample-cfm-tips-mcp](https://github.com/aws-samples/sample-cfm-tips-mcp) - MCP server built on AWS Cloud Financial Management playbooks.
- [Cloudaware MCP](https://docs.cloudaware.com/DOCS/cloudaware-mcp-overview) `vendor` - Connects assistants to the Cloudaware CMDB graph and BigQuery cost and usage exports via read-only SQL, joining infrastructure metadata with spend.
- [Zopnight](https://zop.dev/learn/mcp-server?utm_source=awesome-agentic-finops&utm_medium=listing&utm_campaign=mcp-directory) `vendor` - Hosted MCP server for cloud cost and infrastructure governance across AWS, Azure, and GCP: cost by provider, resource, tag, and team, budgets, rightsizing and idle-resource recommendations, plus Kubernetes and service diagnostics. Writes are off by default, behind an organisation-level permission tier.

### AI cost agents & assistants

Agents and copilots that analyze and act on cloud cost. Includes the commercial leaders for completeness (tagged `vendor`).

- [AWS FinOps Agent](https://aws.amazon.com/blogs/aws-cloud-financial-management/aws-finops-agent-is-now-public-preview/) `vendor` - AWS's own agent (public preview, June 2026): investigates anomalies to root cause via CloudTrail, answers cost questions, schedules reports, and files optimization recommendations as Jira tickets. AWS only, console-based, free during preview with a usage cap.
- [Vantage](https://www.vantage.sh) `vendor` - FinOps Agent that proactively finds savings and can execute commitment purchases with approval; ships open-source MCP servers.
- [CloudZero](https://www.cloudzero.com) `vendor` - "Ask Advisor" conversational assistant plus an MCP server; strong on unit cost and cost-per-customer.
- [Costory](https://costory.io) `vendor` - Assistant and hosted MCP on top of a context layer (business metrics, unit economics, virtual dimensions); ingests cloud (AWS, GCP, Azure) plus SaaS and AI spend (Snowflake, Datadog, Anthropic, Cursor, and more); runs in Claude, Cursor, VS Code, and Dust.
- [Atmoz](https://atmoz.co) `vendor` - Real-time cloud and AI efficiency platform; its Finius agent detects waste as it happens and pushes recommendations into Slack, Teams, and the IDE; read-only, with budgets, SSO, and RBAC.
- [NudgeBee](https://github.com/nudgebee/nudgebee) `vendor` - Self-hosted agent that detects idle resources, spend anomalies, and rightsizing opportunities across AWS, Azure, GCP, and Kubernetes, and applies fixes through approval-gated runbooks. For platform and FinOps teams that want the optimization running inside their own cluster.
- [MrigankJaiswal-hub/finops-Agent](https://github.com/MrigankJaiswal-hub/finops-Agent) - Open-source FinOps agent on AWS Bedrock with analyze, recommend, and execute steps.
- [danjamk/slack-aws-cost-guardian](https://github.com/danjamk/slack-aws-cost-guardian) - AI-driven AWS cost monitoring and anomaly alerts in Slack.

### Assistant skills & plugins

Skills and plugins that turn an AI coding assistant into a cost operator.

- [costory-io/costory-finops-mcp-skills](https://github.com/costory-io/costory-finops-mcp-skills) `vendor` - Claude Code / Codex marketplace plugin packaging five [FinOps skills](https://github.com/costory-io/costory-finops-mcp-skills#finops-skills) (query investigation, virtual dimensions, dashboards, reports/DIGEST, recipes) over the hosted [Costory MCP tools](https://github.com/costory-io/costory-finops-mcp-skills#mcp-tools-reference), plus a library of ready-made tracking recipes.
- [Aboudjem/aws-cost-audit-skill](https://github.com/Aboudjem/aws-cost-audit-skill) - Claude skill that audits an AWS bill; evidence-first, read-only, follows AWS Well-Architected and the FinOps Foundation framework.
- [mindaugasnakrosis/azure-costs-analyzer](https://github.com/mindaugasnakrosis/azure-costs-analyzer) - Claude Code skill for a read-only Azure cost review against Microsoft and FinOps Foundation rules.
- [prajapatimehul/claude-aws-cost-saver](https://github.com/prajapatimehul/claude-aws-cost-saver) - Claude Code and Codex plugin with 160+ AWS cost checks.
- [zxkane/aws-skills](https://github.com/zxkane/aws-skills) - Claude Code plugins for AWS including cost optimization, CDK, serverless, and Bedrock AgentCore.
- [shivamsriva31093/gcp-ironclad](https://github.com/shivamsriva31093/gcp-ironclad) - Claude Code skills plus a gcp-finops MCP for GCP API-key audit and safe spend hardening.
- [unfunco/claude-aws-billing-summary](https://github.com/unfunco/claude-aws-billing-summary) - GitHub Action that posts a Claude-generated monthly AWS billing summary.
- [OptimNow/cloud-finops-skills](https://github.com/OptimNow/cloud-finops-skills) - FOCUS-aligned FinOps knowledge skill and MCP for AI coding assistants.
- [OptimNow/finops-mcp-resources](https://github.com/OptimNow/finops-mcp-resources) - Curated MCP servers and resources for cloud FinOps practitioners.
- [Cletrics/finops-agents](https://github.com/Cletrics/finops-agents) - Collection of FinOps specialist agents for assistants.

### Evals & benchmarks

Emerging. There is not yet a credible, neutral public benchmark for FinOps assistants. If you are building one, open a PR.

## The broader open-source FinOps ecosystem

### Kubernetes & container cost

- [opencost/opencost](https://github.com/opencost/opencost) - CNCF project and spec for Kubernetes and cloud cost monitoring. The de facto open standard for K8s cost.
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

### Infrastructure as code cost

- [infracost/infracost](https://github.com/infracost/infracost) - Cloud cost estimates for Terraform in CI and pull requests. The category leader for shift-left cost.
- [cycloidio/terracost](https://github.com/cycloidio/terracost) - Terraform cost estimation library and CLI.
- [terrateamio/openinfraquote](https://github.com/terrateamio/openinfraquote) - Cost estimates from Terraform plans and state files.
- [TheCloudTheory/arm-estimator](https://github.com/TheCloudTheory/arm-estimator) - Azure cost estimates for ARM, Bicep, and Terraform.
- [revant-io/cdk-cost-limit](https://github.com/revant-io/cdk-cost-limit) - Cost-aware, self-limiting AWS CDK constructs.
- [rshade/finfocus](https://github.com/rshade/finfocus) - FinOps CLI for Pulumi: projected and actual spend, budgets.
- [alikzao/terraform-cost-guard](https://github.com/alikzao/terraform-cost-guard) - Detects idle AWS resources using CUR, Athena, and Grafana.

### Multi-cloud platforms & scanners

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

### AWS

- [alexcasalboni/aws-lambda-power-tuning](https://github.com/alexcasalboni/aws-lambda-power-tuning) - Step Functions state machine that finds the cost and performance sweet spot for Lambda functions, data-driven.
- [nilbuild/aws-cost-cli](https://github.com/nilbuild/aws-cost-cli) - AWS cost analysis in the terminal with a Slack summary.
- [mlevit/aws-auto-cleanup](https://github.com/mlevit/aws-auto-cleanup) - Deletes AWS resources by allowlist and time to live.
- [jcjorel/ec2-spot-converter](https://github.com/jcjorel/ec2-spot-converter) - Converts EC2 instances between On-Demand and Spot in place.
- [sqlxpert/lights-off-aws](https://github.com/sqlxpert/lights-off-aws) - Stops EC2 and RDS on a cron schedule via resource tags.
- [toricls/acos](https://github.com/toricls/acos) - Interactive CLI for AWS cost across an Organization.
- [c1982/awsdtc](https://github.com/c1982/awsdtc) - AWS data-transfer cost explorer, the cost nobody can otherwise explain.
- [jimzucker/aws-forecast](https://github.com/jimzucker/aws-forecast) - Reproduces the Cost Explorer forecast and posts it to Slack.
- [realadeel/CloudVac](https://github.com/realadeel/CloudVac) - Cleans up unused AWS resources across profiles and regions.
- [robsonbittencourt/aws-cost-miner](https://github.com/robsonbittencourt/aws-cost-miner) - Extracts useful information from the AWS billing report.
- [idvoretskyi/aws-s3-cost-explorer](https://github.com/idvoretskyi/aws-s3-cost-explorer) - Single-binary CLI for S3 storage costs and tiers.
- [turbot/steampipe-mod-aws-thrifty](https://github.com/turbot/steampipe-mod-aws-thrifty) - Checks AWS accounts for unused and under-used resources.
- [aws-solutions-library-samples/cloud-intelligence-dashboards-framework](https://github.com/aws-solutions-library-samples/cloud-intelligence-dashboards-framework) - Deploys the AWS Cloud Intelligence Dashboards.
- [sls-mentor/sls-mentor](https://github.com/sls-mentor/sls-mentor) - Audits serverless AWS apps across cost and other pillars.
- [trackit/trackit](https://github.com/trackit/trackit) - Tooling to understand and improve AWS usage.

### Azure

- [mivano/azure-cost-cli](https://github.com/mivano/azure-cost-cli) - CLI for Azure cost with daily cost, budgets, and anomaly detection; assistant-friendly output.
- [thgossler/AzSaveMoney](https://github.com/thgossler/AzSaveMoney) - Flags unused Azure resources for cleanup via tagging.
- [rowilson/azure-cost-management-pbit](https://github.com/rowilson/azure-cost-management-pbit) - Power BI template for Azure Cost Management.
- [microsoft/finops-toolkit](https://github.com/microsoft/finops-toolkit) - Microsoft tooling and FOCUS exports for Azure FinOps.

### GCP & other clouds

- [Cyclenerd/google-cloud-pricing-cost-calculator](https://github.com/Cyclenerd/google-cloud-pricing-cost-calculator) - GCP cost estimates from YAML files and a CLI.
- [Cyclenerd/poweroff-google-cloud-cap-billing](https://github.com/Cyclenerd/poweroff-google-cloud-cap-billing) - Caps GCP billing by automating shutdown.
- [doitintl/iris3](https://github.com/doitintl/iris3) - Automatic GCP resource labeling for cost allocation.
- [dennisklappe/cf-ledger](https://github.com/dennisklappe/cf-ledger) - Per-application Cloudflare cost attribution.

### Pricing data & calculators

- [vantage-sh/ec2instances.info](https://github.com/vantage-sh/ec2instances.info) - EC2 and related instance pricing comparison.
- [doitintl/gcpinstances.info](https://github.com/doitintl/gcpinstances.info) - GCP instance pricing comparison.
- [bytebase/dbcost](https://github.com/bytebase/dbcost) - Cloud database pricing comparison.
- [TUM-DIS/cloudspecs](https://github.com/TUM-DIS/cloudspecs) - Browser explorer for EC2 instances powered by DuckDB-WASM.

### GreenOps & sustainability

- [omrdev1/greenops-cli](https://github.com/omrdev1/greenops-cli) - Carbon-footprint linting for CI/CD pipelines.
- [vinayalodha/greenbot](https://github.com/vinayalodha/greenbot) - AWS cost optimization tool.

### Standards & foundations

- [FinOps-Open-Cost-and-Usage-Spec/FOCUS_Spec](https://github.com/FinOps-Open-Cost-and-Usage-Spec/FOCUS_Spec) - FOCUS, the open specification for billing and usage data. FOCUS 1.2+ supports non-monetary pricing units (such as tokens), the hook for AI-spend reporting.
- [finopsfoundation](https://github.com/finopsfoundation) - The FinOps Foundation framework, definitions, and KPIs. Note the distinction between "FinOps for AI" (managing AI and token spend) and "AI for FinOps" (agents doing FinOps work).
- [project-koku/koku](https://github.com/project-koku/koku) - Open cost management for hybrid cloud, from Red Hat.

### Learning & reference

- [kdeldycke/awesome-billing](https://github.com/kdeldycke/awesome-billing) - Billing and payments knowledge for cloud platforms.
- [ravsau/aws-cloud-cost-management](https://github.com/ravsau/aws-cloud-cost-management) - AWS cost optimization notes and a video playlist.
- [vantage-sh/handbook.vantage.sh](https://github.com/vantage-sh/handbook.vantage.sh) - The Cloud Cost Handbook, plain-English guides to cloud pricing.
- [ahmadalibagheri/finops-tutorial](https://github.com/ahmadalibagheri/finops-tutorial) - A FinOps tutorial series.

### Related lists

- [jmfontaine/awesome-finops](https://github.com/jmfontaine/awesome-finops) - The original Awesome FinOps list.
- [Funkmyster/awesome-cloud-cost-control](https://github.com/Funkmyster/awesome-cloud-cost-control) - Tools, blogs, podcasts, and standards for cloud cost control.
- [ElementTech/awesome-cloud-cost](https://github.com/ElementTech/awesome-cloud-cost) - Tips, tricks, and hacks for saving cloud cost.
- [lcenchew/awesome-aws-cost-management](https://github.com/lcenchew/awesome-aws-cost-management) - Resources for managing AWS cost.
- [OptimNow/finops-mcp-resources](https://github.com/OptimNow/finops-mcp-resources) - A focused list of MCP servers and resources for FinOps.

## Contributing

Contributions are welcome, including from vendors and competitors, under the same rules. Read the [contribution guidelines](CONTRIBUTING.md): inclusion criteria, the `vendor` disclosure tag, and the annotation style (factual, no negative editorializing).

## License

[![CC0](https://licensebuttons.net/p/zero/1.0/88x31.png)](LICENSE)

To the extent possible under law, the maintainers have waived all copyright and related or neighboring rights to this work. See [LICENSE](LICENSE).
