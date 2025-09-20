# Amazon EC2 Instance Lifecycle

## Instance States

### 1. Pending
- Instance is being set up (copying AMI, allocating network)
- **Billing:** Not charged

### 2. Running
- Instance is ready to use
- **Billing:** Charges begin

### 3. Rebooting
- Equivalent to OS reboot
- Keeps same IP addresses and instance store data
- **Billing:** Continues

### 4. Stopping/Stopped
- Similar to shutting down laptop
- Can only stop instances with EBS root volumes
- May move to different physical server on restart
- **Billing:** Compute charges stop, EBS storage charges continue

### 5. Stop-Hibernate
- Saves RAM contents to EBS root volume
- Faster startup than regular stop
- **Billing:** Same as stopped state

### 6. Terminated
- Instance stores erased, IP addresses lost
- Cannot access machine anymore
- **Billing:** All charges stop

## Key Differences

**Stop vs Stop-Hibernate:**
- **Stop:** RAM contents lost
- **Stop-Hibernate:** RAM saved to EBS, faster restart

**Reboot vs Stop/Start:**
- **Reboot:** Same physical server, keeps all addresses
- **Stop/Start:** May change physical server, keeps private IP

## EC2 Pricing Options

### On-Demand Instances
- **Cost:** Pay per hour/second
- **Commitment:** None
- **Best for:** Unpredictable workloads, testing, short-term use

### Spot Instances
- **Cost:** Up to 90% off On-Demand
- **Risk:** Can be interrupted when capacity needed
- **Best for:** Fault-tolerant, flexible timing workloads

### Savings Plans
- **Cost:** Up to 72% savings
- **Commitment:** 1-3 year usage commitment
- **Best for:** Consistent, predictable usage

### Reserved Instances
- **Cost:** Up to 72% off On-Demand
- **Types:** Standard, Convertible, Scheduled
- **Commitment:** 1-3 years
- **Best for:** Steady-state usage

### Dedicated Hosts
- **Cost:** Hourly or Reserved pricing (up to 70% off)
- **Use case:** License compliance, regulatory requirements
- **Benefit:** Use existing server-bound licenses