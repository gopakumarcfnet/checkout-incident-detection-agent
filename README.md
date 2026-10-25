Checkout Incident Detection & Automated Triage

Event-Driven Workflow Automation | n8n | JavaScript | Google Sheets | Webhooks

A workflow automation project designed to monitor e-commerce checkout failure events, classify incident severity, generate alerts, and maintain processing checkpoints.

The solution demonstrates practical applications of workflow orchestration, incident management, data integration, and operational automation.



Business Problem

E-commerce checkout failures can affect customer experience, revenue conversion, and operational reliability.

Engineering and operations teams need a consistent way to identify potentially significant checkout incidents, distinguish higher-priority failures from routine events, and notify downstream systems.

Solution Overview

Built an event-driven automation workflow using n8n, JavaScript, Google Sheets, and HTTP webhooks.

The workflow:

Executes automatically every 15 minutes or through a manual trigger.

Reads checkout event records and configurable baseline metrics.

Processes events newer than the last recorded checkpoint.

Evaluates incidents using predefined severity rules.

Generates HIGH / ALERT or LOW / LOG commands.

Writes decisions to a Google Sheets audit log.

Sends structured commands to a downstream webhook.

Updates processing state after successful webhook execution.

System Architecture

Schedule / Manual Trigger → Read State → Read Baseline Metrics → Read Cart Events → Evaluate Events → Log Command → Send Webhook → Update State

For additional technical details, see Architecture Documentation.

Technology Stack

Technology

Purpose

n8n

Workflow orchestration and scheduling

JavaScript

Event filtering and severity evaluation

Google Sheets

Event data, baselines, audit log, and processing state

HTTP Webhook

Downstream command integration

JSON

Structured incident command payloads

GitHub

Source control and technical documentation

Incident Classification

The workflow evaluates new checkout events against rules including:

Payment-stage failures.

High-value carts with values of 500 or more.

Checkout-step event proportions exceeding configured baselines.

Multiple mobile-device failures.

If any high-severity condition is met, the workflow generates a HIGH / ALERT command. Otherwise, it generates a LOW / LOG command.

Technical note: The current baseline comparison uses the proportion of new failure events at each checkout step, rather than a true failure rate based on all checkout attempts. A production implementation would require both failed and total attempts over a defined time window.

Workflow Demonstration



The workflow is organized into two logical stages:

1. Incident Triage

Reads processing state, baseline metrics, and new checkout events, then evaluates the events using JavaScript.

2. Command Publishing

Writes the incident command, sends the webhook payload, and advances the processing checkpoint.

Repository Structure

workflows/ — Sanitized n8n workflow template.

sample-data/ — Synthetic checkout events, baselines, state, and command-log templates.

docs/ — Architecture documentation and implementation limitations.

screenshots/ — Workflow visualization.

How to Run

Install or access an n8n instance.

Import the workflow JSON from workflows/.

Create a Google Sheet containing the four required tabs: cart_events, baseline_metrics, state, and agent_commands.

Configure your own Google Sheets OAuth credentials.

Replace placeholder spreadsheet identifiers and the webhook destination.

Run the workflow manually using synthetic sample data.

Validate the output before enabling scheduled execution.

Engineering Considerations

The implementation includes timestamp-based incremental processing and structured command generation.

Future production improvements include:

Event-level deduplication and idempotency.

Retry handling for failed webhook deliveries.

Monitoring and failure notifications.

More accurate checkout failure-rate calculations.

Concurrency controls and recovery from partial failures.

A public interactive demo interface.

Planned Agentic AI Enhancements

The current implementation is rule-based workflow automation, not an autonomous LLM agent.

Planned enhancements include an AI-assisted incident analysis component that can:

Summarize incident patterns.

Retrieve relevant historical metrics.

Recommend possible root causes.

Suggest remediation actions.

Generate stakeholder-ready incident summaries.

Severity classification and operational actions will remain governed by explicit rules and appropriate approval controls.

Skills Demonstrated

Workflow Automation | JavaScript | Systems Integration | Webhooks | Incident Triage | Data Processing | Operational Monitoring | State Management | Technical Program Management

Project Status

Portfolio demonstration — workflow template and documentation available.

The repository does not currently provide a hosted interactive demo or independently verified production performance metrics.
