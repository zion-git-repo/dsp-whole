# DSP Management Platform - Feature Specifications & Information Architecture

## Document Purpose

This document provides comprehensive feature specifications organized by user role, defining the information architecture, screen hierarchy, user flows, and specific functionality requirements for UX designers and developers. Each section details what users see, what actions they can perform, and how different features connect to create complete workflows.

---

## Global Navigation Structure

### Top-Level Navigation (Available to All Authenticated Users)

```
┌─────────────────────────────────────────────────────────────┐
│  [LOGO]  Dashboard  |  My Role Menu  |  🔔 Notifications  │  👤 Profile  │
└─────────────────────────────────────────────────────────────┘
│                                                               │
│  Station Selector: [Dropdown: All Stations / Station Name]  │
│  Date Range: [Quick Select: Today | Week | Month | Custom]  │
└─────────────────────────────────────────────────────────────┘
```

**Station Selector Behavior:**
- Multi-station DSPs see "All Stations" option for aggregated views
- Single-station DSPs have this fixed to their station
- Changing station context refreshes all data to show selected station
- User's last selected station is remembered for next login

**Notification Center:**
- Real-time alerts for items requiring attention
- Categorized by urgency: Critical, High, Medium, Low
- Click to navigate directly to relevant screen
- Mark as read/unread functionality
- Notification types by role (detailed in role sections)

**Profile Menu:**
- Account Settings
- Change Password
- Notification Preferences
- Help & Documentation
- Sign Out

---

## ROLE 1: DSP OWNER

### Information Architecture

```
DSP Owner Dashboard
│
├── Executive Overview
│   ├── Cross-Station Performance Summary
│   ├── Financial Snapshot (All Stations)
│   ├── Critical Alerts Dashboard
│   └── Key Metrics Comparison
│
├── Stations Management
│   ├── Station Directory
│   ├── Station Performance Comparison
│   ├── Station Configuration
│   └── Station Analytics
│
├── Financial Management
│   ├── Revenue Dashboard
│   ├── Expense Tracking
│   ├── P&L Reports
│   ├── Payroll Summary (All Stations)
│   └── Budget vs Actual
│
├── Fleet Overview (All Stations)
│   ├── Total Fleet Status
│   ├── Fleet Utilization Metrics
│   ├── Maintenance Costs by Station
│   └── Vehicle ROI Analysis
│
├── Workforce Overview (All Stations)
│   ├── Total Headcount by Station
│   ├── Driver Performance Leaderboard
│   ├── Retention & Turnover Metrics
│   └── Recruiting Pipeline
│
├── Performance Analytics
│   ├── Scorecard Comparison (All Stations)
│   ├── Trend Analysis
│   ├── Benchmarking
│   └── Root Cause Analysis
│
├── Reports & Export
│   ├── Executive Reports
│   ├── Custom Report Builder
│   ├── Scheduled Report Delivery
│   └── Data Export Tools
│
└── System Administration
    ├── User Management (All Stations)
    ├── Role & Permission Management
    ├── Integration Settings
    ├── Billing & Subscription
    └── Audit Logs
```

### Feature List: DSP Owner

#### F-OWN-001: Executive Overview Dashboard

**Screen Components:**
- Hero metrics cards showing:
  - Total active routes across all stations (today)
  - Total active drivers across all stations
  - Total fleet size and availability percentage
  - Week-to-date revenue
  - Current week payroll projection
  - Average scorecard score across all stations
  
- Station health indicator grid:
  - Each station shown as card with health score (Green/Yellow/Red)
  - Click card to drill into station details
  - Shows: Station name, route count today, driver count, key alert count
  
- Critical alerts section:
  - Stations with scorecard metrics below threshold
  - Routes not assigned for next day
  - Drivers with pending terminations
  - Vehicles with overdue maintenance
  - Certifications expiring within 7 days
  - Financial anomalies (unexpected cost spikes)
  
- Performance trend charts:
  - 12-week scorecard trend line by station
  - 12-week revenue trend
  - 12-week cost-per-delivery trend
  - Driver headcount trend

**User Actions:**
- Click any metric to see detailed breakdown
- Click station card to navigate to that station's dashboard
- Click alert to navigate to resolution screen
- Filter view by date range
- Export dashboard as PDF report

**Data Refresh:**
- Real-time for today's metrics
- Nightly refresh for historical trends
- Manual refresh button available

#### F-OWN-002: Station Performance Comparison

**Screen Layout:**
```
┌─────────────────────────────────────────────────────────┐
│  Metrics to Compare: [Multi-select dropdown]            │
│  Time Period: [Last Week | Last Month | Last Quarter]   │
└─────────────────────────────────────────────────────────┘

[Table View]
Station Name | Metric 1 | Metric 2 | Metric 3 | Overall Score
────────────────────────────────────────────────────────────
Station A    | 98.5%   | 2.3      | $1.45    | 🟢 Excellent
Station B    | 94.2%   | 4.1      | $1.67    | 🟡 Good
Station C    | 89.7%   | 6.8      | $1.89    | 🔴 Needs Attention

[Chart View]
- Radar chart comparing stations across multiple metrics
- Bar chart showing ranking by selected metric
- Trend lines showing improvement/decline by station
```

**Available Metrics for Comparison:**
- Amazon scorecard composite score
- Delivery success rate
- POD compliance rate
- Safety events per 10k miles
- Customer feedback score
- Route completion rate
- Average cost per delivery
- Fuel efficiency (MPG)
- Driver retention rate
- Overtime percentage
- Maintenance cost per vehicle
- Revenue per route

**User Actions:**
- Select/deselect metrics to compare
- Change time period
- Sort table by any column
- Click station name to see detailed explanation
- Export comparison report
- Schedule automated weekly comparison email

#### F-OWN-003: Financial Dashboard

**Revenue Section:**
- Current month revenue vs target (progress bar)
- Revenue by station (pie chart)
- Revenue trend (12-month line chart)
- Revenue per route calculation
- Contract renewal dates and values

**Expense Section:**
- Expense breakdown by category:
  - Payroll (largest category, highlighted)
  - Fuel costs
  - Vehicle maintenance
  - Vehicle leases/payments
  - Insurance
  - Station rent/utilities
  - Equipment and supplies
  - Other operational costs
  
- Expense trends (6-month comparison)
- Budget vs actual by category
- Cost per delivery calculation
- Top 5 expense anomalies (unexpected high costs)

**Profitability Section:**
- Gross profit margin
- Net profit margin
- EBITDA calculation
- Profit by station
- Breakeven analysis

**Payroll Summary (All Stations):**
- Current pay period total
- Regular hours vs overtime hours
- Overtime percentage by station
- Average hourly cost by station
- Historical payroll trend

**User Actions:**
- Drill down into any expense category
- View transaction details
- Export financial reports (CSV, Excel, PDF)
- Set budget alerts
- Compare current period to previous periods
- Annotate unusual expenses

#### F-OWN-004: Fleet Overview (All Stations)

**Fleet Status Grid:**
```
Total Vehicles: 150

Active in Service:     120 (80%)  🟢
In Repair:             15  (10%)  🟡
Scheduled Maintenance: 8   (5%)   🟡
On Rent (Temporary):   5   (3%)   🔵
Retired/Sold:          2   (1%)   ⚫
```

**Fleet Metrics Dashboard:**
- Average vehicle age by station
- Average odometer reading
- Vehicles over 100k miles count
- Vehicles overdue for oil change (critical alert)
- Vehicles overdue for inspection
- Average days in repair shop
- Most reliable vehicles (lowest maintenance cost)
- Least reliable vehicles (highest maintenance cost)

**Cost Analysis:**
- Total fleet maintenance costs (month/quarter/year)
- Maintenance cost per vehicle per month
- Maintenance cost by station
- Vehicles with maintenance costs exceeding threshold
- ROI analysis (cost vs vehicle age)

**Utilization Metrics:**
- Vehicles used today / total available
- Average daily utilization percentage by station
- Vehicles not used in last 7 days
- Vehicles not used in last 30 days (candidates for sale)

**User Actions:**
- Click on any status category to see vehicle list
- View detailed vehicle profiles
- Generate fleet reports
- Set maintenance cost alerts
- Compare fleet performance across stations
- Export fleet data

#### F-OWN-005: Workforce Overview (All Stations)

**Headcount Dashboard:**
```
Total Drivers: 180

Active:        165 (91.7%)  🟢
On Leave:      5   (2.8%)   🔵
Inactive:      7   (3.9%)   🟡
Terminated:    3   (1.7%)   🔴

New Hires (Last 30 Days):     12
Terminations (Last 30 Days):  8
Net Change:                   +4
```

**Performance Leaderboard:**
- Top 10 drivers by composite score across all stations
- Shows: Driver name, station, scorecard metrics, routes completed this month
- Bottom 10 drivers requiring attention
- Most improved drivers (month over month)

**Retention Metrics:**
- Average driver tenure
- 30-day retention rate
- 90-day retention rate
- 6-month retention rate
- Retention rate by station (comparison)
- Voluntary vs involuntary termination breakdown

**Recruiting Pipeline:**
- Open positions by station
- Applications in review
- Candidates in onboarding
- Average time to hire
- Cost per hire

**Driver Utilization:**
- Active drivers receiving regular routes
- Active drivers not scheduled this week
- Average routes per driver per week
- Driver availability vs route needs
- Underutilized drivers by station

**User Actions:**
- Click driver name to view full profile
- Filter leaderboard by station
- Export driver lists
- View detailed retention reports
- Compare workforce metrics across stations
- Schedule automated workforce reports

#### F-OWN-006: Cross-Station Scorecard Analytics

**Scorecard Overview Grid:**
- Weekly scorecard summary for all stations
- Each row is a station, columns are metrics:
  - Delivery Completion Rate
  - Delivered Not Received (DNR)
  - Photo On Delivery (POD)
  - Customer Escalations
  - Mentor Feedback Score
  - Overall Score
  
- Color coding: Green (meets/exceeds), Yellow (caution), Red (below threshold)
- Click any cell to see detailed breakdown

**Trend Analysis:**
- 12-week trend lines for each metric by station
- Identify improving vs declining stations
- Seasonal pattern recognition
- Anomaly detection (sudden drops in performance)

**Benchmarking:**
- Compare stations to each other
- Identify best practices from top performers
- Root cause analysis for underperformers
- Correlation analysis (e.g., does safety training reduce mentor deductions?)

**User Actions:**
- Download weekly scorecards for all stations
- Set up automated scorecard distribution
- Create custom metric combinations
- Schedule performance reviews with station managers
- Export trend reports

#### F-OWN-007: System Administration

**User Management:**
- List all users across all stations
- View: Name, email, role, station(s), last login, status
- Search and filter users
- Add new user with role assignment
- Edit user permissions
- Deactivate/reactivate users
- Reset user passwords
- View user activity logs

**Role & Permission Management:**
- Predefined roles: Owner, Station Manager, Dispatcher, HR Admin, Fleet Manager, Driver
- View permissions matrix for each role
- Create custom roles if needed
- Assign role to multiple users (bulk action)

**Integration Settings:**
- API keys and credentials for external systems
- Amazon Cortex integration status
- Samsara API connection status
- Netradyne API connection status
- ADP export configuration
- Data sync schedules and last sync times
- Error logs for failed integrations

**Billing & Subscription:**
- Current subscription plan
- Number of active stations
- Number of active users
- Number of vehicles in system
- Current month usage statistics
- Invoice history
- Payment method management
- Upgrade/downgrade subscription

**Audit Logs:**
- All system activities with user, timestamp, action
- Filter by: user, action type, date range, station
- Export audit logs for compliance
- Critical actions highlighted (data deletion, permission changes, financial edits)

---

## ROLE 2: STATION MANAGER

### Information Architecture

```
Station Manager Dashboard
│
├── Today's Operations
│   ├── Route Dispatch Status
│   ├── Driver Attendance
│   ├── Vehicle Readiness
│   └── Real-time Alerts
│
├── Dispatch Management
│   ├── Upload Routes from Cortex
│   ├── Assign Routes to Drivers
│   ├── Rescue Coordination
│   ├── Route History
│   └── Dispatch Analytics
│
├── Driver Management
│   ├── Driver Directory
│   ├── Driver Performance
│   ├── Coaching & Discipline
│   ├── Attendance & Time Tracking
│   └── Driver Onboarding
│
├── Fleet Management
│   ├── Vehicle Directory
│   ├── Maintenance Requests
│   ├── Vehicle Issues & Repairs
│   ├── Fuel Tracking
│   └── Vehicle Inspections
│
├── Payroll Management
│   ├── Current Pay Period Summary
│   ├── Review & Approve Hours
│   ├── Overtime Management
│   ├── Export to ADP
│   └── Payroll History
│
├── Performance Management
│   ├── Weekly Scorecard
│   ├── POD Metrics
│   ├── Safety Events (Samsara/Netradyne)
│   ├── Coaching Queue
│   └── Performance Reports
│
├── Scheduling
│   ├── Driver Availability Calendar
│   ├── Route Coverage Planning
│   ├── Schedule Requests
│   └── Shift Templates
│
├── Communication
│   ├── Driver Messages
│   ├── Coaching Templates
│   ├── Announcements
│   └── Call Logs
│
└── Station Analytics
    ├── Station Health Dashboard
    ├── Operational Reports
    ├── Custom Analytics
    └── Export Center
```

### Feature List: Station Manager

#### F-MGR-001: Today's Operations Dashboard

**Screen Layout:**
```
┌─────────────────────────────────────────────────────────────┐
│  Station: [Station Name]           Date: [Today's Date]      │
└─────────────────────────────────────────────────────────────┘

[Route Dispatch Status - Hero Metrics]
┌──────────────┬──────────────┬──────────────┬──────────────┐
│ Routes Today │ Assigned     │ Dispatched   │ Completed    │
│     45       │  42 (93%)    │  38 (84%)    │  35 (78%)    │
└──────────────┴──────────────┴──────────────┴──────────────┘

[Driver Attendance]
┌──────────────┬──────────────┬──────────────┬──────────────┐
│ Expected     │ Clocked In   │ On Route     │ Absent       │
│     42       │  40 (95%)    │  38 (90%)    │  2 (5%)      │
└──────────────┴──────────────┴──────────────┴──────────────┘

[Vehicle Status]
┌──────────────┬──────────────┬──────────────┬──────────────┐
│ Available    │ On Route     │ In Repair    │ Maintenance  │
│     48       │  38 (79%)    │  5 (10%)     │  5 (10%)     │
└──────────────┴──────────────┴──────────────┴──────────────┘

[Critical Alerts - Requires Immediate Attention]
🔴 3 routes not assigned for tomorrow
🔴 Vehicle V-245 reported safety issue - requires immediate check
🟡 2 drivers absent without notification
🟡 Driver D-089 approaching 40 hours this week (overtime alert)
🟡 5 fuel receipts pending approval

[Routes Needing Rescue/Support]
Route R-12345 | Driver: John Smith | Expected 60 stops behind | Rescue Available: Yes | [ASSIGN RESCUE]
Route R-12399 | Driver: Jane Doe   | Vehicle issue reported  | Status: Waiting swap  | [VIEW DETAILS]

[Performance Snapshot - Today]
Delivery Success Rate:  97.2% (↑ 0.5% vs yesterday)
POD Compliance:         98.5% (↑ 0.3% vs yesterday)  
Safety Events:          3 events (2 hard brake, 1 speeding)
Customer Escalations:   0 (🟢 Good!)
```

**Real-time Updates:**
- Route status updates every 5 minutes (if integrated with Amazon tracking)
- Driver clock-in/clock-out updates immediately
- New alerts appear at top with notification sound
- Rescue requests trigger immediate alert

**User Actions:**
- Click any metric to see detailed list
- Click alert to navigate to resolution screen
- Assign rescue to route
- Send message to driver from route card
- Mark alert as acknowledged/resolved
- Refresh data manually
- View historical comparison

#### F-MGR-002: Route Upload & Assignment Workflow

**Step 1: Upload Routes from Cortex**

```
┌─────────────────────────────────────────────────────────┐
│  Upload Routes for Date: [Date Picker - default tomorrow] │
│                                                           │
│  [Upload CSV File from Cortex] or [Drag & Drop Here]    │
│                                                           │
│  Recent Uploads:                                          │
│  - 2025-11-08_routes.csv (45 routes) - Uploaded at 4:30 PM │
│  - 2025-11-07_routes.csv (43 routes) - Uploaded at 5:15 PM │
└─────────────────────────────────────────────────────────┘
```

**CSV Validation:**
- System validates required fields: Route ID, Estimated Packages, Estimated Duration, Route Type
- Shows preview of parsed data before importing
- Highlights any errors or warnings
- Option to fix and re-upload or proceed with warnings

**Step 2: Route Assignment Interface**

```
┌─────────────────────────────────────────────────────────┐
│  Routes for: November 8, 2025            45 total routes │
│  Assigned: 38 | Unassigned: 7                           │
│                                                           │
│  [Smart Auto-Assign] [Clear All Assignments]            │
└─────────────────────────────────────────────────────────┘

[Left Panel - Unassigned Routes]
┌─────────────────────────────────┐
│ Filter: [All | Residential |    │
│         Business | Heavy]        │
│ Sort by: [Route ID | Est. Time] │
├─────────────────────────────────┤
│ Route R-45123                   │
│ 🔵 Residential | ⏱ 8.5 hrs     │
│ 📦 180 packages | No special req│
│ [Drag to assign] ────────────>  │
├─────────────────────────────────┤
│ Route R-45124                   │
│ 🟣 Business | ⏱ 7.0 hrs        │
│ 📦 145 packages | Heavy items   │
│ [Drag to assign] ────────────>  │
└─────────────────────────────────┘

[Right Panel - Driver Assignment Grid]
┌──────────────────────────────────────────┐
│ Filter: [Show: All | Available Only]    │
│ Sort: [Name | Performance | Experience]  │
├──────────────────────────────────────────┤
│ Driver: John Smith (ID: D-089)          │
│ Status: ✅ Available | Scheduled         │
│ Vehicle: V-234 (Ready ✅)               │
│ Performance: ⭐⭐⭐⭐⭐ (4.8/5.0)      │
│ Experience: 🟢 High (18 months)         │
│ Last 10 routes avg: 8.2 hrs             │
│                                          │
│ [Drop route here to assign]             │
│                                          │
│ Assigned: Route R-45099 (8.5 hrs)       │
│ [X Remove]                               │
├──────────────────────────────────────────┤
│ Driver: Jane Doe (ID: D-124)            │
│ Status: ✅ Available | Scheduled         │
│ Vehicle: V-256 (Ready ✅)               │
│ Performance: ⭐⭐⭐⭐ (4.2/5.0)         │
│ Experience: 🟡 Medium (6 months)        │
│ Last 10 routes avg: 9.1 hrs             │
│                                          │
│ [Drop route here to assign]             │
│                                          │
│ Assigned: Route R-45101 (7.5 hrs)       │
│ [X Remove]                               │
├──────────────────────────────────────────┤
│ Driver: Mike Johnson (ID: D-067)        │
│ Status: ⚠️ Available | NOT Scheduled    │
│ (Driver did not mark available)         │
│ Performance: ⭐⭐⭐ (3.5/5.0)           │
│ ⚠️ Recent coaching: Speeding (3 days ago)│
│ Last 10 routes avg: 9.5 hrs             │
│                                          │
│ [Drop route here to assign]             │
└──────────────────────────────────────────┘
```

**Smart Auto-Assign Logic:**
- Considers driver performance score
- Matches route difficulty to driver experience
- Balances workload (hours) across drivers
- Respects driver availability submissions
- Avoids assigning to drivers with recent safety events
- Considers driver familiarity with route area (if historical data available)
- Ensures each driver has appropriate vehicle assigned

**Assignment Features:**
- Drag and drop routes to drivers
- Bulk assign by route type
- Color coding for route difficulty
- Warning indicators for suboptimal assignments
- Conflict detection (driver scheduled off, vehicle not ready, driver over hours)
- Ability to add notes to assignment
- Save draft assignments (not published to drivers yet)
- Publish assignments to notify drivers

**User Actions:**
- Manually drag routes to drivers
- Click "Smart Auto-Assign" for algorithm assignment
- Edit individual assignments
- Add/remove drivers from available pool
- Swap assignments between drivers
- View driver history with similar routes
- Add special instructions to route
- Publish assignments (sends notification to drivers)
- Export assignment sheet (PDF/Excel)

#### F-MGR-003: Driver Directory & Profiles

**Driver Directory Screen:**

```
┌─────────────────────────────────────────────────────────┐
│  Driver Directory (Station: [Station Name])              │
│                                                           │
│  [Search drivers...] [Add New Driver]                    │
│                                                           │
│  Filters:                                                 │
│  Status: [All | Active | Inactive | On Leave | Termed]  │
│  Performance: [All | Top Performers | Needs Coaching]    │
│  Availability: [All | Available Today | On Route]        │
└─────────────────────────────────────────────────────────┘

[Driver List - Table View]
Name          | ID     | Status  | Performance | Routes (30d) | Last Active | Actions
──────────────────────────────────────────────────────────────────────────────────
John Smith    | D-089  | Active  | ⭐⭐⭐⭐⭐ | 22          | Today       | [View] [Message]
Jane Doe      | D-124  | Active  | ⭐⭐⭐⭐   | 20          | Today       | [View] [Message]
Mike Johnson  | D-067  | Active  | ⭐⭐⭐     | 18          | Yesterday   | [View] [Message]
Sarah Wilson  | D-201  | Active  | ⭐⭐⭐⭐⭐ | 23          | Today       | [View] [Message]
Tom Brown     | D-156  | Inactive| ⭐⭐       | 0           | 10 days ago | [View] [Reactivate]
Lisa Garcia   | D-234  | On Leave| ⭐⭐⭐⭐   | 15          | 5 days ago  | [View] [Message]

[Quick Stats]
Total Drivers: 42 | Active: 38 | Inactive: 2 | On Leave: 1 | Terminated: 1 (last 30 days)
```

**Driver Profile - Detailed View:**

When clicking on a driver, open comprehensive profile:

```
┌─────────────────────────────────────────────────────────┐
│  👤 John Smith (ID: D-089)                               │
│  Status: Active | Hire Date: March 15, 2024             │
│                                                           │
│  [Edit Profile] [Send Message] [View Schedule] [Coach]   │
└─────────────────────────────────────────────────────────┘

[Navigation Tabs]
Overview | Routes | Performance | Safety | Vehicles | Fuel | Time & Attendance | Coaching | Certifications | Documents

═══════════════════════════════════════════════════════════
[TAB: Overview]
═══════════════════════════════════════════════════════════

[Personal Information]
Name: John Smith
Employee ID: D-089
Email: john.smith@email.com
Phone: (555) 123-4567
Emergency Contact: Mary Smith (Wife) - (555) 987-6543
Hire Date: March 15, 2024
Tenure: 8 months, 23 days
Date of Birth: January 10, 1990
Driver's License: DL123456789 | Expiry: Dec 31, 2026 ✅

[Current Status]
Employment Status: Active
Available Today: Yes ✅
Scheduled for Tomorrow: Yes ✅
On Route Currently: No
Last Clocked In: Today 7:45 AM
Last Route Completed: Yesterday, Route R-44987

[Performance Summary]
Overall Rating: ⭐⭐⭐⭐⭐ (4.8/5.0)
Routes Completed (30 days): 22
Routes Completed (All time): 187
Avg Delivery Success: 98.5%
Avg POD Compliance: 99.2%
Avg Customer Rating: 4.9/5.0
Safety Score: 96% (4 events last 90 days)

[Recent Activity]
- Nov 6: Completed Route R-44987 (8.2 hrs, 178 packages)
- Nov 5: Completed Route R-44901 (8.5 hrs, 183 packages)
- Nov 4: Completed Route R-44856 (7.8 hrs, 165 packages)
- Nov 3: Day Off
- Nov 2: Completed Route R-44798 (9.1 hrs, 195 packages)

[Quick Actions]
[Assign Route] [Send Message] [Schedule Day Off] [Start Coaching] [View Full History]

═══════════════════════════════════════════════════════════
[TAB: Routes]
═══════════════════════════════════════════════════════════

[Filters]
Date Range: [Last 30 Days ▼]
Route Type: [All Types ▼]
Show: [Completed | All | In Progress]

[Route History Table]
Date       | Route ID  | Type        | Packages | Duration | Success Rate | Status
────────────────────────────────────────────────────────────────────────────────
Nov 6, 2025| R-44987  | Residential | 178      | 8h 15m   | 98.9%        | ✅ Completed
Nov 5, 2025| R-44901  | Mixed       | 183      | 8h 32m   | 97.8%        | ✅ Completed
Nov 4, 2025| R-44856  | Residential | 165      | 7h 48m   | 99.4%        | ✅ Completed
Nov 2, 2025| R-44798  | Business    | 195      | 9h 6m    | 96.9%        | ✅ Completed
Nov 1, 2025| R-44712  | Residential | 172      | 8h 21m   | 98.3%        | ✅ Completed

[Click any route for detailed breakdown]

[Route Analytics for This Driver]
- Average duration: 8.4 hours
- Average packages: 179
- Most common route type: Residential (65%)
- Best performing route type: Residential (98.9% success)
- Routes requiring rescue: 1 (0.5% of total)
- Peak performance time: Morning shift

═══════════════════════════════════════════════════════════
[TAB: Performance]
═══════════════════════════════════════════════════════════

[Scorecard Metrics - Last 4 Weeks]

┌─────────────────────────────────────────────────────────┐
│ Delivery Success Rate                                    │
│ ████████████████████░ 98.5%  (Target: 97%)  ✅ Exceeds  │
│ Trend: ↗ +0.8% from last month                          │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ Photo On Delivery (POD) Compliance                       │
│ ███████████████████░░ 99.2%  (Target: 98%)  ✅ Exceeds  │
│ Trend: ↗ +1.2% from last month                          │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ Customer Feedback Score                                  │
│ ████████████████████░ 4.9/5.0  (Target: 4.5)  ✅ Exceeds│
│ Trend: → Stable                                          │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ Delivered Not Received (DNR) Rate                        │
│ ██░░░░░░░░░░░░░░░░░░ 0.3%  (Target: <2%)  ✅ Excellent  │
│ Trend: ↘ -0.2% from last month                          │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ Mentor Feedback Deductions                               │
│ ██████░░░░░░░░░░░░░░ 2 points  (Target: <5)  ✅ Good    │
│ Trend: → Stable                                          │
└─────────────────────────────────────────────────────────┘

[Detailed Incident Breakdown]
- DNR Incidents (last 30 days): 2
  - Oct 28: Package marked delivered but customer claims not received (Resolved)
  - Oct 15: Package delivered to wrong apartment number (Coached)
  
- POD Issues (last 30 days): 3
  - Nov 2: Photo missing for 1 delivery (Technical issue - excused)
  - Oct 20: Photo quality poor (Coached)
  - Oct 12: Photo showed vehicle in frame (Coached)

[Performance Trend Chart]
[12-week line graph showing delivery success rate trending upward from 96.5% to 98.5%]

═══════════════════════════════════════════════════════════
[TAB: Safety]
═══════════════════════════════════════════════════════════

[Safety Score Summary]
Overall Safety Score: 96/100 🟢 Good
Last 90 Days Events: 4 total
Safety Rating: ⭐⭐⭐⭐ (4/5)

[Event Breakdown by Type]
Hard Braking:        2 events
Hard Acceleration:   0 events
Harsh Cornering:     1 event
Speeding:            1 event
Distracted Driving:  0 events
Following Too Close: 0 events

[Recent Safety Events - Detailed]

┌─────────────────────────────────────────────────────────┐
│ Event #4 - Hard Braking                                  │
│ Date: November 4, 2025, 2:34 PM                         │
│ Location: 123 Main St, City, ST (GPS link)             │
│ Severity: 🟡 Medium (G-Force: 0.68)                     │
│ Vehicle: V-234                                           │
│ Route: R-44856                                           │
│                                                           │
│ [📹 View Video] [View Location on Map]                  │
│                                                           │
│ Review Status: ✅ Coaching Completed (Nov 5)            │
│ Coaching Notes: Discussed anticipating traffic. Driver  │
│ acknowledged and committed to maintaining safe distance. │
│                                                           │
│ Driver Response: "Car in front stopped suddenly at      │
│ yellow light. Will maintain better following distance." │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ Event #3 - Speeding                                      │
│ Date: October 28, 2025, 11:15 AM                        │
│ Location: Highway 401, GPS coordinates                   │
│ Severity: 🟡 Medium (12 mph over limit)                 │
│ Speed: 77 mph in 65 mph zone                            │
│ Duration: 3 minutes                                      │
│ Vehicle: V-234                                           │
│ Route: R-44512                                           │
│                                                           │
│ [📹 View Video] [View Location on Map]                  │
│                                                           │
│ Review Status: ✅ Coaching Completed (Oct 29)           │
│ Coaching Notes: Reviewed speed limits and consequences. │
│ Driver understands impact on safety score.              │
└─────────────────────────────────────────────────────────┘

[Safety Trend Chart]
[3-month graph showing safety events per month: Aug (6), Sep (3), Oct (2), Nov (1 so far)]
Trend: ↗ Improving (Fewer events over time)

[Coaching Impact Analysis]
Events Before First Coaching: Avg 2.5 per month
Events After Coaching: Avg 1.0 per month
Improvement: 60% reduction ✅

═══════════════════════════════════════════════════════════
[TAB: Vehicles]
═══════════════════════════════════════════════════════════

[Vehicles Used by This Driver]

Current Primary Vehicle: V-234 (Ford Transit 250, 2023)
Assigned Since: March 15, 2024

[Vehicle Usage History]
Vehicle | Usage Period      | Total Routes | Avg Daily Miles | Issues Reported
────────────────────────────────────────────────────────────────────────────────
V-234   | Mar 15 - Present | 187         | 145            | 2
V-198   | Training Period  | 5           | 120            | 0

[Issues Reported by This Driver]

┌─────────────────────────────────────────────────────────┐
│ Issue Report #234                                        │
│ Date: October 15, 2025                                  │
│ Vehicle: V-234                                           │
│ Issue Type: 🔴 Mechanical - Brake Noise                 │
│ Description: "Hearing squeaking noise when braking,     │
│ especially at low speeds. Not affecting braking power   │
│ but should be checked."                                  │
│                                                           │
│ Resolution Status: ✅ Resolved (Oct 17)                 │
│ Action Taken: Brake pads replaced, noise resolved       │
│ Downtime: 2 days                                         │
│ Cost: $287.45                                            │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ Issue Report #187                                        │
│ Date: August 8, 2025                                    │
│ Vehicle: V-234                                           │
│ Issue Type: 🟡 Minor - Check Engine Light               │
│ Description: "Check engine light came on during route." │
│                                                           │
│ Resolution Status: ✅ Resolved (Aug 9)                  │
│ Action Taken: Diagnostic scan showed O2 sensor issue,   │
│ sensor replaced                                          │
│ Downtime: 1 day                                          │
│ Cost: $156.78                                            │
└─────────────────────────────────────────────────────────┘

[Vehicle Care Score]
Pre-Trip Inspections Completed: 187/187 (100%) ✅
Issues Reported: 2 (Proactive maintenance)
Vehicle Cleanliness: Good (based on post-trip inspections)
Fuel Card Usage: Normal (no anomalies)

═══════════════════════════════════════════════════════════
[TAB: Fuel]
═══════════════════════════════════════════════════════════

[Fuel Summary - Last 30 Days]
Total Fuel Purchases: 8
Total Gallons: 194.3 gallons
Total Cost: $717.23
Average Cost per Gallon: $3.69
Estimated MPG: 11.2 (Good for delivery van)
Estimated Cost per Mile: $0.33

[Fuel Purchase History]

┌─────────────────────────────────────────────────────────┐
│ Purchase #1                                              │
│ Date: November 6, 2025, 5:45 PM                         │
│ Location: Shell Station, 456 Oak Ave                    │
│ Receipt Uploaded: ✅ Yes [View Image]                   │
│                                                           │
│ Extracted Data (OCR):                                    │
│ - Invoice #: 789456123                                  │
│ - Gallons: 24.8                                         │
│ - Price/Gallon: $3.69                                   │
│ - Total: $91.51                                         │
│                                                           │
│ Vehicle: V-234                                           │
│ Odometer: 48,756 miles                                  │
│ Route: R-44987                                           │
│                                                           │
│ Verification Status: ✅ Approved (Auto)                 │
│ GPS Verification: ✅ Matches route area                 │
│ Time Verification: ✅ During shift hours                │
└─────────────────────────────────────────────────────────┘

[Additional 7 fuel purchases listed similarly]

[Fuel Analytics]
- Expected fuel consumption (based on route miles): 192 gal
- Actual fuel consumption: 194.3 gal
- Variance: +1.2% (within normal range) ✅
- Fuel efficiency trend: Stable
- Anomalies detected: None ✅

[Fuel Locations Map]
[Map showing all fuel purchase locations color-coded by route]

═══════════════════════════════════════════════════════════
[TAB: Time & Attendance]
═══════════════════════════════════════════════════════════

[Current Pay Period: Nov 1 - Nov 15, 2025]

Total Hours Worked: 38.5 hours (as of Nov 6)
Regular Hours: 38.5 hours
Overtime Hours: 0 hours
Projected Week Total: 42 hours ⚠️ (Approaching OT)

[Time Entries - This Week]

Day        | Clock In | Clock Out | Breaks      | Total Hours | Route
───────────────────────────────────────────────────────────────────────
Mon, Nov 4 | 7:45 AM  | 5:30 PM   | 30m lunch   | 9.25 hrs    | R-44856
                                   | 2x15m break |             |
Tue, Nov 5 | 7:42 AM  | 5:45 PM   | 30m lunch   | 9.55 hrs    | R-44901
                                   | 2x15m break |             |
Wed, Nov 6 | 7:48 AM  | 5:35 PM   | 30m lunch   | 9.28 hrs    | R-44987
                                   | 2x15m break |             |
Thu, Nov 7 | Scheduled | Scheduled| ---         | Est. 9.0 hrs| R-45024
Fri, Nov 8 | Scheduled | Scheduled| ---         | Est. 9.0 hrs| R-45098

[Attendance Record - Last 90 Days]
Days Scheduled: 60
Days Worked: 58
Absences: 2 (1 called in sick, 1 approved time off)
Attendance Rate: 96.7% ✅
Tardiness: 1 occurrence (15 minutes late on Oct 12)
Early Departures: 0

[Payroll Calculation - Current Period]
Regular Hours (38.5 hrs): $19.50/hr = $750.75
Overtime Hours (0 hrs): $29.25/hr = $0.00
Holiday Hours (0 hrs): $39.00/hr = $0.00
────────────────────────────────────────
Gross Pay (to date): $750.75

Projected Full Period Gross: ~$1,560 (assuming normal hours continue)

[Overtime Alerts]
⚠️ Driver is scheduled for 2 more days this week
⚠️ If both routes take ~9 hours, driver will have ~4 hours overtime
⚠️ Consider adjusting Friday schedule if minimizing OT is priority

[Historical Payroll]
[Table showing last 6 pay periods with hours and gross pay]

═══════════════════════════════════════════════════════════
[TAB: Coaching]
═══════════════════════════════════════════════════════════

[Coaching Summary]
Total Coaching Sessions: 5 (All time)
Last 90 Days: 2 sessions
Last Session: November 5, 2025
Overall Response: Positive (Driver responds well to feedback)

[Coaching History]

┌─────────────────────────────────────────────────────────┐
│ Coaching Session #5                                      │
│ Date: November 5, 2025                                  │
│ Type: 🟡 Safety - Hard Braking Event                    │
│ Conducted By: Sarah Johnson (Station Manager)           │
│                                                           │
│ Reason for Coaching:                                     │
│ Hard braking event on Nov 4 during Route R-44856        │
│ (Samsara Event #1456)                                   │
│                                                           │
│ Discussion Points:                                       │
│ - Reviewed event video together                         │
│ - Discussed importance of maintaining safe following    │
│   distance, especially in heavy traffic                  │
│ - Reviewed anticipation techniques for traffic flow      │
│ - Driver acknowledged the event and understood causes    │
│                                                           │
│ Driver Commitment:                                       │
│ "I will maintain a minimum 3-second following distance  │
│ and watch for brake lights further ahead to anticipate  │
│ stops earlier."                                          │
│                                                           │
│ Follow-up Plan:                                          │
│ Monitor safety events for next 30 days. If no similar   │
│ events occur, coaching is considered successful.         │
│                                                           │
│ Driver Acknowledgment: ✅ Signed on Nov 5, 2025         │
│ Manager Notes: Driver was receptive and professional.   │
│ Shows consistent improvement after coaching.             │
│                                                           │
│ [View Full Coaching Document] [Print]                    │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ Coaching Session #4                                      │
│ Date: October 20, 2025                                  │
│ Type: 🟡 Performance - POD Photo Quality                │
│ Conducted By: Sarah Johnson (Station Manager)           │
│                                                           │
│ Reason for Coaching:                                     │
│ Multiple photos flagged for poor quality in weekly      │
│ scorecard (Week 42)                                      │
│                                                           │
│ Discussion Points:                                       │
│ - Reviewed Amazon's photo requirements                   │
│ - Practiced proper photo angles in training room         │
│ - Emphasized importance of good lighting                 │
│ - Showed examples of excellent vs poor photos            │
│                                                           │
│ Driver Commitment:                                       │
│ "I will take extra care to ensure clear, well-lit photos│
│ that show the package and delivery location clearly."   │
│                                                           │
│ Follow-up Plan:                                          │
│ Manager will spot-check POD photos daily for next week. │
│                                                           │
│ Outcome: ✅ Successful                                   │
│ POD compliance improved from 97% to 99%+ after coaching │
│                                                           │
│ Driver Acknowledgment: ✅ Signed on Oct 20, 2025        │
│                                                           │
│ [View Full Coaching Document] [Print]                    │
└─────────────────────────────────────────────────────────┘

[Additional 3 coaching sessions listed with less detail]

[Coaching Effectiveness Analysis]
Sessions Required: Below Average (Good performance)
Response to Coaching: Excellent ✅
Repeat Issues: None
Trend: Improving (Longer gaps between coaching needed)

═══════════════════════════════════════════════════════════
[TAB: Certifications]
═══════════════════════════════════════════════════════════

[Required Certifications Status]

┌─────────────────────────────────────────────────────────┐
│ Driver's License                                         │
│ License #: DL123456789                                  │
│ State: CA                                                │
│ Class: C (Non-Commercial)                               │
│ Issue Date: January 15, 2020                            │
│ Expiration: December 31, 2026                           │
│ Status: ✅ Valid (1 year, 2 months remaining)           │
│ [Upload New License] [View Scanned Copy]                │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ Defensive Driving Course                                 │
│ Provider: Smith System                                   │
│ Completion Date: March 20, 2024                         │
│ Certificate #: SS-2024-089456                           │
│ Valid Through: March 20, 2026                           │
│ Status: ✅ Valid (1 year, 4 months remaining)           │
│ [Upload Renewal Certificate] [View Certificate]         │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ Amazon Delivery Training                                 │
│ Completion Date: March 18, 2024                         │
│ Training Modules Completed: 8/8                         │
│ Final Assessment Score: 94%                             │
│ Mentor Ride-Along: Completed (3 days, Mentor: D-045)   │
│ Status: ✅ Certified                                     │
│ Recertification Due: March 18, 2026                     │
│ [View Training Record] [Schedule Recertification]       │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ Vehicle Pre-Trip Inspection Certification                │
│ Completion Date: March 19, 2024                         │
│ Certified By: Fleet Manager Tom Wilson                  │
│ Status: ✅ Certified                                     │
│ [View Certification Document]                            │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ Background Check                                         │
│ Provider: Checkr                                         │
│ Completed: March 10, 2024                               │
│ Status: ✅ Cleared                                       │
│ Results: No disqualifying issues                        │
│ [View Background Check Report] (Restricted Access)       │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ Drug Screening                                           │
│ Provider: LabCorp                                        │
│ Test Date: March 12, 2024                               │
│ Status: ✅ Negative / Passed                            │
│ [View Test Results] (Restricted Access)                 │
└─────────────────────────────────────────────────────────┘

[Upcoming Renewals]
No certifications expiring within next 6 months ✅

[Alerts & Reminders]
System will automatically notify 60 days before any expiration

═══════════════════════════════════════════════════════════
[TAB: Documents]
═══════════════════════════════════════════════════────════

[Document Library for John Smith]

Onboarding Documents
├── Application Form [PDF] (Mar 10, 2024)
├── I-9 Employment Eligibility [PDF] (Mar 10, 2024)
├── W-4 Tax Withholding [PDF] (Mar 10, 2024)
├── Direct Deposit Form [PDF] (Mar 10, 2024)
├── Emergency Contact Form [PDF] (Mar 10, 2024)
├── Uniform Size & Issuance [PDF] (Mar 15, 2024)
└── Equipment Checkout Form [PDF] (Mar 15, 2024)
    - Rabbit Device: RBT-456
    - Fuel Card: FC-089
    - Van Key: V-234

Certifications & Training
├── Driver's License (Current) [Image] (Jan 15, 2020)
├── Defensive Driving Certificate [PDF] (Mar 20, 2024)
├── Amazon Training Completion [PDF] (Mar 18, 2024)
├── Pre-Trip Inspection Cert [PDF] (Mar 19, 2024)
├── Background Check Report [PDF] (Mar 10, 2024) [Restricted]
└── Drug Test Results [PDF] (Mar 12, 2024) [Restricted]

Performance Documents
├── Coaching Session #1 [PDF] (Apr 15, 2024)
├── Coaching Session #2 [PDF] (Jun 3, 2024)
├── Coaching Session #3 [PDF] (Aug 8, 2024)
├── Coaching Session #4 [PDF] (Oct 20, 2024)
├── Coaching Session #5 [PDF] (Nov 5, 2024)
├── Performance Review - Q2 2024 [PDF] (Jul 1, 2024)
└── Recognition Award - Top Performer [PDF] (Sep 15, 2024)

Payroll Documents
├── Pay Stubs (Last 6 months) [Folder]
└── Annual Tax Documents (2024) [Folder]

Other Documents
├── Uniform Replacement Request [PDF] (Sep 1, 2024)
└── Schedule Change Request [PDF] (Oct 5, 2024)

[Upload New Document]
Document Type: [Dropdown]
Description: [Text Field]
File: [Choose File]
[Upload]
```

**User Actions on Driver Profile:**
- Edit personal information
- Update employment status
- View complete history across all tabs
- Send message to driver
- Initiate coaching session
- Export driver profile report (PDF)
- Print driver profile
- Compare driver to others
- Add notes/comments (internal use only)

#### F-MGR-004: Fleet & Vehicle Management

**Vehicle Directory Screen:**

```
┌─────────────────────────────────────────────────────────┐
│  Fleet Management (Station: [Station Name])              │
│                                                           │
│  [Search vehicles...] [Add New Vehicle]                  │
│                                                           │
│  Filters:                                                 │
│  Status: [All | Active | In Repair | Maintenance | Rent]│
│  Maintenance: [All | Overdue | Due Soon | Up to Date]   │
│  Type: [All | Owned | Leased | Rental]                  │
└─────────────────────────────────────────────────────────┘

[Quick Stats Cards]
┌──────────────┬──────────────┬──────────────┬──────────────┐
│ Total Fleet  │ Active       │ In Repair    │ Overdue Maint│
│     48       │  38 (79%)    │  5 (10%)     │  3 ⚠️        │
└──────────────┴──────────────┴──────────────┴──────────────┘

[Vehicle List - Card View Option or Table View Option]

Vehicle: V-234 | Ford Transit 250 (2023)
Status: 🟢 Active - On Route
License: ABC-1234 | VIN: 1FTBW3XM***123456
Mileage: 48,756 mi | Next Oil Change: 51,000 mi (⚠️ Due Soon)
Current Driver: John Smith (D-089)
Last Service: Oct 15, 2025
[View Details] [Schedule Maintenance] [Report Issue]

Vehicle: V-256 | Ford Transit 250 (2023)
Status: 🟢 Active - Available
License: XYZ-5678 | VIN: 1FTBW3XM***789012
Mileage: 52,340 mi | Next Oil Change: 55,000 mi
Current Driver: Unassigned
Last Service: Oct 28, 2025
[View Details] [Assign to Route] [Report Issue]

Vehicle: V-245 | Ram ProMaster 2500 (2022)
Status: 🔴 In Repair - Safety Hold
License: DEF-9012 | VIN: 3C6TRVBG***456789
Mileage: 67,123 mi | Issue: Brake system problem (reported Nov 6)
Expected Return: Nov 10, 2025
[View Details] [View Issue Report] [Update Status]

Vehicle: V-198 | Ford Transit 250 (2021)
Status: 🟡 Scheduled Maintenance
License: GHI-3456 | VIN: 1FTBW3XM***345678
Mileage: 89,456 mi | Service: 90k mile service (scheduled Nov 9)
Shop: Quick Lube Plus | Appointment: Nov 9, 9:00 AM
[View Details] [View Appointment] [Cancel/Reschedule]

[Continue list of all vehicles...]
```

**Vehicle Detail Screen:**

```
┌─────────────────────────────────────────────────────────┐
│  🚐 Vehicle V-234 - Ford Transit 250 (2023)              │
│  Status: Active | License: ABC-1234                      │
│                                                           │
│  [Edit Vehicle] [Schedule Maintenance] [Report Issue]    │
│  [Take Offline] [View Costs] [Export Records]           │
└─────────────────────────────────────────────────────────┘

[Navigation Tabs]
Overview | Maintenance History | Active Issues | Assignments | Costs | Inspections | Documents

═══════════════════════════════════════════════════════════
[TAB: Overview]
═══════════════════════════════════════════════════════════

[Vehicle Information]
Make/Model: Ford Transit 250
Year: 2023
VIN: 1FTBW3XM***123456
License Plate: ABC-1234 (California)
Color: White
Type: Cargo Van

[Acquisition Information]
Acquired: January 15, 2023
Acquisition Type: Purchased
Purchase Price: $42,500
Current Book Value: $36,000 (estimated)
Warranty: Until Jan 15, 2026 or 60,000 miles

[Current Status]
Status: 🟢 Active - On Route
Current Mileage: 48,756 miles
Current Driver: John Smith (D-089)
Current Route: R-44987 (Assigned today)
Last Location Update: 2:34 PM (GPS via Samsara)

[Maintenance Status]
Next Oil Change: Due at 51,000 mi (2,244 mi remaining) ⚠️ Due Soon
Last Oil Change: Oct 15, 2025 at 45,000 mi
Next Tire Rotation: Due at 54,000 mi (5,244 mi remaining)
Next Inspection: Annual - Due Dec 10, 2025
Maintenance Alerts: 1 - Oil change approaching

[Performance Metrics]
Total Miles Driven: 48,756 miles
Average Daily Miles: 145 miles
Days in Service: 335 days
Days in Repair: 12 days (3.6% downtime)
Average Fuel Efficiency: 11.4 MPG
Total Routes Completed: 298

[Quick Actions]
[Schedule Oil Change] [Assign Different Driver] [View All Routes] [Download Vehicle Report]

═══════════════════════════════════════════════════════════
[TAB: Maintenance History]
═══════════════════════════════════════════════════════════

[Upcoming Maintenance]
⚠️ Oil Change - Due in 2,244 miles (Est. 16 days based on avg usage)
   Recommended Service: Joe's Auto Service ($89 typical cost)
   [Schedule Now]

○ Tire Rotation - Due in 5,244 miles (Est. 36 days)
   [Schedule Now]

○ Annual State Inspection - Due Dec 10, 2025 (33 days)
   [Schedule Now]

[Completed Maintenance History]

┌─────────────────────────────────────────────────────────┐
│ Service #45 - Oil Change & Filter                        │
│ Date: October 15, 2025                                  │
│ Mileage: 45,000 miles                                   │
│ Service Provider: Joe's Auto Service                     │
│ Work Order #: JA-2025-4567                              │
│                                                           │
│ Services Performed:                                      │
│ - Oil change (Full synthetic 5W-30, 6 quarts)           │
│ - Oil filter replacement                                 │
│ - Multi-point inspection completed                       │
│ - Tire pressure check and adjustment                     │
│                                                           │
│ Parts Cost: $47.50                                       │
│ Labor Cost: $35.00                                       │
│ Total Cost: $82.50                                       │
│                                                           │
│ Downtime: 4 hours (same day service)                    │
│ Next Oil Change Recommended: 50,000 miles               │
│                                                           │
│ Technician Notes: "All systems check out. Brake pads at │
│ 50% - monitor for next service. Tires show even wear."  │
│                                                           │
│ [View Invoice] [View Photos] [Download Receipt]         │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ Service #44 - Brake Pad Replacement                      │
│ Date: October 17, 2025                                  │
│ Mileage: 45,156 miles                                   │
│ Service Provider: Joe's Auto Service                     │
│ Work Order #: JA-2025-4589                              │
│ Priority: 🔴 High (Safety Issue)                        │
│                                                           │
│ Services Performed:                                      │
│ - Front brake pad replacement (both sides)               │
│ - Brake system inspection                                │
│ - Test drive and verification                            │
│                                                           │
│ Parts Cost: $156.78                                      │
│ Labor Cost: $130.67                                      │
│ Total Cost: $287.45                                      │
│                                                           │
│ Downtime: 2 days (parts ordered)                        │
│                                                           │
│ Technician Notes: "Brake pads were down to 15%. Rotors  │
│ in good condition, no need for replacement. All brake    │
│ system components functioning properly."                 │
│                                                           │
│ Trigger: Driver reported squeaking noise (Issue #234)   │
│                                                           │
│ [View Invoice] [View Photos] [Download Receipt]         │
└─────────────────────────────────────────────────────────┘

[Continue maintenance history...]

[Maintenance Summary]
Total Maintenance Events: 45
Total Maintenance Cost: $4,567.89
Average Cost per Service: $101.51
Last 12 Months Cost: $1,245.67
Preventive vs Reactive: 85% Preventive ✅

[Maintenance Trend Chart]
[Bar chart showing monthly maintenance costs over 12 months]

═══════════════════════════════════════════════════════════
[TAB: Active Issues]
═══════════════════════════════════════════════════════════

[Current Issues: None ✅]

[Recently Resolved Issues]

┌─────────────────────────────────────────────────────────┐
│ Issue #234 - RESOLVED                                    │
│ Reported: October 15, 2025 at 3:45 PM                  │
│ Reported By: John Smith (Driver D-089)                  │
│ Issue Type: 🔴 Mechanical - Brake Noise                 │
│ Severity: High (Safety-related)                         │
│                                                           │
│ Driver Description:                                      │
│ "Hearing squeaking noise when braking, especially at low│
│ speeds. Not affecting braking power but should be       │
│ checked. Noticed it starting around noon today."        │
│                                                           │
│ Photos Attached: 2 [View Photos]                        │
│ Audio Recording: Yes (brake noise) [Play Audio]         │
│ Location When Reported: GPS coordinates                  │
│                                                           │
│ Status Timeline:                                         │
│ Oct 15, 3:45 PM - Issue reported by driver              │
│ Oct 15, 4:00 PM - Acknowledged by Fleet Manager         │
│ Oct 15, 4:15 PM - Vehicle taken out of service          │
│ Oct 15, 5:30 PM - Inspection scheduled with Joe's Auto  │
│ Oct 16, 9:00 AM - Vehicle dropped at shop               │
│ Oct 16, 2:00 PM - Diagnosis: Worn brake pads            │
│ Oct 17, 11:00 AM - Repair completed                     │
│ Oct 17, 1:00 PM - Test drive completed, cleared         │
│ Oct 17, 2:00 PM - Vehicle returned to service           │
│                                                           │
│ Resolution:                                              │
│ Front brake pads replaced. Issue resolved. Vehicle safe │
│ for operation.                                           │
│                                                           │
│ Total Downtime: 2 days                                   │
│ Repair Cost: $287.45                                     │
│                                                           │
│ Driver Feedback: "Thank you for quick repair. Brakes    │
│ feel great now!"                                         │
│                                                           │
│ [Reopen Issue] [View Full History] [Download Report]    │
└─────────────────────────────────────────────────────────┘

[Issue Reporting Statistics]
Total Issues Reported (All Time): 8
Issues per 10,000 Miles: 1.64 (Below average ✅)
Average Resolution Time: 1.5 days
Proactive Reports by Drivers: 100% ✅

═══════════════════════════════════════════════════════════
[TAB: Assignments]
═══════════════════════════════════════════════════════════

[Primary Driver Assignment]
Current Primary Driver: John Smith (D-089)
Assigned Since: March 15, 2024 (236 days)
Routes Completed: 187
Driver Performance with This Vehicle: 4.8/5.0 ⭐

[Assignment History]

Date Range          | Driver           | Routes | Avg Performance
─────────────────────────────────────────────────────────────────
Mar 15 - Present    | John Smith (D-089) | 187   | 4.8/5.0
Jan 15 - Mar 14     | Training Pool      | 45    | N/A
─────────────────────────────────────────────────────────────────

[Recent Route Usage - Last 10 Days]

Date       | Driver           | Route    | Miles | Duration | Notes
────────────────────────────────────────────────────────────────────
Nov 6, 2025| John Smith       | R-44987  | 142   | 8h 15m   | Completed
Nov 5, 2025| John Smith       | R-44901  | 156   | 8h 32m   | Completed
Nov 4, 2025| John Smith       | R-44856  | 138   | 7h 48m   | Completed
Nov 3, 2025| Not Used (Sunday)| ---      | 0     | ---      | Day Off
Nov 2, 2025| John Smith       | R-44798  | 168   | 9h 6m    | Completed
Nov 1, 2025| John Smith       | R-44712  | 145   | 8h 21m   | Completed
Oct 31, 2025| John Smith      | R-44689  | 152   | 8h 45m   | Completed

[Usage Statistics]
Days Used (Last 30): 23 days
Days Available: 26 days (excluding maintenance)
Utilization Rate: 88.5% ✅
Average Daily Miles: 147 miles
Total Miles (Last 30): 3,381 miles

═══════════════════════════════════════════════════════════
[TAB: Costs]
═══════════════════════════════════════════════════════════

[Cost Summary]

Total Cost of Ownership (Since Acquisition):
Purchase Price:              $42,500.00
Total Maintenance:           $4,567.89
Total Fuel (estimated):      $18,234.56
Insurance (prorated):        $3,456.00
Registration/Tags:           $287.00
Total Cost:                  $69,045.45

Cost per Mile:               $1.42
Cost per Day (avg):          $206.11
Cost per Route (avg):        $231.65

[Cost Breakdown - Last 12 Months]

Category              | Amount      | % of Total
──────────────────────────────────────────────────
Fuel                  | $7,234.56   | 68.5%
Maintenance           | $1,245.67   | 11.8%
Insurance             | $1,728.00   | 16.4%
Registration          | $95.67      | 0.9%
Repairs (Unplanned)   | $256.78     | 2.4%
──────────────────────────────────────────────────
Total (12 months):    | $10,560.68  | 100%

[Monthly Cost Trend Chart]
[Line graph showing total monthly costs over 12 months]

[Fuel Cost Details]
Total Fuel Purchased (12 months): 1,960 gallons
Total Fuel Cost: $7,234.56
Average Price per Gallon: $3.69
Fuel Efficiency: 11.4 MPG
Cost per Mile (Fuel): $0.50

[Maintenance Cost Details]
Preventive Maintenance: $1,058.90 (85%)
Unplanned Repairs: $186.77 (15%)
Most Expensive Service: $287.45 (Brake pads, Oct 17)

[Cost Comparison to Fleet Average]
This Vehicle Cost/Mile: $1.42
Fleet Average Cost/Mile: $1.67
Variance: -15% (This vehicle is below average cost ✅)

[ROI Analysis]
Current Book Value: $36,000 (estimated)
Total Investment: $69,045.45
Depreciation: $6,500 (15.3%)
Routes Completed: 298
Revenue per Route (est): $145
Estimated Revenue Generated: $43,210
Break-even Point: Projected at route #476 (month 18)

═══════════════════════════════════════════════════════════
[TAB: Inspections]
═══════════════════════════════════════════════════════════

[Pre-Trip Inspections (Last 30 Days)]

All Inspections Completed: 23/23 (100%) ✅
Inspections with Issues: 2 (8.7%)
Average Inspection Time: 4 minutes

[Recent Inspections]

┌─────────────────────────────────────────────────────────┐
│ Pre-Trip Inspection                                      │
│ Date: November 6, 2025 at 7:30 AM                       │
│ Inspector: John Smith (Driver D-089)                    │
│ Route: R-44987                                           │
│ Odometer: 48,714 miles                                  │
│                                                           │
│ Inspection Results: ✅ PASS - No Issues                 │
│                                                           │
│ Checklist Completed:                                     │
│ ✅ Exterior Condition (body, lights, mirrors)           │
│ ✅ Tires (pressure, tread, damage)                      │
│ ✅ Fluid Levels (oil, coolant, washer fluid)            │
│ ✅ Brakes (function test)                               │
│ ✅ Safety Equipment (fire extinguisher, first aid)      │
│ ✅ Interior Condition (seats, cargo area)               │
│ ✅ Documents (registration, insurance)                   │
│                                                           │
│ Inspector Notes: "All systems good. Vehicle clean and   │
│ ready for route."                                        │
│                                                           │
│ [View Full Inspection] [View Photos]                     │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ Pre-Trip Inspection                                      │
│ Date: October 15, 2025 at 7:25 AM                       │
│ Inspector: John Smith (Driver D-089)                    │
│ Route: R-44512                                           │
│ Odometer: 44,998 miles                                  │
│                                                           │
│ Inspection Results: ⚠️ PASS WITH ADVISORIES             │
│                                                           │
│ Issues Noted:                                            │
│ ⚠️ Brakes - Squeaking noise when braking                │
│    Severity: Medium (not affecting function)             │
│    Action: Issue report submitted (#234)                 │
│    Resolution: Vehicle approved for route, repair       │
│    scheduled after completion                            │
│                                                           │
│ All Other Checks: ✅ PASS                                │
│                                                           │
│ Inspector Notes: "Hearing brake squeak. Not affecting   │
│ stopping power but should be checked soon."             │
│                                                           │
│ Manager Override: Approved by Sarah Johnson             │
│ Override Reason: "Safe for today's route. Repair        │
│ scheduled for tomorrow."                                 │
│                                                           │
│ [View Full Inspection] [View Photos] [View Issue #234]  │
└─────────────────────────────────────────────────────────┘

[Post-Trip Inspections]

Post-trip inspections follow similar format, capturing end-of-day
condition, any new issues discovered, fuel level, odometer reading,
and cleanliness status.

[Annual State Inspection]
Last Inspection: December 10, 2024
Result: ✅ PASSED
Next Due: December 10, 2025 (33 days)
Inspection Station: California DMV Authorized #4567
[View Certificate] [Schedule Next Inspection]

═══════════════════════════════════════════════════════════
[TAB: Documents]
═══════════════════════════════════════════════════════════

[Vehicle Documents Library]

Ownership & Registration
├── Title Document [PDF]
├── Registration (Current) [PDF] - Expires Dec 31, 2025
├── Registration (Previous) [PDF] - Historical
├── Purchase Agreement [PDF]
└── Bill of Sale [PDF]

Insurance
├── Insurance Policy (Current) [PDF] - Policy #INS-789456
├── Insurance Card [PDF]
└── Previous Policies [Folder]

Maintenance Records
├── All Service Invoices [Folder] - 45 documents
├── Warranty Information [PDF]
├── Owner's Manual [PDF]
└── Maintenance Schedule [PDF]

Inspections
├── Annual State Inspections [Folder]
├── Pre-Trip Inspection Photos [Folder]
└── Post-Trip Inspection Photos [Folder]

Other Documents
├── Vehicle Photos (Acquisition) [Folder]
├── Samsara Device Installation [PDF]
├── Wrap/Decal Installation [PDF]
└── Modifications Log [PDF]

[Upload New Document]
Document Category: [Dropdown]
Document Name: [Text Field]
File: [Choose File]
[Upload]
```

**User Actions on Vehicle Profiles:**
- Schedule maintenance appointments
- Report new issues
- Update vehicle status
- Assign to different driver
- View cost analysis
- Export vehicle history
- Add maintenance reminders
- Upload documents

---

#### F-MGR-005: Payroll Management

**Payroll Dashboard:**

```
┌─────────────────────────────────────────────────────────┐
│  Payroll Management (Station: [Station Name])            │
│                                                           │
│  Current Pay Period: Nov 1 - Nov 15, 2025               │
│  Status: 🟡 In Progress (7 of 15 days complete)         │
│                                                           │
│  [View Previous Periods] [Export to ADP] [Settings]     │
└─────────────────────────────────────────────────────────┘

[Payroll Summary - Current Period]
┌──────────────┬──────────────┬──────────────┬──────────────┐
│ Total Hours  │ Regular Hrs  │ Overtime Hrs │ Holiday Hrs  │
│   1,245.5    │  1,198.0     │  47.5        │  0.0         │
└──────────────┴──────────────┴──────────────┴──────────────┘

┌──────────────┬──────────────┬──────────────┬──────────────┐
│ Est. Gross   │ Avg Hourly   │ OT %         │ Drivers Paid │
│  $24,567.45  │  $19.73      │  3.8%        │  38          │
└──────────────┴──────────────┴──────────────┴──────────────┘

[Alerts & Warnings]
⚠️ 3 drivers approaching 40 hours this week
⚠️ 5 time entries pending manager approval
⚠️ 2 drivers with missing punch-out entries
✅ All previous pay periods finalized

[Actions Required]
┌─────────────────────────────────────────────────────────┐
│ 🔴 HIGH PRIORITY                                         │
│ Review and approve 5 time entry corrections             │
│ [REVIEW NOW]                                             │
│                                                           │
│ 🟡 MEDIUM PRIORITY                                       │
│ Contact 2 drivers about missing clock-out times          │
│ [VIEW DETAILS]                                           │
│                                                           │
│ 🟢 REMINDER                                              │
│ Payroll export to ADP due in 8 days (Nov 15)           │
│ [SET REMINDER]                                           │
└─────────────────────────────────────────────────────────┘
```

**Detailed Time Tracking View:**

```
┌─────────────────────────────────────────────────────────┐
│  Time & Attendance Detail                                │
│  Pay Period: Nov 1 - Nov 15, 2025                       │
│                                                           │
│  [Filter by Driver] [Filter by Status] [Export Excel]   │
└─────────────────────────────────────────────────────────┘

[Time Entry Table - Sortable Columns]

Driver Name  | ID    | Days Worked | Reg Hrs | OT Hrs | Hol Hrs | Total | Status  | Actions
──────────────────────────────────────────────────────────────────────────────────────────────
John Smith   | D-089 | 5 of 7     | 38.5    | 0.0    | 0.0     | 38.5  | ✅ Good | [Details]
Jane Doe     | D-124 | 5 of 7     | 38.0    | 0.0    | 0.0     | 38.0  | ✅ Good | [Details]
Mike Johnson | D-067 | 5 of 7     | 41.5    | 1.5    | 0.0     | 43.0  | ⚠️ OT   | [Details]
Sarah Wilson | D-201 | 5 of 7     | 37.8    | 0.0    | 0.0     | 37.8  | ✅ Good | [Details]
Tom Brown    | D-156 | 4 of 7     | 28.2    | 0.0    | 0.0     | 28.2  | ⚠️ Low  | [Details]
Lisa Garcia  | D-234 | 3 of 7     | 22.5    | 0.0    | 0.0     | 22.5  | ⚠️ Low  | [Details]
...

[Click any driver row to see detailed time entries]
```

**Individual Driver Time Detail:**

```
┌─────────────────────────────────────────────────────────┐
│  Time Detail: John Smith (D-089)                         │
│  Pay Period: Nov 1 - Nov 15, 2025                       │
│                                                           │
│  [Edit Entry] [Add Manual Entry] [Export Report]        │
└─────────────────────────────────────────────────────────┘

[Summary for This Driver]
Total Hours: 38.5 hours
Regular: 38.5 | Overtime: 0.0 | Holiday: 0.0
Estimated Gross Pay: $750.75 (at $19.50/hr)
Days Worked: 5 | Days Scheduled: 7 | Absent: 0

[Detailed Time Entries]

Day/Date    | Clock In | Clock Out | Breaks           | Total Hrs | Route    | Status
──────────────────────────────────────────────────────────────────────────────────────
Mon, Nov 4  | 7:45 AM  | 5:30 PM   | 30m lunch       | 9.25      | R-44856  | ✅ Approved
                                    | 2x15m (paid)     |           |          |
─────────────────────────────────────────────────────────────────────────────────────
Tue, Nov 5  | 7:42 AM  | 5:45 PM   | 30m lunch       | 9.55      | R-44901  | ✅ Approved
                                    | 2x15m (paid)     |           |          |
─────────────────────────────────────────────────────────────────────────────────────
Wed, Nov 6  | 7:48 AM  | 5:35 PM   | 30m lunch       | 9.28      | R-44987  | ✅ Approved
                                    | 2x15m (paid)     |           |          |
─────────────────────────────────────────────────────────────────────────────────────
Thu, Nov 7  | 7:50 AM  | 5:15 PM   | 30m lunch       | 8.92      | R-45024  | ⏳ Pending
                                    | 2x15m (paid)     |           |          | [APPROVE]
─────────────────────────────────────────────────────────────────────────────────────
Fri, Nov 8  | Scheduled| Scheduled | ---              | Est. 9.0  | R-45098  | Future
─────────────────────────────────────────────────────────────────────────────────────
Sat, Nov 9  | Day Off  | ---       | ---              | 0.0       | ---      | Day Off
─────────────────────────────────────────────────────────────────────────────────────
Sun, Nov 10 | Day Off  | ---       | ---              | 0.0       | ---      | Day Off

[Payroll Calculation Details]

Regular Hours Calculation:
─────────────────────────────
Mon Nov 4:   9.25 hrs
Tue Nov 5:   9.55 hrs
Wed Nov 6:   9.28 hrs
Thu Nov 7:   8.92 hrs (pending approval)
Fri Nov 8:   9.00 hrs (estimated)
────────────────────────────
Week 1 Total: 46.00 hrs

Since Week 1 total is 46 hours:
- Regular hours: 40.00 hrs @ $19.50 = $780.00
- Overtime hours: 6.00 hrs @ $29.25 = $175.50
────────────────────────────
Week 1 Estimated Gross: $955.50

[Note: Break deductions]
- 30-minute unpaid lunch deducted from each day with 6+ hour shift
- Two 15-minute breaks are paid (California law)
```

**Export to ADP:**

```
┌─────────────────────────────────────────────────────────┐
│  Export Payroll to ADP                                   │
│  Pay Period: Nov 1 - Nov 15, 2025                       │
│                                                           │
│  [Preview Export] [Generate ADP File] [Help]            │
└─────────────────────────────────────────────────────────┘

[Pre-Export Validation]

✅ All time entries approved: 38 drivers
✅ No missing clock-in/out entries
✅ All overtime calculated correctly
✅ Holiday pay rules applied (if applicable)
⚠️ 2 drivers with adjusted hours (manual corrections) - Review recommended

[Export Options]
File Format: [ADP Standard CSV ▼]
Include: [☑] Regular Hours
         [☑] Overtime Hours
         [☑] Holiday Hours
         [☑] Employee IDs
         [☐] Bank Account Info (handled separately in ADP)

[Preview Sample Data]
Employee ID | Last Name | First Name | Reg Hours | OT Hours | Holiday Hours | Gross Pay
────────────────────────────────────────────────────────────────────────────────────────
D-089       | Smith     | John       | 40.00     | 6.00     | 0.00          | $955.50
D-124       | Doe       | Jane       | 40.00     | 4.50     | 0.00          | $911.63
D-067       | Johnson   | Mike       | 40.00     | 8.25     | 0.00          | $1,021.31
...

[Generate Export File]
Estimated file size: 45 KB
File will be generated as: Payroll_Nov1-15_2025.csv
[GENERATE FILE] [Cancel]

[After Generation]
✅ File generated successfully!
📄 Payroll_Nov1-15_2025.csv
[Download File] [Email to HR] [Upload to ADP Portal]

[Record of Export]
Exported By: Sarah Johnson (Station Manager)
Export Date: November 7, 2025 at 2:45 PM
Pay Period: Nov 1-15, 2025
Total Drivers: 38
Total Gross Pay: $24,567.45
```

#### F-MGR-006: Performance Management & Scorecard

**Performance Dashboard:**

```
┌─────────────────────────────────────────────────────────┐
│  Performance Management (Station: [Station Name])        │
│                                                           │
│  [Scorecard] [POD Metrics] [Safety] [Coaching Queue]    │
└─────────────────────────────────────────────────────────┘

═══════════════════════════════════════════════════════════
[TAB: Scorecard]
═══════════════════════════════════════════════════════════

[Upload New Scorecard]
Week: [Week Picker]
File: [Choose CSV file from Cortex]
[Upload & Process]

[Current Week Performance - Week 45, 2025]

┌─────────────────────────────────────────────────────────┐
│ Overall Score: 847 / 1000                                │
│ Status: 🟢 FANTASTIC (Tier 1)                           │
│ Rank: #15 of 347 DSPs in region                        │
│ Week-over-week: ↗ +12 points                            │
└─────────────────────────────────────────────────────────┘

[Detailed Metrics Breakdown]

Customer Delivery Experience (400 points possible)
┌─────────────────────────────────────────────────────────┐
│ Delivered & Received: 98.5%                              │
│ ████████████████████░ 387/400 points  🟢 Excellent      │
│ Target: >97% | Benchmark: 97.8%                         │
│                                                           │
│ DNR Rate: 0.8%                                           │
│ Issues: 12 DNR incidents this week                       │
│ Top reasons: Wrong address (5), Customer unavailable (4) │
│ [View DNR Details] [Coach Affected Drivers]              │
└─────────────────────────────────────────────────────────┘

Photo Quality & Compliance (200 points possible)
┌─────────────────────────────────────────────────────────┐
│ POD Compliance: 99.1%                                    │
│ ███████████████████░░ 195/200 points  🟢 Excellent      │
│ Target: >98% | Benchmark: 98.5%                         │
│                                                           │
│ Photo Issues: 8 photos flagged                           │
│ - Poor lighting: 3                                       │
│ - Vehicle in frame: 2                                    │
│ - No package visible: 2                                  │
│ - Other: 1                                               │
│ [View Flagged Photos] [Coach Drivers]                    │
└─────────────────────────────────────────────────────────┘

Mentor Feedback (200 points possible)
┌─────────────────────────────────────────────────────────┐
│ Mentor Score: 168/200 points  🟡 Good                    │
│ ████████████████░░░░                                     │
│ Target: >180 | Benchmark: 175                           │
│                                                           │
│ Deductions by Category:                                  │
│ - Distracted Driving: 12 points                         │
│ - Speeding: 8 points                                     │
│ - Following Distance: 7 points                           │
│ - Other Safety: 5 points                                 │
│                                                           │
│ ⚠️ Area for Improvement - See Safety Tab for details    │
│ [View Mentor Events] [Review Coaching Plan]              │
└─────────────────────────────────────────────────────────┘

Customer Feedback (100 points possible)
┌─────────────────────────────────────────────────────────┐
│ Customer Rating: 4.9/5.0                                 │
│ ████████████████████░ 97/100 points  🟢 Excellent       │
│                                                           │
│ Positive Feedback: 234 compliments received              │
│ Negative Feedback: 3 complaints                          │
│ Top Compliments: "On-time", "Careful with packages"     │
│ [View Customer Comments]                                 │
└─────────────────────────────────────────────────────────┘

Organizational Compliance (100 points possible)
┌─────────────────────────────────────────────────────────┐
│ Compliance Score: 100/100 points  🟢 Perfect             │
│ ████████████████████                                     │
│                                                           │
│ ✅ All drivers properly badged                           │
│ ✅ All vehicles inspected                                │
│ ✅ No uniform violations                                 │
│ ✅ No attendance issues                                  │
│ ✅ All safety training current                           │
└─────────────────────────────────────────────────────────┘

[12-Week Performance Trend]
[Line chart showing total score over last 12 weeks]
Weeks 33-44: Shows general upward trend from 798 to 847

[Action Items Based on Scorecard]
🔴 HIGH PRIORITY
- Address 5 drivers with multiple mentor deductions
- Review and coach on distracted driving prevention

🟡 MEDIUM PRIORITY
- Continue photo quality monitoring (currently good)
- Follow up on 12 DNR incidents - identify patterns

🟢 MAINTAIN
- Customer feedback remains excellent
- Compliance perfect - keep standard procedures

[Compare to Previous Weeks]
Week 45: 847 points ↗
Week 44: 835 points
Week 43: 821 points
Week 42: 809 points
Trend: ↗ Improving (Consistent upward movement)

═══════════════════════════════════════════════════════════
[TAB: POD Metrics]
═══════════════════════════════════════════════════════════

[POD Compliance Dashboard]

Overall POD Rate: 99.1%
Total Deliveries This Week: 8,456
Photos Captured: 8,380
Missing Photos: 76 (0.9%)

[POD Issues Breakdown]

Issue Type               | Count | % of Total | Drivers Affected
─────────────────────────────────────────────────────────────────
Missing Photo            | 45    | 0.53%      | 12
Poor Lighting            | 18    | 0.21%      | 8
Vehicle in Frame         | 6     | 0.07%      | 4
Package Not Visible      | 5     | 0.06%      | 3
Wrong Location Photo     | 2     | 0.02%      | 2
─────────────────────────────────────────────────────────────────
Total Issues:            | 76    | 0.90%      | 23 (unique)

[Top Offenders - Requires Coaching]

Driver            | POD Rate | Issues This Week | Action Required
─────────────────────────────────────────────────────────────────
Mike Johnson      | 96.2%    | 8 missing photos | 🔴 Immediate coaching
Lisa Garcia       | 97.5%    | 5 poor lighting  | 🟡 Coaching recommended
Tom Brown         | 97.8%    | 4 vehicle in frame| 🟡 Coaching recommended

[Drivers with Perfect POD]
- 15 drivers achieved 100% POD compliance this week ✅
- Recognize and share best practices
[View Top Performers] [Send Recognition]

[POD Trend Analysis]
[Chart showing POD compliance rate over 12 weeks]
Trend: Stable high performance (98-99% range consistently)

[Sample Flagged Photos]
[Grid of thumbnail images showing examples of each issue type]
[Click to view full size and associated delivery details]

═══════════════════════════════════════════════════════════
[TAB: Safety Events]
═══════════════════════════════════════════════════════════

[Safety Event Queue - Requires Review]

Filter: [All Events | Pending Review | Coaching Required | Completed]
Sort by: [Date ▼ | Severity | Driver]

┌─────────────────────────────────────────────────────────┐
│ Event #2389 - PENDING REVIEW                             │
│ Type: 🔴 Distracted Driving (Phone Use)                  │
│ Driver: Mike Johnson (D-067)                            │
│ Date: November 6, 2025 at 1:45 PM                       │
│ Vehicle: V-289                                           │
│ Route: R-44965                                           │
│ Location: I-405 Northbound, GPS coordinates             │
│ Severity: High                                           │
│ Source: Netradyne Camera                                 │
│                                                           │
│ [📹 View Video (15 sec clip)] [View Full Context]       │
│                                                           │
│ Auto-Analysis:                                           │
│ Driver appears to be looking at phone screen while      │
│ driving. Duration: ~3 seconds. Traffic: Moderate.       │
│                                                           │
│ Review Actions:                                          │
│ [✅ Coaching Required] [⚠️ No Action - Excused]         │
│ [📝 Add Notes] [🚫 Dispute Event]                       │
│                                                           │
│ Quick Coach: [Send Standard Template]                    │
│ [Schedule In-Person Coaching] [Mark Reviewed]            │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ Event #2388 - PENDING REVIEW                             │
│ Type: 🟡 Hard Braking                                    │
│ Driver: Sarah Wilson (D-201)                            │
│ Date: November 6, 2025 at 11:22 AM                      │
│ Vehicle: V-234                                           │
│ Route: R-44987                                           │
│ Location: Main St & Oak Ave intersection                 │
│ Severity: Medium (G-force: 0.71)                        │
│ Source: Samsara Telematics                              │
│                                                           │
│ [📹 View Video] [View Location Map]                     │
│                                                           │
│ Context:                                                 │
│ - Traffic light changed to yellow                        │
│ - Vehicle in front stopped suddenly                      │
│ - No collision                                           │
│                                                           │
│ Review Actions:                                          │
│ [✅ Coaching Required] [⚠️ No Action - Excused]         │
│ [Mark as Training Opportunity] [Reviewed]                │
└─────────────────────────────────────────────────────────┘

[Continue list of pending events...]

[Safety Statistics - This Week]

Total Events: 47
Events Reviewed: 45 (95.7%)
Coaching Required: 12
No Action Required: 33
Pending Review: 2

Events by Type:
- Hard Braking: 18 events (38%)
- Speeding: 12 events (26%)
- Distracted Driving: 8 events (17%)
- Following Too Close: 6 events (13%)
- Hard Acceleration: 3 events (6%)

Events by Severity:
- 🔴 High: 8 events
- 🟡 Medium: 24 events
- 🟢 Low: 15 events

[Driver Safety Leaderboard]

Top 10 Safest Drivers (Fewest Events):
1. John Smith (D-089) - 0 events this week ✅
2. Jane Doe (D-124) - 0 events this week ✅
3. [Continue list...]

Drivers Requiring Attention (Multiple Events):
1. Mike Johnson (D-067) - 6 events (3 coaching required) 🔴
2. Lisa Garcia (D-234) - 4 events (2 coaching required) 🟡
3. [Continue list...]

[Safety Trend]
[Chart showing total events per week over 12 weeks]
Trend: Generally decreasing (good progress)

═══════════════════════════════════════════════════════════
[TAB: Coaching Queue]
═══════════════════════════════════════════════════════════

[Coaching Pipeline]

Status Filter: [All | Pending | Scheduled | Completed | Acknowledged]

┌──────────────┬──────────────┬──────────────┬──────────────┐
│ Pending      │ Scheduled    │ Completed    │ Acknowledged │
│     12       │     5        │     18       │     15       │
└──────────────┴──────────────┴──────────────┴──────────────┘

[Pending Coaching - Requires Action]

┌─────────────────────────────────────────────────────────┐
│ 🔴 URGENT - Overdue Coaching                             │
│ Driver: Mike Johnson (D-067)                            │
│ Issue: Multiple distracted driving events (3)            │
│ Events: Oct 28, Nov 2, Nov 6                            │
│ Days Pending: 9 days ⚠️ OVERDUE                         │
│ Priority: 🔴 HIGH                                        │
│                                                           │
│ Recommended Action:                                      │
│ Immediate in-person coaching required due to safety     │
│ pattern and severity of infractions.                     │
│                                                           │
│ [Schedule Coaching] [Use Template] [Escalate to Owner]  │
└─────────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────────┐
│ Coaching Required                                        │
│ Driver: Lisa Garcia (D-234)                             │
│ Issue: POD photo quality (Poor lighting - 5 instances)   │
│ Period: Week 45 (Nov 1-7)                               │
│ Days Pending: 2 days                                     │
│ Priority: 🟡 MEDIUM                                      │
│                                                           │
│ Suggested Template: "POD Photo Quality Improvement"     │
│                                                           │
│ [Schedule Coaching] [Send Template Message] [View Details]│
└─────────────────────────────────────────────────────────┘

[Continue list of pending coaching...]

[Scheduled Coaching Sessions]

┌─────────────────────────────────────────────────────────┐
│ Scheduled Coaching Session                               │
│ Driver: Tom Brown (D-156)                               │
│ Date/Time: November 8, 2025 at 2:00 PM                 │
│ Type: Safety - Speeding events                          │
│ Location: Station Office                                │
│ Scheduled By: Sarah Johnson (Station Manager)           │
│ Status: ⏰ Upcoming (Tomorrow)                          │
│                                                           │
│ [View Coaching Plan] [Reschedule] [Cancel] [Remind Driver]│
└─────────────────────────────────────────────────────────┘

[Completed Coaching - Awaiting Acknowledgment]

┌─────────────────────────────────────────────────────────┐
│ Completed Coaching - Needs Driver Signature              │
│ Driver: John Smith (D-089)                              │
│ Date Conducted: November 5, 2025                        │
│ Type: Safety - Hard braking event                       │
│ Conducted By: Sarah Johnson                             │
│ Status: ⏳ Awaiting driver acknowledgment               │
│ Days Since Coaching: 2 days                             │
│                                                           │
│ [Send Reminder to Driver] [View Coaching Document]       │
│ [Mark as Acknowledged] (Override if needed)              │
└─────────────────────────────────────────────────────────┘

[Coaching Analytics]

Coaching Sessions This Month: 18
Average Time to Complete: 3.2 days
Driver Response Rate: 95% (positive acknowledgment)
Repeat Coaching (Same Issue): 12% (acceptable)

Most Common Coaching Topics:
1. Safety Events (48%)
2. POD Quality (28%)
3. Customer Service (15%)
4. Attendance (9%)

Coaching Effectiveness:
Drivers showing improvement after coaching: 87% ✅
Drivers requiring escalation: 3 (8%)
```

**User Actions:**
- Upload weekly scorecards
- Review safety events and assign coaching
- Monitor POD compliance
- Schedule coaching sessions
- Send coaching templates
- Track coaching completion
- Generate performance reports
- Identify training needs

---

This completes the Station Manager role specification. Would you like me to continue with:
1. **Dispatcher Role** (focused on daily route operations)
2. **Driver Role** (mobile app features)
3. **Fleet Manager Role** (vehicle-centric view)
4. **HR Administrator Role** (people operations focus)

Let me know which role you'd like me to detail next, or if you'd like me to complete all roles in the next response!
