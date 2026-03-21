# AI Automation Prompt Pack (15 Prompts)

> Prompts for automating repetitive tasks, building workflows, and extracting value from data.
> Replace `{placeholders}` with your own context before use.

---

## 1. Structured Data Extraction

```
Extract structured data from the following unstructured text.

Source text:
{paste_text — e.g., emails, invoices, resumes, product listings, legal documents}

Data type: {invoice_data/contact_info/product_specs/event_details/etc.}

Please:
1. Extract all relevant data points into a structured JSON format
2. Use consistent field names in snake_case
3. For any ambiguous or missing fields, use null and add a "confidence" field (high/medium/low)
4. Handle edge cases: multiple values for one field, inconsistent formatting, typos
5. Provide the schema definition so I can validate future extractions
6. If processing multiple items, return as a JSON array
7. Add a "_metadata" field with: extraction_date, source_type, items_found

Output format: {json/csv/markdown_table}

If this is a recurring task, also provide a system prompt I can use to automate this extraction.
```

---

## 2. Automated Report Generation

```
Generate a {report_type — e.g., "weekly sales", "monthly performance", "project status"} report from the following raw data.

Data:
{paste_data — tables, CSV, JSON, or describe the data source}

Report audience: {executives/team/clients}
Reporting period: {date_range}
Previous period data (for comparison): {paste_or_describe}

Please generate a report with:
1. Executive summary (3-5 bullet points, lead with the most important insight)
2. Key metrics dashboard (format as a table with: metric, current value, previous value, % change, status indicator)
3. Trend analysis — what's improving, declining, or anomalous
4. Top {number} performers and bottom {number} performers (with context)
5. Root cause analysis for any significant changes
6. Recommended actions based on the data (prioritized)
7. Risks or items requiring attention
8. Appendix with detailed data tables

Format the report in {markdown/html/plain_text} suitable for {email/pdf/presentation}.
```

---

## 3. Workflow Design & Automation Blueprint

```
Design an automated workflow for {process_description}.

Current manual process:
{describe_step_by_step_how_it's_done_now}

Pain points:
{what_takes_too_long/what_goes_wrong/what's_repetitive}

Tools available: {list — e.g., "Zapier, Google Sheets, Slack, email, CRM, etc."}
Budget for new tools: {budget}
Technical skill level: {non_technical/some_coding/developer}

Please provide:
1. Process map: Current state (manual) vs. Future state (automated)
2. Automation architecture — which tools handle which steps
3. Trigger events: what starts each automated action
4. Decision logic: any if/then branches in the workflow
5. Error handling: what happens when an automated step fails
6. Human-in-the-loop checkpoints (where a person should still review)
7. Implementation plan — step-by-step setup instructions
8. Testing strategy — how to verify the workflow works correctly
9. Estimated time savings per week/month
10. Maintenance requirements — what to check monthly
```

---

## 4. API Integration Script Generator

```
Generate a script to integrate {api_service_1} with {api_service_2}.

Use case: {describe_what_data_should_flow_between_them}
Direction: {one_way/bidirectional}
Trigger: {event_based/scheduled/manual}
Language: {python/javascript/etc.}

API 1 details:
- Authentication: {api_key/oauth/bearer}
- Base URL: {url}
- Relevant endpoints: {list_endpoints}
- Documentation: {doc_url}

API 2 details:
- Authentication: {api_key/oauth/bearer}
- Base URL: {url}
- Relevant endpoints: {list_endpoints}
- Documentation: {doc_url}

Please provide:
1. Complete working script with:
   - Authentication setup
   - Data fetching from source API (with pagination handling)
   - Data transformation/mapping between the two schemas
   - Writing to destination API (with batch/bulk support if available)
2. Error handling: retry logic, rate limit handling, logging
3. Configuration file (keep secrets separate from code)
4. Scheduling setup (cron expression or cloud scheduler config)
5. Monitoring: how to know if the sync is working or broken
6. README with setup instructions
```

---

## 5. Web Scraping Instruction Set

```
Create a web scraping solution for {target_website_or_type}.

Goal: Extract {what_data} from {how_many_pages — e.g., "all product listings", "first 100 search results"}.

Target URL pattern: {url_pattern}
Data points to extract per item:
{list_fields — e.g., "title, price, rating, description, image_url"}

Constraints:
- Respect robots.txt: {yes/no}
- Rate limiting: {requests_per_second}
- Authentication required: {yes/no}
- JavaScript rendering needed: {yes/no}

Please provide:
1. Technology recommendation: {beautifulsoup/scrapy/playwright/puppeteer} with justification
2. Complete scraping script in {language}
3. Anti-detection measures (headers, delays, rotation)
4. Data cleaning and validation logic
5. Output format: {csv/json/database}
6. Error handling: retries, broken pages, changed layouts
7. Scheduling for recurring scrapes
8. Diff detection — alert when the data structure changes
9. Legal and ethical considerations note
```

---

## 6. Data Cleaning & Transformation Pipeline

```
Design a data cleaning pipeline for my dataset.

Dataset description:
- Source: {where_the_data_comes_from}
- Format: {csv/json/excel/database}
- Size: {rows} rows x {columns} columns
- Sample data:
{paste_sample_rows}

Known data quality issues:
{list — e.g., "missing values in email column", "inconsistent date formats", "duplicate entries", "outliers in price field"}

Target output:
- Format: {desired_format}
- Schema: {desired_column_names_and_types}
- Destination: {database/file/api}

Please provide:
1. Data profiling summary: identify all issues (nulls, duplicates, format inconsistencies, outliers)
2. Cleaning rules for each issue, with justification for each decision
3. Complete transformation script in {python/sql/etc.} using {pandas/dbt/etc.}
4. Validation checks to run after cleaning (row count, null count, value ranges)
5. Logging: track what was changed, removed, or flagged
6. Before/after comparison report template
7. How to make this pipeline reusable for future data loads
```

---

## 7. Scheduling & Task Automation System

```
Design a task scheduling and automation system for {use_case — e.g., "content publishing", "report distribution", "data backups", "social media posting"}.

Tasks to automate:
{list_with_frequency — e.g.,
- "Generate weekly report" — every Monday 9am
- "Backup database" — daily at 2am
- "Post to social media" — 3x per day at optimal times
- "Check inventory levels" — every 4 hours
}

Infrastructure: {local_machine/cloud_server/serverless}
OS: {linux/macos/windows}
Budget: {budget}

Please provide:
1. Technology stack recommendation (cron, Airflow, cloud scheduler, n8n, etc.)
2. Complete configuration for each scheduled task
3. Dependency management — tasks that must run in order
4. Failure handling: retry policy, alerting, manual override
5. Logging and audit trail setup
6. Dashboard for monitoring task status
7. Notification setup: {email/slack/sms} alerts for failures and completions
8. Scaling plan: what happens when tasks take longer than expected
9. Complete setup instructions from scratch
```

---

## 8. Monitoring & Alerting Configuration

```
Set up a monitoring and alerting system for {what_to_monitor — e.g., "website uptime", "API health", "server resources", "application errors"}.

What to monitor:
{list_with_thresholds — e.g.,
- Website response time > 2 seconds
- Error rate > 1%
- CPU usage > 80% for 5 minutes
- Disk space < 20%
- SSL certificate expiry < 30 days
}

Current infrastructure: {describe}
Notification channels: {email/slack/pagerduty/sms}
Team structure: {who_gets_alerted_and_when}
Budget: {budget}

Please provide:
1. Tool recommendation: {uptime_robot/datadog/prometheus_grafana/custom}
2. Complete configuration for each monitor/alert
3. Alert severity levels (info/warning/critical) with escalation rules
4. On-call rotation setup
5. Incident response playbook template for the top 3 alert types
6. Silence/maintenance window configuration
7. Monthly health report automation
8. Setup instructions step by step
```

---

## 9. Email Processing & Classification Automation

```
Design an email processing automation system.

Volume: ~{number} emails per day to {email_address}
Current process: {describe_manual_process}

Email categories to detect:
{list — e.g.,
- Customer support request (subcategories: billing, technical, general)
- Sales inquiry
- Partnership proposal
- Spam / irrelevant
- Urgent / time-sensitive
}

For each category, the automated action should be:
{list_actions — e.g.,
- Support: create ticket in {tool}, auto-reply with acknowledgment
- Sales: forward to {team}, log in CRM
- Urgent: SMS alert to {person}
}

Please provide:
1. Classification logic (keyword-based rules + AI classification prompt)
2. System prompt for AI-powered email classification (with examples)
3. Auto-reply templates for each category
4. Routing rules and escalation logic
5. Tool/platform recommendation for implementation
6. Setup instructions
7. Accuracy monitoring: how to track and improve classification over time
8. Edge case handling: emails that fit multiple categories, unknown languages, attachments
```

---

## 10. Document Generation from Templates

```
Create a document generation system that produces {document_type — e.g., "invoices", "contracts", "proposals", "certificates"} from templates.

Template inputs (variables):
{list — e.g., "client_name, project_description, line_items[], total_amount, payment_terms, dates"}

Output format: {pdf/docx/html}
Volume: {number} documents per {day/week/month}
Brand requirements: {logo, colors, fonts}

Please provide:
1. Template design in {html/markdown/latex} with variable placeholders
2. Generation script in {language} that:
   - Accepts input data (JSON/CSV/form)
   - Validates all required fields
   - Populates the template
   - Generates the output file
   - Handles conditional sections (show/hide based on data)
3. Batch generation capability for multiple documents
4. Naming convention for output files
5. Storage and organization strategy
6. Email delivery integration (auto-send generated documents)
7. Version tracking and audit log
8. Sample input data and expected output
```

---

## 11. Social Media Auto-Posting Pipeline

```
Design an automated social media posting pipeline.

Platforms: {instagram/twitter/linkedin/facebook/tiktok}
Posting frequency: {posts_per_platform_per_day}
Content source: {manual_queue/rss_feed/ai_generated/repurposed}
Brand: {brand_name}

Requirements:
- Schedule posts in advance ({days/weeks} ahead)
- Optimal posting time per platform
- Platform-specific formatting (character limits, image sizes, hashtags)
- Analytics tracking (which posts perform best)

Please provide:
1. Architecture diagram (text-based) showing the full pipeline
2. Tool stack recommendation with cost estimate
3. Content queue format (spreadsheet/database schema)
4. Automation script/configuration for posting
5. Image/media handling workflow
6. Hashtag strategy automation
7. Engagement monitoring (auto-alerts for viral posts or negative sentiment)
8. Monthly analytics report automation
9. Content recycling logic (re-post evergreen content)
10. Complete setup guide
```

---

## 12. Log Analysis & Anomaly Detection

```
Create a log analysis and anomaly detection system for {system_description}.

Log source: {application_logs/server_logs/access_logs/etc.}
Log format:
{paste_sample_log_lines}

Volume: ~{number} log lines per {hour/day}
Current log storage: {file/elasticsearch/cloudwatch/etc.}

I want to detect:
{list — e.g.,
- Unusual spike in error rates
- New error types never seen before
- Suspicious access patterns (brute force, scraping)
- Performance degradation trends
- Failed deployment indicators
}

Please provide:
1. Log parsing configuration (regex patterns for each log format)
2. Key metrics to extract and track
3. Anomaly detection rules (statistical baselines + threshold alerts)
4. Pattern recognition for {specific_patterns}
5. Dashboard design with the most important views
6. Alert rules with appropriate thresholds to minimize false positives
7. Implementation in {python/elk_stack/cloudwatch/etc.}
8. Historical analysis query templates (for incident investigation)
9. Log retention and rotation policy recommendation
```

---

## 13. Batch File Processing Automation

```
Automate batch processing of {file_type — e.g., "images", "PDFs", "CSVs", "audio files", "videos"}.

Input: {number} {file_type} files in {input_location}
Processing needed:
{list_operations — e.g.,
- Resize images to 800x600
- Convert PNG to WebP
- Add watermark
- Rename with date prefix
- Extract metadata
- Compress
}

Output: {output_location}
Frequency: {one_time/daily/on_new_files}
Environment: {os}

Please provide:
1. Complete script in {language/bash} that:
   - Scans input directory for new files
   - Validates file type and integrity
   - Applies all processing steps in correct order
   - Handles errors per-file (don't stop on one bad file)
   - Moves processed files to output location
   - Creates a processing log/report
2. File watching setup for real-time processing of new files
3. Progress tracking for large batches
4. Duplicate detection
5. Rollback capability (keep originals until confirmed)
6. Performance optimization for large batches
7. Setup instructions and dependency installation
```

---

## 14. Database Backup & Recovery Automation

```
Design an automated database backup and recovery system.

Database: {postgres/mysql/mongodb/etc.} version {version}
Database size: {size}
Growth rate: ~{size} per month
Hosting: {self_hosted/rds/cloud_sql/atlas}
RPO (Recovery Point Objective): {max_acceptable_data_loss_time}
RTO (Recovery Time Objective): {max_acceptable_downtime}

Please provide:
1. Backup strategy: full + incremental schedule
2. Complete backup script with:
   - Automated full backup ({frequency})
   - Incremental/WAL backups ({frequency})
   - Compression and encryption
   - Upload to {s3/gcs/azure_blob} with lifecycle rules
3. Retention policy (daily for X days, weekly for X weeks, monthly for X months)
4. Backup verification: automated restore test script
5. Recovery procedure documentation (step-by-step)
6. Monitoring: alerts for failed backups, storage usage tracking
7. Cost estimation for storage
8. Disaster recovery: cross-region replication setup
9. Cron/scheduler configuration for all automated tasks
10. Runbook: "The database is down — here's exactly what to do"
```

---

## 15. AI-Powered Content Pipeline

```
Design an end-to-end AI-powered content creation and distribution pipeline.

Content type: {blog_posts/newsletters/social_media/product_descriptions}
Volume: {number} pieces per {day/week}
Topics/niche: {topic_area}
Brand voice: {describe_tone}
Distribution channels: {list_channels}

Pipeline stages to automate:
1. Topic research and ideation
2. Content generation with AI
3. Human review/editing
4. SEO optimization
5. Image/media creation
6. Publishing to {platforms}
7. Performance tracking

Please provide:
1. Pipeline architecture with tools for each stage
2. AI prompt templates for content generation (with quality guardrails)
3. Editorial workflow: AI draft > human review > approval > publish
4. Quality control checklist (automated where possible)
5. SEO optimization automation (meta tags, internal links, schema)
6. Image generation prompts or stock photo selection criteria
7. Publishing automation configuration per platform
8. Analytics dashboard: which content performs and why
9. Feedback loop: how performance data improves future content
10. Cost per content piece estimate (AI tokens + tools + human time)
```

---

*Part of the AI Prompt Engineering Pack v1.0.0*
*For professionals who want to automate the boring stuff and focus on what matters.*
