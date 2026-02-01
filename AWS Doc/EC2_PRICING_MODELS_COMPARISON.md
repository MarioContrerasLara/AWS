# EC2 Instance Pricing Models - Comprehensive Comparison

## Quick Reference Table

| Pricing Model | Cost per Hour | Commitment | Flexibility | Best For | Reliability |
|---|---|---|---|---|---|
| **On-Demand** | $1.00 | None | Maximum | Testing, variable workloads | High ✓ |
| **Spot** | $0.10 (90% off) | None | Maximum | Batch jobs, flexible timing | Low (can interrupt) |
| **Reserved (Standard)** | $0.50 (50% off) | 1-3 years | Minimum | Steady-state, predictable | High ✓ |
| **Reserved (Convertible)** | $0.54 (46% off) | 1-3 years | Moderate | Predictable with some flexibility | High ✓ |
| **Savings Plans (Compute)** | $0.28 (72% off) | 1-3 years | Maximum | Predictable long-term workloads | High ✓ |
| **Savings Plans (EC2 Instance)** | $0.36 (64% off) | 1-3 years | Moderate | Instance family consistency | High ✓ |
| **Dedicated Instances** | $2.00 | Hourly | High | Compliance, licensing | High ✓ |
| **Dedicated Hosts** | Variable | Monthly | Varies | Software licensing, compliance | High ✓ |

---

## Detailed Comparison

### 1. ON-DEMAND INSTANCES

**Overview:**
The most flexible pricing model with no long-term commitment. Pay per second (minimum 1 minute) or per hour.

```
Pricing: $1.00/hour per instance
Commitment: None
Upfront Cost: $0
Minimum Contract: None
Flexibility: Maximum
```

**Characteristics:**
```
✓ Start and stop anytime
✓ Pay only for running hours
✓ No long-term contracts
✓ Most expensive option
✓ Instant availability
✓ Perfect for unpredictable workloads
✓ Suitable for testing/development
✗ Higher hourly rate
✗ No cost savings
```

**Use Cases:**
```
1. Development & Testing
   └─ Quick environment setup
   └─ May use 1-2 hours only

2. Short-term Projects
   └─ Project runs for weeks
   └─ Then completely terminates

3. Variable Workloads
   └─ Traffic spikes unpredictably
   └─ Need to scale quickly

4. First-time Users
   └─ Learning AWS
   └─ Testing applications

5. Temporary Needs
   └─ One-time data processing
   └─ Temporary analytics
```

**Cost Example (1 year, 1 instance):**
```
Continuous (24/7):        $8,760/year
Peak hours only (8h/day):  $2,920/year
```

**Pros:**
- ✓ No commitment
- ✓ Instant availability
- ✓ Perfect flexibility
- ✓ Easy to start
- ✓ No penalty for stopping

**Cons:**
- ✗ Highest hourly cost
- ✗ No discounts
- ✗ Expensive for 24/7 workloads
- ✗ Not cost-effective long-term

---

### 2. SPOT INSTANCES

**Overview:**
Deeply discounted EC2 instances that AWS can interrupt with 2-minute notice. Great for non-critical workloads.

```
Pricing: $0.10/hour (90% discount)
Commitment: None
Upfront Cost: $0
Minimum Contract: None
Flexibility: Maximum
Interruption Risk: High
```

**Characteristics:**
```
✓ 90% discount on-demand price
✓ No upfront payment
✓ No long-term commitment
✓ Can be interrupted anytime (2-min notice)
✓ Available only when spare capacity exists
✓ Prices fluctuate based on supply/demand
✗ Unreliable for critical workloads
✗ Can lose instances without warning
✗ Availability varies by region/AZ
```

**How Spot Works:**
```
Step 1: AWS has spare capacity
Step 2: Offers excess capacity at discount
Step 3: You bid for instances
Step 4: If capacity needed, instances terminated
Step 5: 2-minute warning before termination
Step 6: Instance disappears
```

**Use Cases:**
```
1. Batch Processing
   ├─ Image thumbnail creation
   ├─ Log analysis
   ├─ Data transformations
   └─ Can resume on next instance

2. Machine Learning Training
   ├─ Non-production training
   ├─ Checkpoints for recovery
   └─ Can restart from checkpoint

3. Big Data Processing
   ├─ Hadoop/Spark jobs
   ├─ Can re-run lost work
   └─ Embarrassingly parallel tasks

4. Development/Testing
   ├─ Non-critical testing
   ├─ Performance testing
   └─ Cost-effective testing

5. Non-Critical Web Services
   ├─ Development environments
   ├─ Staging servers
   ├─ Non-public facing services
   └─ Background workers

NOT For:
✗ Production applications
✗ Customer-facing services
✗ Databases
✗ Any time-sensitive work
✗ Real-time processing
```

**Cost Example (1 year):**
```
Spot Instance:     $876/year
On-Demand:         $8,760/year
Savings:           $7,884 (90%)
```

**Pros:**
- ✓ 90% cost savings
- ✓ No commitment
- ✓ Great for batch jobs
- ✓ Fast deployment
- ✓ Can scale to 1000s of instances

**Cons:**
- ✗ Can be interrupted anytime
- ✗ 2-minute termination notice
- ✗ Not reliable for production
- ✗ Prices fluctuate
- ✗ Limited availability
- ✗ Application must handle interruption

---

### 3. RESERVED INSTANCES (STANDARD)

**Overview:**
One or three-year commitment for significant savings. You're reserved a specific instance type in a specific region.

```
Pricing: $0.50/hour (50% discount)
Commitment: 1 or 3 years
Upfront Cost: Partial or full payment
Minimum Contract: 1-3 years
Flexibility: Minimum (locked configuration)
```

**Characteristics:**
```
✓ 50% discount vs On-Demand
✓ 3-year option for deeper discount
✓ Can pay: All upfront, partial, or hourly
✓ High reliability (no interruption)
✗ Locked to specific instance type
✗ Locked to specific region
✗ Locked to specific OS
✗ Locked to specific tenancy
✗ 1-3 year commitment
✗ Can be expensive if usage changes
```

**Payment Options:**
```
All Upfront (AURI):
├─ Pay entire cost upfront
├─ Largest discount (72%)
└─ Best for: Committed budgets

Partial Upfront (PURI):
├─ Pay ~50% upfront
├─ Remaining as hourly charges
├─ Moderate discount (60%)
└─ Best for: Mixed payment approach

No Upfront (NURI):
├─ No upfront payment
├─ Pay hourly for commitment period
├─ Smaller discount (50%)
└─ Best for: Cash flow constraints
```

**Use Cases:**
```
1. 24/7 Web Applications
   ├─ E-commerce sites
   ├─ Content management systems
   ├─ Always-on services

2. Databases
   ├─ Database servers
   ├─ Always running
   ├─ Consistent workload

3. Steady-State Applications
   ├─ Known, predictable usage
   ├─ Minimal fluctuations
   ├─ Long-term deployment

4. Production Environments
   ├─ Mission-critical systems
   ├─ Stable, predictable load
   └─ 24/7 availability required
```

**Example: 3-Year t3.medium in us-east-1**
```
All Upfront:    $1,188 (3-year) = $0.45/hour
Partial:        $684 upfront + $0.22/hour
No Upfront:     $0.60/hour × 26,280 hours

On-Demand:      $0.83/hour (vs $0.45 with RI)
Savings:        55% annually
```

**Pros:**
- ✓ 50% savings (50% with all upfront)
- ✓ No interruption risk
- ✓ Flexible payment options
- ✓ 3-year option for more savings
- ✓ Can modify instance family (limited)
- ✓ Can sell unused RIs on marketplace

**Cons:**
- ✗ Locked to specific instance type
- ✗ Locked to specific region
- ✗ Locked to specific OS (Linux/Windows)
- ✗ Long-term commitment
- ✗ No refunds if you change mind
- ✗ Cost if needs change

---

### 4. RESERVED INSTANCES (CONVERTIBLE)

**Overview:**
Like Standard RIs but with flexibility to change instance families. Costs slightly more but offers more flexibility.

```
Pricing: $0.54/hour (46% discount)
Commitment: 1 or 3 years
Upfront Cost: Similar to Standard RI
Minimum Contract: 1-3 years
Flexibility: Moderate
```

**Characteristics:**
```
✓ Can convert to different instance families
✓ Can change instance sizes
✓ Can change regions
✓ Can change OS (limited)
✓ 46% discount
✓ Same reliability as Standard RI
✗ Slightly higher cost than Standard RI
✗ Still some commitment
```

**Convertible Features:**
```
CAN CHANGE:
✓ Instance family (t3 → m5 → c5)
✓ Instance size (large → xlarge)
✓ Region (us-east-1 → eu-west-1)
✓ Tenancy (default → dedicated)

CANNOT CHANGE:
✗ Operating system (easily)

RESTRICTIONS:
├─ Can only exchange UP in value
│  └─ Example: t3.large → m5.xlarge (OK)
│  └─ Example: m5.xlarge → t3.large (NOT allowed)
└─ Exchange fee applies
```

**Use Cases:**
```
1. Evolving Applications
   ├─ Application needs change over time
   ├─ Might need larger instances later
   └─ Want flexibility to scale up

2. Uncertain Long-term Needs
   ├─ Expect workload to grow
   ├─ Don't know final instance size
   └─ Want option to upgrade

3. Development Environment
   ├─ May need to test different types
   ├─ Want commitment discount
   └─ Need flexibility
```

**Example Comparison: Standard vs Convertible**
```
Standard RI (t3.large, 1-year):
├─ Cost: $360 all upfront
├─ Hourly: $0.41
├─ Can't change instance family
└─ Best: Know exact needs

Convertible RI (t3.large → m5.xlarge, 1-year):
├─ Cost: $420 all upfront
├─ Hourly: $0.48
├─ Can upgrade to any family
└─ Best: Uncertain future needs

Difference: $60/year for flexibility
```

**Pros:**
- ✓ 46% savings
- ✓ Flexibility across families
- ✓ Can modify to suit changes
- ✓ Still solid discount
- ✓ Marketplace resale possible

**Cons:**
- ✗ More expensive than Standard RI
- ✗ Still requires commitment
- ✗ Exchange restrictions (only up in value)
- ✗ Still regional (can't move freely)

---

### 5. SAVINGS PLANS (COMPUTE SAVINGS PLAN)

**Overview:**
Flexible pricing commitment for compute services (EC2, Fargate, Lambda). Provides maximum flexibility with strong discounts.

```
Pricing: $0.28/hour (72% discount)
Commitment: 1 or 3 years
Upfront Cost: Optional
Minimum Contract: 1-3 years
Flexibility: Maximum
Services: EC2, Fargate, Lambda
```

**Characteristics:**
```
✓ 72% discount (highest savings)
✓ Applies to EC2, Fargate, Lambda
✓ Can switch instance families freely
✓ Can change sizes anytime
✓ Can change regions anytime
✓ Can change OS anytime
✓ Can switch between services
✗ Commitment for 1-3 years
✗ Usage beyond commitment charged separately
```

**Compute Savings Plan Flexibility:**
```
CAN CHANGE:
✓ Any instance family (t3, m5, c5, r5, z1d, etc.)
✓ Any instance size (nano → 24xlarge)
✓ Any region (us-east-1 → ap-southeast-2)
✓ Any OS (Linux, Windows, RHEL, SQL Server)
✓ Between services (EC2 → Fargate → Lambda)
✓ Tenancy changes
└─ All WITHOUT penalty

CHANGES ARE AUTOMATIC:
├─ Switch instance type instantly
├─ Discount applies immediately
└─ No approval needed
```

**Use Cases:**
```
1. Multi-Family Environments
   ├─ Use mix of instance types
   ├─ t3 for small tasks
   ├─ m5 for mid-tier
   ├─ c5 for compute
   ├─ Discount applies to all

2. Growing Businesses
   ├─ Start with small instances
   ├─ Grow to larger instances
   ├─ Always get 72% discount
   ├─ No renegotiation needed

3. Container/Serverless Migration
   ├─ Start on EC2
   ├─ Move to Fargate
   ├─ Add Lambda functions
   ├─ Commitment still applies

4. Multi-Region Deployments
   ├─ Instances in US
   ├─ Instances in Europe
   ├─ Single commitment covers both

5. Cost Optimization with Flexibility
   ├─ Want deep savings (72%)
   ├─ Need to stay flexible
   ├─ Perfect balance
```

**Cost Example:**
```
Savings Plan Commitment: $10,000/year

Scenario 1: Consistent usage
├─ $10,000/year covers all usage
└─ Everything is discounted

Scenario 2: Usage grows
├─ $10,000 covers $13,889 on-demand value
├─ Additional usage: Charged at on-demand
└─ Still saving 72% on commitment

Scenario 3: Switch instance types
├─ Start: 10x t3.large ($0.83/hr = $8,300/yr)
├─ Later: 5x m5.xlarge ($1.39/hr = $5,600/yr)
├─ Discount applies to both equally
```

**Savings Plans vs Committed Cost:**
```
Company Target: $5,000/month compute spend

With Savings Plan:
├─ Commit: $60,000/year (1-year)
├─ Gets: 72% discount
├─ Effective rate: ~$13.89/hour
├─ Can use 5 m5.large OR 10 t3.medium
├─ Savings: ~$60,000 (vs on-demand)

With On-Demand:
├─ Average m5.large: $0.96/hr
├─ 5 instances × 730 hours = $3,504/month
├─ No commitment, no savings
```

**Pros:**
- ✓ Maximum flexibility (72% discount)
- ✓ Switch instances freely
- ✓ Applies to EC2, Fargate, Lambda
- ✓ Can change regions
- ✓ Highest savings available
- ✓ Best balance of savings + flexibility

**Cons:**
- ✗ 1-3 year commitment required
- ✗ Usage beyond commitment: On-demand pricing
- ✗ Commitment is firm (can't cancel)

---

### 6. SAVINGS PLANS (EC2 INSTANCE SAVINGS PLAN)

**Overview:**
Commitment for specific instance family within a region. Less flexible than Compute SP but with discounts.

```
Pricing: $0.36/hour (64% discount)
Commitment: 1 or 3 years
Upfront Cost: Optional
Minimum Contract: 1-3 years
Flexibility: Moderate
Services: EC2 only
```

**Characteristics:**
```
✓ 64% discount
✓ Applies to EC2 only
✓ Can change sizes within family
✓ Can change tenancy
✓ Higher discount than convertible RI
✗ Locked to specific instance family
✗ Locked to specific region
✗ Cannot change family
✗ Less flexibility than Compute SP
```

**EC2 Instance SP Limitations:**
```
CAN CHANGE:
✓ Instance size (t3.medium → t3.xlarge)
✓ Tenancy (default → dedicated)

CANNOT CHANGE:
✗ Instance family (t3 → m5)
✗ Region (us-east-1 → us-west-2)
✗ OS (Linux → Windows)
✗ Service (EC2 only)
```

**Use Cases:**
```
1. Single Instance Family Workloads
   ├─ Use only t3 instances
   ├─ Different sizes over time
   └─ Want 64% discount

2. Regional Deployments
   ├─ Only deployed in one region
   ├─ Use same instance family
   └─ Want commitment discount

3. When Compute SP Too Flexible
   ├─ Know you'll use t3
   ├─ In us-east-1
   ├─ Willing to lock to get slightly better discount
```

**Comparison: EC2 SP vs Compute SP**
```
Compute Savings Plan (Maximum Flexibility):
├─ Cost: $10,000/year
├─ Works: ANY family, ANY size, ANY region, ANY service
├─ Best: Maximum flexibility needs
├─ Discount: 72%

EC2 Instance Savings Plan (Moderate Flexibility):
├─ Cost: $9,000/year (less expensive)
├─ Works: Specific family only (e.g., t3)
├─ Best: Single family usage
├─ Discount: 64%

Standard Reserved Instance (Minimal Flexibility):
├─ Cost: $8,000/year (cheaper)
├─ Works: Specific type only (t3.large)
├─ Best: Locked configuration
├─ Discount: 50%
```

**Pros:**
- ✓ 64% savings
- ✓ Can change sizes
- ✓ Better than Standard RI
- ✓ Less commitment than Compute SP (slightly)

**Cons:**
- ✗ Locked to instance family
- ✗ Locked to region
- ✗ Less flexible than Compute SP
- ✗ Still 1-3 year commitment

---

### 7. DEDICATED INSTANCES

**Overview:**
EC2 instances on hardware dedicated to your account. Charged extra for hardware isolation.

```
Pricing: $2.00/hour + additional cost
Commitment: Per-hour (can stop)
Upfront Cost: None
Minimum Contract: None
Flexibility: High
Hardware: Dedicated to account
```

**Characteristics:**
```
✓ Physical server dedicated to your account
✓ Isolated from other customers
✓ Can change instance types on same hardware
✓ No other customer workloads
✗ Most expensive option
✗ Unnecessary for most workloads
✗ Hardware isolation cost premium
✗ No deeper discounts available
```

**What Dedicated Means:**
```
Shared Infrastructure (Normal EC2):
├─ Multiple customers on same physical server
├─ Virtualization isolates workloads
├─ Lower cost
└─ Secure but shared

Dedicated Instances:
├─ Entire physical server dedicated to you
├─ Only your instances on hardware
├─ Higher cost
├─ Physical isolation
└─ Still virtualized (not bare metal)

Dedicated Hosts:
├─ Full server control
├─ No virtualization layer
├─ For software licensing
└─ Different pricing model
```

**Use Cases:**
```
1. Software Licensing Requirements
   ├─ License per-socket/core
   ├─ Dedicated hardware required
   ├─ Examples: Certain databases, big data tools

2. Compliance Requirements
   ├─ HIPAA compliance needs
   ├─ PCI-DSS strict isolation
   ├─ Regulatory requirements for isolation

3. Performance Sensitivity
   ├─ Expect "noisy neighbor" issues
   ├─ Want guaranteed isolation
   ├─ Non-shared physical resources

4. License Mobility
   ├─ Need to move licenses between instances
   ├─ Dedicated instances allow this
   ├─ Dedicated Hosts better for this
```

**Cost Comparison:**
```
Standard m5.large (Shared):     $0.96/hour
Dedicated m5.large:             $2.00/hour  (+$1.04 premium)

Annual Cost (1 instance):
Shared:                         $8,409/year
Dedicated:                      $17,520/year
                                ($9,111 MORE)
```

**Pros:**
- ✓ Full hardware isolation
- ✓ Physical server dedication
- ✓ No other customer workloads
- ✓ Meets some compliance needs

**Cons:**
- ✗ MOST expensive option
- ✗ Unnecessary for most use cases
- ✗ No deeper savings available
- ✗ Hardware underutilization likely

---

### 8. DEDICATED HOSTS

**Overview:**
An entire physical server dedicated to you with full control. Priced per host, not per instance.

```
Pricing: $1.00-$5.00/hour (per host)
Commitment: Monthly billing
Upfront Cost: Can be significant
Minimum Contract: Monthly
Flexibility: Can mix instance sizes
Hardware: Full server control
```

**Characteristics:**
```
✓ Full physical server
✓ Bring your own license (BYOL)
✓ License mobility
✓ Can run multiple instance sizes
✓ Full host control
✗ Most expensive per-instance
✗ Must commit by the month
✗ Software licensing constraints
✗ Minimum host rental cost
```

**Dedicated Hosts vs Dedicated Instances:**
```
DEDICATED INSTANCES:
├─ Server dedicated to account
├─ AWS controls virtualization
├─ Cannot move licenses
├─ Pay per instance + premium
└─ Simpler management

DEDICATED HOSTS:
├─ Full server to customer
├─ Customer controls virtual layout
├─ Can move licenses between VMs
├─ Pay per host (monthly)
├─ Bring Your Own License (BYOL)
└─ Complex licensing needs
```

**Use Cases:**
```
1. Bring Your Own License (BYOL)
   ├─ SQL Server licensing
   ├─ Oracle licensing
   ├─ Want to reuse existing licenses
   └─ Reduce software costs

2. License Mobility
   ├─ Move licenses between instances
   ├─ Consolidate existing licenses
   ├─ Complex licensing agreements

3. Full Host Control
   ├─ Specific OS requirements
   ├─ Custom host configurations
   ├─ Detailed resource allocation

4. Specific Compliance
   ├─ Some compliance frameworks
   ├─ Physical host control required
   ├─ Very specific regulations
```

**Cost Comparison:**

```
Option 1: Dedicated Instances (2x m5.large)
├─ Instance cost: $0.96 × 2 = $1.92/hr
├─ Dedicated premium: $1.04 × 2 = $2.08/hr
├─ Total: $3.92/hour = $34,387/year
└─ Plus: Own license costs ($?)

Option 2: Dedicated Host (m5 family)
├─ Host cost: ~$2.00/hour = $17,520/year
├─ Can fit: Multiple m5 instances
├─ Plus: Bring your license (SAVE licensing)
└─ Potential savings: $5,000-$20,000+ annually
```

**Pros:**
- ✓ Full physical server control
- ✓ License portability
- ✓ BYOL support (save on licensing)
- ✓ Can mix instance configurations
- ✓ Can save significantly with BYOL

**Cons:**
- ✗ Most expensive per-instance
- ✗ Monthly minimum commitment
- ✗ Complex license management
- ✗ Likely host underutilization

---

## Comprehensive Comparison Table

| Feature | On-Demand | Spot | Standard RI | Convertible RI | Compute SP | EC2 SP | Dedicated | Dedicated Host |
|---------|-----------|------|------------|----------------|-----------|--------|-----------|----------------|
| **Hourly Cost** | $1.00 | $0.10 | $0.50 | $0.54 | $0.28 | $0.36 | $2.00+ | $1.00/host |
| **Discount** | 0% | 90% | 50% | 46% | 72% | 64% | Extra cost | Depends |
| **Commitment** | None | None | 1-3 yr | 1-3 yr | 1-3 yr | 1-3 yr | None | Monthly |
| **Flexibility** | Max | Max | Min | Mod | Max | Mod | High | High |
| **Upfront Cost** | None | None | Yes | Yes | Opt | Opt | None | Yes |
| **Can Interrupt** | No | Yes | No | No | No | No | No | No |
| **Instance Family** | Any | Any | Locked | Flex | Any | Locked | Any | Any |
| **Region Change** | Any | Any | No | Yes | Yes | No | Any | Yes |
| **Size Change** | Any | Any | Limited | Yes | Any | Yes | Any | Yes |
| **Best Use Case** | Testing | Batch | Steady 24/7 | Uncertain | Predictable | Single family | Compliance | BYOL |
| **Reliability** | High | Very Low | High | High | High | High | High | High |

---

## Decision Tree: Which Pricing Model?

```
START: How predictable is your workload?

├─ UNPREDICTABLE (Variable, spiky)
│  └─ Use: ON-DEMAND
│     └─ Best for: Testing, variable loads
│
├─ PREDICTABLE (Consistent 24/7)
│  │
│  ├─ Do you need flexibility?
│  │  │
│  │  ├─ YES (might change instance type)
│  │  │  ├─ Need to switch families?
│  │  │  │  ├─ YES → COMPUTE SAVINGS PLAN (72% discount)
│  │  │  │  └─ NO → EC2 INSTANCE SP (64% discount)
│  │  │  │
│  │  │  └─ Don't want to commit
│  │  │     └─ Use: ON-DEMAND (pay premium for flexibility)
│  │  │
│  │  └─ NO (locked configuration)
│  │     └─ RESERVED INSTANCE - STANDARD (50% discount)
│  │
│  └─ Need hardware isolation?
│     ├─ YES (compliance, licensing)
│     │  ├─ Have software licenses?
│     │  │  ├─ YES → DEDICATED HOST (BYOL discount)
│     │  │  └─ NO → DEDICATED INSTANCE
│     │  │
│     │  └─ Consider costs carefully
│     │
│     └─ NO (standard isolation OK)
│        └─ SAVINGS PLAN (72% discount)
│
└─ FLEXIBLE WORKLOAD (Can stop/start)
   ├─ Can tolerate interruptions?
   │  ├─ YES (batch processing)
   │  │  └─ SPOT INSTANCES (90% discount)
   │  │
   │  └─ NO (must be reliable)
   │     └─ SAVINGS PLAN (72% discount)
   │
   └─ Long-term predictable?
      ├─ YES → SAVINGS PLAN or RESERVED
      └─ NO → ON-DEMAND
```

---

## Cost Calculation Examples

### Example 1: Web Application (24/7, predictable)

```
Application: E-commerce website
Workload: Constant, predictable
Traffic: Steady 24/7
Instances: 5x m5.large

Annual Calculation:
Hours per year: 365 × 24 = 8,760 hours
Instance hours: 5 × 8,760 = 43,800 hours
Base rate: $0.96/hour (m5.large on-demand)

PRICING OPTIONS:

On-Demand:
└─ 43,800 hours × $0.96 = $42,048/year

Reserved Instances (Standard, 1-year, all upfront):
├─ Commitment: $21,024 upfront (50% off)
├─ Then: Free usage for 1 year
└─ Total: $21,024/year (SAVE $21,024 = 50%)

Reserved Instances (Standard, 3-year, all upfront):
├─ Commitment: $30,456 upfront
├─ Then: Free usage for 3 years
└─ Total: $10,152/year average (SAVE $31,896 = 76%)

Compute Savings Plan (3-year):
├─ Commitment: $11,900/year
├─ Covers: 72% of compute spend
├─ Additional usage: On-demand
└─ Best case: SAVE $30,148/year (72%)

Best Option: 3-Year Reserved Instance
└─ Saves: $31,896 over 3 years
```

### Example 2: Batch Processing (Flexible, non-critical)

```
Task: Process 100 TB of image data
Duration: 2 weeks (168 hours)
Instances: 10x c5.2xlarge (parallel processing)
Can interrupt: Yes (checkpoints saved)

Instance hours: 10 × 168 = 1,680 hours
Base rate: $1.63/hour (c5.2xlarge on-demand)

PRICING OPTIONS:

On-Demand:
└─ 1,680 × $1.63 = $2,738/2 weeks

Spot Instances:
├─ Price: $0.49/hour (70% discount)
├─ Cost: 1,680 × $0.49 = $823
├─ Risk: May interrupt
└─ Savings: $1,915 (70%)

Savings Plan (if already have commitment):
├─ Pre-committed to SP
├─ Discount applied: 72%
├─ Effective: $0.46/hour
└─ Cost: $772

Best Option: Spot Instances
└─ Can save $1,915 vs on-demand
└─ Risk acceptable for batch job
└─ Application handles interruption
```

### Example 3: Development Environment (Ad-hoc, testing)

```
Environment: Multiple instances for testing
Duration: ~40 hours/month (on/off)
Instances: 2x t3.large + 1x t3.xlarge
Running time: 40 hours/month (480/year)

Instance hours: 
├─ 2 × t3.large: 960 hours/year
├─ 1 × t3.xlarge: 480 hours/year
└─ Total: 1,440 hours/year

Rates:
├─ t3.large: $0.83/hour
└─ t3.xlarge: $1.66/hour

Average cost: ~$2,000/year

PRICING OPTIONS:

On-Demand (most practical):
├─ Use only when needed
├─ No long-term commitment
├─ Cost: $2,000/year
└─ Best: Simple, no waste

Reserved Instance (BAD idea):
├─ Pay for 24/7 when using 40 hours/month
├─ Massive waste
├─ Total cost: $18,000+/year
└─ Would lose money

Spot Instances (Good option):
├─ Can get interrupted during testing
├─ Price: $0.25/hour (70% off)
├─ Cost: ~$360/year
├─ Savings: $1,640
└─ Best: If interruptions acceptable

Best Option: On-Demand (simplicity) or Spot (savings)
```

---

## Savings Summary

```
Annual Cost Comparison (1 Instance, 24/7/365)

Instance Type: m5.large on-demand = $0.96/hour

ON-DEMAND:        $8,410/year    (0% discount)
SPOT:             $841/year      (90% discount) *
RESERVED-1YR:     $4,205/year    (50% discount)
RESERVED-3YR:     $3,154/year    (62.5% discount)
COMPUTE SP-1YR:   $2,349/year    (72% discount)
COMPUTE SP-3YR:   $2,349/year    (72% discount)
EC2 SP-1YR:       $3,033/year    (64% discount)
EC2 SP-3YR:       $3,033/year    (64% discount)
DEDICATED:        $17,520/year   (-108% premium)
DEDICATED HOST:   $8,761/year    (variable)

* Spot can be interrupted, not for production

MAXIMUM SAVINGS:  $6,061/year with Savings Plan
BEST BALANCE:     Savings Plan (72% savings + flexibility)
```

---

## Quick Decision Guide

**Choose ON-DEMAND if:**
- ✓ Workload is unpredictable
- ✓ Short-term testing/development
- ✓ Cannot predict future needs
- ✓ Prefer simplicity over savings
- ✓ Occasional, sporadic usage

**Choose SPOT INSTANCES if:**
- ✓ Can tolerate interruptions
- ✓ Batch processing jobs
- ✓ Fault-tolerant application
- ✓ Flexible timeline
- ✓ Non-critical workload
- **Savings: 90%**

**Choose RESERVED INSTANCES if:**
- ✓ Steady 24/7 workload
- ✓ Predictable resource needs
- ✓ Known instance configuration
- ✓ 1-3 year timeframe
- ✓ Want guaranteed pricing
- **Savings: 50-72%** (depending on upfront)

**Choose CONVERTIBLE RI if:**
- ✓ Want RI benefits
- ✓ May change instance families
- ✓ Uncertain future needs
- ✓ Willing to pay premium for flexibility
- **Savings: 46%**

**Choose SAVINGS PLAN (COMPUTE) if:**
- ✓ Predictable long-term usage
- ✓ May change instance types
- ✓ Multi-region deployment
- ✓ Want maximum flexibility
- ✓ Want maximum savings
- **Savings: 72%** (BEST BALANCE)

**Choose SAVINGS PLAN (EC2 INSTANCE) if:**
- ✓ Will use single instance family
- ✓ Single region
- ✓ Want commitment discount
- **Savings: 64%**

**Choose DEDICATED INSTANCES if:**
- ✓ Compliance requires isolation
- ✓ License requirements
- ✓ Regulatory needs
- ✓ Very specific requirements
- **Cost: Premium (not recommended otherwise)**

**Choose DEDICATED HOSTS if:**
- ✓ Have software licenses (BYOL)
- ✓ License mobility needed
- ✓ Full host control required
- ✓ Can amortize licensing costs
- **Cost: High, but may save on licenses**

---

## AWS Certification Tips

**For AWS Cloud Practitioner Exam:**

1. **Know the basics:**
   - On-Demand = No commitment
   - Spot = Can interrupt (90% off)
   - Reserved = 1-3 year commitment
   - Savings Plans = Most flexible + biggest discount

2. **Common test scenarios:**
   - "No upfront costs, start/stop anytime" → On-Demand
   - "Can be interrupted, cheapest option" → Spot
   - "Predictable 24/7 workload" → Reserved or Savings Plan
   - "Compliance isolation required" → Dedicated

3. **Price comparison questions:**
   - Cheapest for flexible: Spot (90%)
   - Cheapest for committed: Savings Plan (72%)
   - Best balance: Savings Plan
   - Most reliable: Reserved or Savings Plan

4. **Use case matching:**
   - Batch jobs → Spot
   - Production web app → Reserved or Savings Plan
   - Development → On-Demand
   - Compliance/licensing → Dedicated

---

This comparison should help you understand EC2 pricing models for both AWS certification and real-world decision-making! 🚀
