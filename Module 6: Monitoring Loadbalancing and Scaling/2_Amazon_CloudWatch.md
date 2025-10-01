# Amazon CloudWatch

## Core Concepts

### Metrics
- **Definition:** Time-ordered set of data points with timestamps
- **Default frequency:** Every 5 minutes (free)
- **Detailed monitoring:** Every 1 minute (paid feature)
- **Dimensions:** Name-value pairs for filtering (e.g., InstanceId)

### Custom Metrics
- **Purpose:** Application-level metrics not provided by default
- **Resolution:** Down to 1-second intervals
- **Examples:** Page views, error rates, load times, process counts

## CloudWatch Components

### Dashboards
- **Purpose:** Customizable visualization of metrics
- **Features:** Widgets, graphs, text displays
- **Scope:** Single or multi-region views
- **Access control:** IAM policies
- **Integration:** GetMetricData API for external tools

### CloudWatch Logs
- **Purpose:** Centralized log storage and analysis
- **Sources:** EC2, Lambda, applications, AWS services
- **Features:** Query, filter, metric filters
- **Configuration:** 
  - Lambda: Automatic with IAM permissions
  - EC2: Requires CloudWatch Logs agent

#### Log Organization
- **Log Events:** Individual log entries with timestamps
- **Log Streams:** Sequence of events from same source
- **Log Groups:** Collection of related log streams

### CloudWatch Alarms

#### Alarm Configuration
1. **Select metric** to monitor
2. **Define threshold** (e.g., CPU > 80%)
3. **Set time period** (e.g., sustained for 5 minutes)
4. **Configure actions** when alarm triggers

#### Alarm States
| State | Description |
|-------|-------------|
| **OK** | Metric within threshold |
| **ALARM** | Metric outside threshold |
| **INSUFFICIENT_DATA** | Not enough data to determine state |

#### Alarm Actions
- **EC2 actions:** Reboot, stop, terminate instances
- **Auto Scaling:** Scale up/down resources
- **SNS notifications:** Email, SMS alerts
- **Lambda functions:** Custom remediation logic

## Monitoring Workflow Example

### Employee Directory Application
1. **Set up metric filter** for HTTP 500 errors
2. **Define alarm** if errors sustained over time period
3. **Configure action** to send notification or auto-remediate
4. **Result:** Proactive issue detection and response

## Cost Considerations

### Free Tier
- Basic monitoring (5-minute intervals)
- Standard metrics from AWS services
- Basic dashboards

### Paid Features
- Detailed monitoring (1-minute intervals)
- Custom metrics
- High-resolution metrics
- Extended retention

## Integration Benefits

- **Unified monitoring** across all AWS services
- **Automated responses** to operational issues
- **Historical analysis** for capacity planning
- **Real-time alerting** for immediate action
- **Custom dashboards** for different stakeholders