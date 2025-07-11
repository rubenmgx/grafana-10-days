# Grafana in 10 days

## Tools You'll Need:
* A computer with Docker installed (simplifies setup for Grafana, Prometheus, Loki).
* Internet connection for tutorials and documentation.
* A code editor (VS Code, Sublime Text, etc.).

---------

## Day 1: Introduction to Observability & Grafana Fundamentals
Goal: Understand what Grafana is, its role in observability, and get a basic Grafana instance running.
* Topics:
    * What is Observability (Metrics, Logs, Traces)?
    * What is Grafana? Why is it used?
    * Grafana architecture overview (Frontend, Backend, Data Sources, Panels, Dashboards).
    * Installation of Grafana (Docker recommended for quick start).
    * Initial login and understanding the UI.
    * Adding a basic data source (e.g., the built-in "TestData" data source).
    * Creating your first simple dashboard and adding a basic panel.
* Links:
    * Grafana Labs "What is Grafana?": https://grafana.com/docs/grafana/latest/introduction/
    * Grafana Installation (choose Docker): https://grafana.com/docs/grafana/latest/setup-grafana/installation/ (Look for Docker instructions)
    * Grafana Fundamentals - Getting Started: https://grafana.com/tutorials/grafana-fundamentals/ (Focus on "Understanding the Grafana UI" and "Create a dashboard")
    * TestData data source tutorial: https://grafana.com/docs/grafgrafana/latest/datasources/testdata/
* Test Cases (Day 1):
    * Successfully install Grafana and log in.
    * Add the "TestData" data source.
    * Create a new dashboard.
    * Add a "Time series" panel using "TestData" and choose a scenario like "Fluctuating Value" or "Sine Wave".
    * Adjust the time range (e.g., "Last 1 hour").
    * Save your dashboard.

---------

## Day 2: Data Sources - Metrics with Prometheus
Goal: Understand metric data, set up Prometheus, and connect Grafana to Prometheus to visualize real metrics.
* Topics:
    * Introduction to Metrics and Time-Series Databases.
    * Prometheus basics: what it is, how it collects data (scraping).
    * Installing Prometheus and Node Exporter (via Docker Compose for simplicity).
    * Adding Prometheus as a data source in Grafana.
    * Basic PromQL (Prometheus Query Language) - up, node_cpu_seconds_total, rate(), sum().
    * Building a dashboard with Prometheus metrics (CPU, Memory, Disk Usage).
* Links:
    * How to Set Up Grafana with Prometheus? Step-by-Step Guide: https://www.cherryservers.com/blog/set-up-grafana-with-prometheus (Focus on "Install Prometheus", "Configure Prometheus", "Install Node Exporter", "Add Node Exporter to Prometheus", "Set up Grafana and connect to Prometheus").
    * Prometheus Querying Basics (PromQL): https://prometheus.io/docs/prometheus/latest/querying/basics/
    * Grafana Prometheus Data Source: https://grafana.com/docs/grafana/latest/datasources/prometheus/
* Test Cases (Day 2):
    * Successfully install Prometheus and Node Exporter.
    * Add Prometheus as a data source in Grafana.
    * Create a new dashboard named "Server Metrics".
    * Add a panel showing up metric for your Node Exporter.
    * Add a panel showing CPU utilization (e.g., 100 - (avg by (instance) (rate(node_cpu_seconds_total{mode="idle"}[5m])) * 100)).
    * Add a panel showing memory usage.
    * Generate some load (e.g., run stress-ng or a script to consume CPU/memory) and observe the graphs reacting.

---------

### Day 3: Data Sources - Logs with Loki
Goal: Understand log data, set up Loki, and connect Grafana to Loki to visualize and query logs.
* Topics:
    * Introduction to Logs and Log Aggregation.
    * Loki basics: what it is, how it collects logs (LogQL).
    * Installing Loki (via Docker Compose for simplicity, e.g., with Grafana Alloy/Promtail).
    * Adding Loki as a data source in Grafana.
    * Basic LogQL (Loki Query Language) - label selectors, filters (|=, !=).
    * Building dashboards with Loki logs.
    * Using the "Explore" feature for ad-hoc log querying.
* Links:
    * Loki Tutorial (Quick Start): https://grafana.com/docs/loki/latest/get-started/quick-start/tutorial/ (Focus on setting up the Loki stack and querying logs).
    * Grafana Loki Data Source: https://grafana.com/docs/grafana/latest/datasources/loki/
* Test Cases (Day 3):
    * Successfully install Loki and a log collector (e.g., Grafana Alloy/Promtail) alongside Grafana.
    * Add Loki as a data source.
    * Use the "Explore" tab to query logs from one of your running containers (e.g., Grafana or Loki containers).
    * Filter logs by severity (e.g., level="error").
    * Create a dashboard panel that shows the count of "error" logs over time.

---------

### Day 4: Data Sources - Traces with Tempo
Goal: Understand trace data, set up Tempo, and connect Grafana to Tempo to visualize distributed traces.
* Topics:
    * Introduction to Traces and Distributed Tracing.
    * Tempo basics: what it is, how it stores traces.
    * Setting up a simple application that emits OpenTelemetry traces and sends them to Tempo (Docker Compose examples are available).
    * Adding Tempo as a data source in Grafana.
    * Exploring traces in Grafana, linking metrics, logs, and traces.
* Links:
    * Intro to distributed tracing with Tempo, OpenTelemetry, and Grafana Cloud (concepts are transferable to self-hosted): https://grafana.com/blog/2024/05/28/full-stack-observability-with-grafana-prometheus-loki-tempo-and-opentelemetry/ (Focus on Tempo concepts).
    * Grafana Tempo Data Source: https://grafana.com/docs/grafana/latest/datasources/tempo/
    * OpenTelemetry Demo (can be complex, start with a simple app): Look for simpler examples of sending traces to Tempo. A quick search for "Tempo OpenTelemetry Docker Compose example" should yield good results.
* Test Cases (Day 4):
    * Successfully set up Tempo and a simple application sending traces to it.
    * Add Tempo as a data source in Grafana.
    * Use the "Explore" tab to query traces.
    * Identify a trace, click into it, and understand the span hierarchy.
    * (Optional but recommended): Integrate traces with a metric panel (e.g., click a spike in latency and see relevant traces).

---------

##Day 5: Dashboard Design & Visualization
Goal: Master various visualization types, panel options, and effective dashboard design principles.
* Topics:
    * Panel types: Time Series, Stat, Gauge, Bar Chart, Table, Heatmap, etc.
    * Panel Editor: Query tab, Transform tab, Visualize tab.
    * Transformations: Join, Reduce, Organize Fields, Labels to Fields.
    * Overrides: Customize individual series or fields.
    * Dashboard variables (query, custom, textbox, constant).
    * Annotations: Marking events on graphs.
    * Dashboard organization: Rows, Folders.
    * Best practices for dashboard design (readability, actionability).
* Links:
    * Grafana Data Visualization Tutorial: https://grafana.com/blog/2025/02/05/how-to-visualize-csv-data-with-grafana/ (Focus on visualization principles)
    * Grafana Panels and Visualizations: https://grafana.com/docs/grafana/latest/panels-visualizations/
    * Grafana Transformations: https://grafana.com/docs/grafana/latest/panels-visualizations/transformations/
    * Grafana Variables Tutorial: https://www.swiftorial.com/tutorials/performance_monitoring/grafana/templates/creating_templates (Covers templating/variables)
    * Grafana Annotations: https://grafana.com/docs/grafana/latest/dashboards/annotations/
* Test Cases (Day 5):
    * For your "Server Metrics" dashboard:
        * Change CPU utilization to a "Gauge" panel.
        * Add a "Stat" panel showing current memory usage.
        * Create a variable for instance (e.g., label_values(up, instance) for Prometheus) and use it to filter panels.
        * Add a manual annotation to one of your graphs.
        * Experiment with a "Table" panel showing raw data from a Prometheus query.

---------

## Day 6: Grafana Alerting
Goal: Learn how to create and manage alerts in Grafana, configure notification channels, and understand alert states.
* Topics:
    * Introduction to Grafana Alerting (unified alerting).
    * Alert rules: conditions, evaluation, folders, labels.
    * Contact points: Email, Slack, Webhooks, PagerDuty, etc.
    * Notification policies: Routing alerts, grouping, silences.
    * Testing alert rules.
    * Best practices for alerting (avoiding alert fatigue).
* Links:
    * Get started with Grafana Alerting: https://grafana.com/tutorials/alerting-get-started-pt1/ (This is a multi-part series, go through all of them).
    * Grafana Alerting: Advanced Alerting Configurations & Best Practices: https://drdroid.io/engineering-tools/grafana-alerting-advanced-alerting-configurations-best-practices (Good for best practices and testing alerts).
    * Grafana Notification Channels: https://grafana.com/docs/grafana/latest/alerting/set-up/contact-points/
* Test Cases (Day 6):
    * Configure an Email or Slack contact point (use a test webhook site if you don't want to use real email/Slack).
    * Create an alert rule for your Prometheus CPU utilization metric: "If CPU > 80% for 1 minute, fire an alert."
    * Generate CPU load to trigger the alert and verify the notification.
    * Create a notification policy to route specific alerts (e.g., based on a label).
    * Silence an alert.

---------

## Day 7: User Management & Security
Goal: Understand user roles, permissions, and basic security best practices for Grafana.
* Topics:
    * Grafana users, roles (Viewer, Editor, Admin), organizations.
    * Teams and permissions for dashboards/folders.
    * Authentication methods (basic, LDAP, OAuth, SAML).
    * API keys for programmatic access.
    * Security hardening for Grafana instance (HTTPS, cookie settings, hiding version).
    * Provisioning dashboards and data sources (configuration as code).
* Links:
    * Grafana User Management: https://grafana.com/docs/grafana/latest/administration/user-management/
    * Configuring Grafana Authentication: https://grafana.com/docs/grafana/latest/setup-grafana/configure-security/configure-authentication/
    * Grafana API Keys: https://grafana.com/docs/grafana/latest/administration/api-keys/
    * Configure security hardening | Grafana documentation: https://grafana.com/docs/grafana/latest/setup-grafana/configure-security/configure-security-hardening/
    * Provision dashboards and data sources: https://grafana.com/docs/grafana/latest/administration/provisioning/
* Test Cases (Day 7):
    * Create a new user with "Viewer" role and log in as them to verify read-only access.
    * Create a new team.
    * Give the new team view access to your "Server Metrics" dashboard.
    * (Optional): Experiment with creating an API key and using curl to query a dashboard or data source.
    * Review the grafana.ini configuration file for security settings.

---------

## Day 8: Advanced Querying & Transformations
Goal: Deepen your understanding of query languages (PromQL, LogQL), advanced transformations, and cross-data source queries.
* Topics:
    * Advanced PromQL: Aggregation operators (avg by, sum by), joins, functions (irate, histogram_quantile).
    * Advanced LogQL: Log parsing (JSON, Regex), metric extractions (line_format, label_format, log_metric_extractor).
    * Combining data: Mixed data sources, transformations for merging data.
    * Ad-hoc filters and link settings.
* Links:
    * Prometheus Query Editor Reference: https://grafana.com/docs/grafana/latest/datasources/prometheus/query-editor/
    * LogQL Cheatsheet: https://grafana.com/docs/loki/latest/reference/logql/
    * Grafana Transform data: https://grafana.com/docs/grafana/latest/panels-visualizations/transformations/
    * How to use PromQL joins for more effective queries: https://grafana.com/blog/2024/05/10/how-to-use-promql-joins-for-more-effective-queries/
* Test Cases (Day 8):
    * Create a new panel that shows the 95th percentile of HTTP request duration from a Prometheus metric (if you have one, otherwise simulate with TestData).
    * For your Loki data, extract a specific field (e.g., response time from an access log line) and create a time series graph of it using LogQL.
    * Create a dashboard using "Mixed" data sources. For example, show CPU usage from Prometheus and error logs from Loki on the same graph, perhaps with annotations from the logs.
    * Experiment with different transformations (e.g., Group by on your table panel).

---------

## Day 9: Integrating with Other Data Sources & Ecosystem
Goal: Explore other popular data sources and understand Grafana's broader ecosystem.
* Topics:
    * SQL databases (PostgreSQL, MySQL) as data sources.
    * Cloud monitoring services (AWS CloudWatch, Azure Monitor, Google Cloud Monitoring) - understand how to connect.
    * Importing pre-built dashboards from Grafana.com/dashboards.
    * Grafana plugins (data sources, panels, apps).
    * Introduction to Grafana Cloud (managed Grafana).
    * Grafana's role in a larger observability stack.
* Links:
    * Grafana Data Sources (browse common ones): https://grafana.com/docs/grafana/latest/datasources/
    * Grafana Dashboard Gallery: https://grafana.com/grafana/dashboards/ (Practice importing one).
    * Grafana Plugins: https://grafana.com/grafana/plugins/
    * Grafana Cloud: https://grafana.com/grafana/cloud/
* Test Cases (Day 9):
    * Find a popular dashboard on Grafana.com (e.g., for Node Exporter, if you're using it) and import it. Explore how it's built.
    * (Optional, requires a database): Set up a PostgreSQL or MySQL database (can be local Docker container) and add it as a data source. Query some simple data from it.
    * (Optional, if you have an AWS account): Set up the CloudWatch data source and create a simple panel showing an EC2 metric.

---------

##Day 10: Advanced Topics, Troubleshooting & Best Practices
Goal: Review, refine, and understand advanced concepts like performance, best practices, and troubleshooting.
* Topics:
    * Dashboard performance optimization (efficient queries, proper use of variables).
    * Troubleshooting Grafana issues (logs, data source connection errors).
    * Dashboards as Code (using JSON model directly or tools like Grafonnet/Terraform).
    * Best practices for production Grafana deployments (scaling, backups).
    * Reviewing key concepts: Observability pillars, Grafana features.
    * Planning for your own monitoring needs.
* Links:
    * Troubleshooting Grafana: https://grafana.com/docs/grafana/latest/troubleshooting/
    * Grafana Provisioning (revisit and understand json for dashboards): https://grafana.com/docs/grafana/latest/administration/provisioning/
    * Grafana High Availability (conceptual): https://grafana.com/docs/grafana/latest/setup-grafana/cluster-grafana/
    * Official Grafana Blog/Webinars: Explore recent updates and advanced use cases.
* Test Cases (Day 10):
    * Identify a panel in one of your dashboards that might be slow to load. Try to optimize its query or apply transformations.
    * Simulate a data source going down and observe Grafana's behavior.
    * Export one of your dashboards as JSON. Modify the JSON slightly (e.g., change a panel title) and try to re-import it.
    * Reflect on a real-world scenario you'd want to monitor and outline the Grafana dashboards and alerts you would create.
