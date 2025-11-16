# Internal Project Management Tool

A comprehensive project management system built with FilamentPHP, designed to streamline project execution, team coordination, client communication, QA workflows, financial management, and freelancer tracking.

## 🎯 Objective

Centralize and streamline all activities related to project execution with a **simple, minimal, and user-friendly** interface optimized for small teams with strict role-based access control.

**Design Philosophy: User-Friendly, Not Theory-Friendly**
- Built for real-world project management, not academic concepts
- Clean, intuitive interfaces that anyone can use
- Quick actions accessible in 1-2 clicks
- No unnecessary complexity or jargon
- Focus on getting work done efficiently

## 🛠️ Technology Stack

- **Framework**: Laravel 11
- **Admin Panel**: FilamentPHP v3
- **Permissions**: Filament Shield (role & permission management)
- **Media Management**: Spatie Media Library
- **Settings**: Spatie Laravel Settings
- **Activity Log**: Spatie Laravel Activity Log
- **Database**: MySQL/PostgreSQL
- **Queue**: Redis
- **Storage**: Local/S3
- **Version Control**: Git (GitHub/GitLab integration)

## 👥 User Roles & Permissions

### 1. Admin
- Full access across all modules
- Create projects, users, clients, budgets
- Access all standups, documents, communication
- Configure global system settings

### 2. Project Manager (PM)
- Manage assigned projects
- Create/assign tasks
- View all standups (Dev/QA/Freelancers)
- Access client communication module
- Approve PRs
- Manage risks, delays, documentation

### 3. Developer
- Access assigned tasks
- Submit standups
- Add commits/PR links
- Update daily progress
- Limited project view

### 4. QA
- Access QA board
- Create/track bugs
- Upload test cases
- Validate and approve tasks for "Done"
- Access only QA-related documents

### 5. Freelancer
- Access only assigned tasks
- Restricted document visibility
- Must submit daily standups
- Cannot access client communication
- Cannot view team standups
- Cannot approve PRs

### 6. Finance
- Manage budgets, invoices, payouts
- View financial reports
- No access to technical tasks or communication

## 📋 Core Modules

### 1. System Settings Module (Spatie Settings)
**Admin configurable settings:**
- ✅ Task Status Stages (To Do → In Progress → Review → QA → Done)
- ✅ Priority Levels (Low, Medium, High, Urgent)
- ✅ Default Project Workflow
- ✅ Standup Timings (Morning/Evening windows)
- ✅ Risk Severity Levels (Low/Med/High/Critical)
- ✅ Payment Models (Hourly/Monthly/Project-based)
- ✅ Document Categories
- ✅ Notification Preferences
- ✅ Freelancer Rules & Auto-alerts
- ✅ PR Workflow Settings

### 2. Dashboard Module
**Role-based dashboards with real-time data:**

**PM Dashboard:**
- Today's tasks
- Delayed tasks
- Standup summary
- PR pending approvals
- Risks
- Project-level alerts

**Developer/QA Dashboard:**
- Assigned tasks
- Deadlines
- PR status
- Pending reviews/QA tasks
- Standup reminders

**Freelancer Dashboard:**
- Assigned tasks only
- Deadlines
- Standup history
- Performance alerts

**Admin Dashboard:**
- Overall project status
- Team performance summary
- Financial overview
- Risks snapshot

**Finance Dashboard:**
- Payments due
- Budget tracking
- Freelancer payouts
- Invoice status

### 3. Standup Management Module
**Two daily standups:**

**Morning Standup:**
- What is planned today?
- Any blockers?

**Evening Standup:**
- What was completed?
- What is pending?
- Blockers
- Time spent

**Features:**
- ✅ Only PM/Admin can view all standups
- ✅ Team members see only their own
- ✅ Auto-alerts for missed submissions
- ✅ Standup history per user
- ✅ Compliance tracking

### 4. Project Management Module
**Complete project lifecycle management:**

**Project Creation:**
- Title, description
- Client linking
- Timeline & deadlines
- Budget allocation
- Assigned PM
- Versions/Sprints

**Requirements Section:**
- BRD upload (Business Requirement Document)
- FRD upload (Functional Requirement Document)
- Requirement approval workflow

**Project Overview Dashboard:**
- Status tracking
- Budget monitoring
- Task overview
- Risk management
- Document repository

**Change Request Management:**
- CR logging and tracking
- Impact assessment
- Timeline revision
- Budget updates
- Client approval workflow

### 5. Task Management Module
**Comprehensive task tracking:**

**Task Card Fields:**
- Title & Description
- Deadline & Priority
- Status (configurable workflow)
- Assignee
- Subtasks
- Attachments (Spatie Media)
- PR links
- Blockers
- Comments
- Daily progress tracker

**Additional Features:**
- ✅ Auto-delay alerts
- ✅ PM views all tasks
- ✅ Freelancers see only assigned tasks
- ✅ Time estimate vs actual time spent
- ✅ Daily update timeline
- ✅ Automatic delay prediction

### 6. Daily Update & Progress Tracking
- Daily updates by assignee
- Consolidated timeline view for PM
- Automatic delay prediction using trends
- Progress percentage tracking
- Blocker identification

### 7. PR & Code Integration Module
**GitHub/GitLab Integration:**
- PR linking to tasks
- Commit logs display
- Branch tracking

**PR Approval Workflow:**
- Dev → PM approval required
- QA validation before "Done"
- PR pending reminders
- CI/CD status tracking

**Branching Model:**
- `main` → initial setup code
- `development` → active development
- `production` → production-ready code
- `feature/*` → feature branches
- `bugfix/*` → bug fixes
- `hotfix/*` → urgent fixes

### 8. QA & Bug Management Module
**Dedicated QA workflow:**
- QA-specific task board
- Test case upload (Spatie Media)
- Bug creation with:
  - Severity
  - Priority
  - Reproduction steps
  - Screenshots/attachments
- Bug lifecycle tracking
- QA approval required before "Done"
- Test Case Document (TCD)
- QA Sign-off Report

### 9. Risk Identification & Mitigation Module
**Risk management per project:**
- Risk log with severity levels
- Owner assignment
- Mitigation plan
- Status tracking
- High-risk notifications
- Escalation workflow

**Risk Types:**
- Delayed client input
- Integration dependency
- Team bandwidth issues
- Unclear requirements

### 10. Freelancer Management Module
**Complete freelancer lifecycle:**

**Freelancer Database:**
- Personal details
- Skill mapping
- Pricing models (hour/month/project)
- Ratings & performance scores
- Agreement & NDA uploads (Spatie Media)
- Availability tracking

**Freelancer Rules:**
- ✅ Mandatory daily standups
- ✅ Mandatory daily commits
- ✅ 24-hour no update flag
- ✅ 48-hour unresponsive → PM alert
- ✅ Auto-reassignment trigger

**Performance Tracking:**
- Communication rating
- Response time rating
- Code quality rating
- Project history
- Payment history

**Restrictions:**
- Limited task visibility
- No client communication
- No team standup access
- No PR approval rights

### 11. Communication Management Module
**Project-level communication:**
- Meeting notes
- Requirement clarifications
- Client decisions
- Email approvals (PDF/screenshots upload)
- Minutes of Meeting (MoM) templates
- Discussion threads

**Access Control:**
- ✅ Only PM/Admin access
- ✅ Team members & freelancers cannot view
- ✅ Client communication history
- ✅ Approval tracking

### 12. Document Management Module (Spatie Media Library)
**Structured document repository:**

**Folder Structure:**
- 📁 BRD (Business Requirements)
- 📁 FRD (Functional Requirements)
- 📁 Client Communication
- 📁 Technical Documentation
  - API Docs
  - Database Schema
- 📁 Credentials (Admin/PM only)
- 📁 Contracts/SOW
- 📁 QA Documents
  - Test Cases
  - Bug Reports
  - QA Sign-off
- 📁 Delivery & Handover
- 📁 Change Requests

**Features:**
- ✅ Document version control
- ✅ Access control per folder
- ✅ Upload history
- ✅ Download logs
- ✅ File preview
- ✅ Search & filter

### 13. Client Management Module (Mini-CRM)
**Client relationship management:**

**Client Profile:**
- Company details
- Contact list
- Project history
- Payment history
- Budget overview
- Reviews/ratings
- Approved agreements & contracts
- Communication log

**Features:**
- Client sign-off tracking
- Project portfolio per client
- Revenue analysis per client
- Future opportunity tracking

### 14. Financial Management Module
**Complete financial tracking:**

**Budget Management:**
- Client budget tracking
- Milestone payment tracking
- Paid/Pending status
- Payment reminders

**Freelancer Payouts:**
- Payout logs
- Payment schedule
- Pending payments
- Payment history

**Financial Reports:**
- Profit/Loss per project
- Revenue breakdown
- Expense tracking
- Budget vs Actual analysis

**Access Control:**
- ✅ Finance-only sensitive data access
- ✅ PM can view project budgets
- ✅ Admin full access

### 15. Reporting & Analytics Module
**Comprehensive reporting:**

**PM Reports:**
- Delayed tasks report
- Standup compliance
- Risk reports
- Freelancer reliability scores
- Team productivity metrics

**CEO Reports:**
- All project health overview
- Financial summaries
- Client status overview
- Delays & bottlenecks
- Team performance

**Finance Reports:**
- Payment logs
- Revenue breakdown
- Expense reports
- Profit/Loss statements
- Invoice status

**Export Options:**
- PDF export
- Excel export
- CSV export
- Email reports

### 16. Post-Project Closure Module
**Project completion workflow:**

**Final Delivery Checklist:**
- ✅ Final deliverables sent
- ✅ Client sign-off upload
- ✅ Revoke all access (freelancer, dev, QA)
- ✅ Archive documents
- ✅ Client feedback form
- ✅ Retrospective notes (Lessons Learned)

**Support/Warranty Tracking:**
- Support period (7/14/30 days)
- Bug-fix only support
- Enhancement request tracking
- Support ticket logging

**Post-Project Review:**
- Client satisfaction survey
- Internal retrospective
- Performance review
- Lessons learned database

### 17. Notifications & Alerts Module
**Real-time notification system:**

**Alert Types:**
- ✅ Task deadline reminders
- ✅ Delayed tasks alerts
- ✅ Missed standups
- ✅ Unresponsive freelancers (24h/48h)
- ✅ Payment due reminders
- ✅ PR pending approval
- ✅ Risk alerts (high severity)
- ✅ Document update notifications
- ✅ Client approval pending
- ✅ QA sign-off required

**Notification Channels:**
- In-app notifications
- Email notifications
- Dashboard alerts
- Configurable per role

### 18. Integrations
**Third-party integrations:**
- ✅ GitHub/GitLab (PR tracking, commits)
- ✅ Email SMTP (notifications, client communication)
- ✅ Google Drive/Zoho (optional storage backup)
- ✅ Google Calendar (optional reminders)
- ✅ Slack/Discord (optional team notifications)

## 🗂️ Database Schema Overview

### Core Tables
- `users` (with roles via Spatie Permission)
- `projects`
- `tasks`
- `subtasks`
- `clients`
- `freelancers`
- `standups`
- `daily_updates`
- `risks`
- `bugs`
- `pull_requests`
- `documents` (Spatie Media)
- `communications`
- `meetings`
- `budgets`
- `payments`
- `invoices`
- `change_requests`
- `test_cases`
- `project_closures`
- `retrospectives`
- `notifications`

### Pivot Tables
- `project_user` (team assignments)
- `task_user` (task assignments)
- `model_has_roles` (Filament Shield)
- `model_has_permissions` (Filament Shield)
- `role_has_permissions` (Filament Shield)

## 📅 Implementation Phases

### Phase 1: Foundation & Core Setup (Week 1-2)
**Goal: Setup base infrastructure and authentication**

- ✅ Laravel 11 installation
- ✅ FilamentPHP v3 installation
- ✅ Filament Shield setup (roles & permissions)
- ✅ Spatie packages setup (Media Library, Settings, Activity Log)
- ✅ Database design & migrations
- ✅ User authentication & roles
- ✅ Basic dashboard layout
- ✅ System settings module

**Deliverables:**
- Working admin panel with login
- Role-based access control
- Basic settings configuration

### Phase 2: Project & Task Management (Week 2-3)
**Goal: Core project and task functionality**

- ✅ Project CRUD with Filament
- ✅ Client management module
- ✅ Task management with status workflow
- ✅ Subtask support
- ✅ Document upload (BRD/FRD)
- ✅ Basic project dashboard
- ✅ Task assignment workflow

**Deliverables:**
- Create and manage projects
- Task creation and assignment
- Document repository structure
- Client linking

### Phase 3: Standup & Daily Progress (Week 3-4)
**Goal: Team collaboration and progress tracking**

- ✅ Standup management (morning/evening)
- ✅ Daily update tracking
- ✅ Progress timeline view
- ✅ Auto-alerts for missed standups
- ✅ Standup compliance reports
- ✅ Role-based standup visibility

**Deliverables:**
- Daily standup submission
- Progress tracking
- Compliance monitoring
- Team coordination

### Phase 4: QA & Development Workflow (Week 4-5)
**Goal: QA processes and code integration**

- ✅ QA board & bug tracking
- ✅ Test case upload
- ✅ Bug lifecycle management
- ✅ PR integration (GitHub/GitLab)
- ✅ Commit tracking
- ✅ QA approval workflow
- ✅ Code review system

**Deliverables:**
- QA task board
- Bug tracking system
- PR linking and approval
- Test case management

### Phase 5: Freelancer & Risk Management (Week 5-6)
**Goal: Freelancer tracking and risk mitigation**

- ✅ Freelancer database
- ✅ Freelancer onboarding workflow
- ✅ Agreement/NDA upload
- ✅ Performance tracking
- ✅ Auto-alerts (24h/48h)
- ✅ Risk identification module
- ✅ Risk mitigation tracking
- ✅ Escalation workflow

**Deliverables:**
- Freelancer management system
- Performance rating system
- Risk log and tracking
- Alert automation

### Phase 6: Financial Management (Week 6-7)
**Goal: Budget tracking and payment management**

- ✅ Budget allocation per project
- ✅ Milestone payment tracking
- ✅ Freelancer payout module
- ✅ Invoice generation
- ✅ Payment reminders
- ✅ Profit/Loss calculation
- ✅ Financial reports

**Deliverables:**
- Budget management
- Payment tracking
- Invoice system
- Financial reporting

### Phase 7: Communication & Documentation (Week 7-8)
**Goal: Centralized communication and document management**

- ✅ Communication module (PM/Admin only)
- ✅ Meeting notes (MoM)
- ✅ Client approval tracking
- ✅ Email integration
- ✅ Document version control
- ✅ Access control per document
- ✅ Document search & filter

**Deliverables:**
- Communication hub
- Document repository
- Version control
- Access management

### Phase 8: Analytics & Reporting (Week 8-9)
**Goal: Comprehensive reporting and analytics**

- ✅ PM reports (delays, risks, compliance)
- ✅ CEO dashboard (project health)
- ✅ Finance reports (P&L, revenue)
- ✅ Freelancer performance reports
- ✅ Export functionality (PDF/Excel)
- ✅ Custom report builder
- ✅ Scheduled reports

**Deliverables:**
- Role-based reports
- Export functionality
- Dashboard analytics
- Performance metrics

### Phase 9: Post-Project & Closure (Week 9-10)
**Goal: Project completion and retrospective**

- ✅ Project closure checklist
- ✅ Client sign-off workflow
- ✅ Access revocation
- ✅ Document archiving
- ✅ Client feedback collection
- ✅ Retrospective module
- ✅ Lessons learned database
- ✅ Support/Warranty tracking

**Deliverables:**
- Closure workflow
- Feedback system
- Retrospective tool
- Support tracking

### Phase 10: Notifications & Integrations (Week 10-11)
**Goal: Automation and third-party integrations**

- ✅ Notification system (in-app/email)
- ✅ Auto-alerts configuration
- ✅ GitHub/GitLab webhook integration
- ✅ Email SMTP setup
- ✅ Calendar integration (optional)
- ✅ Slack/Discord integration (optional)
- ✅ Backup automation

**Deliverables:**
- Complete notification system
- Integration with version control
- Email automation
- Optional integrations

### Phase 11: Testing & Polish (Week 11-12)
**Goal: Quality assurance and UI refinement**

- ✅ End-to-end testing
- ✅ Role-based access testing
- ✅ Performance optimization
- ✅ UI/UX refinement
- ✅ Mobile responsiveness
- ✅ Security audit
- ✅ Documentation completion

**Deliverables:**
- Production-ready application
- Test coverage
- User documentation
- Admin guide

## 🚀 Installation Guide

### Prerequisites
- PHP 8.2+
- Composer
- Node.js & NPM
- MySQL 8.0+ or PostgreSQL 14+
- Redis (for queues)

### Installation Steps

```bash
# Clone repository
git clone <repository-url>
cd Cuckoo

# Install dependencies
composer install
npm install

# Environment setup
cp .env.example .env
php artisan key:generate

# Database setup
php artisan migrate
php artisan db:seed

# Setup Filament Shield
php artisan shield:install
php artisan shield:generate --all

# Create super admin user
php artisan shield:super-admin

# Build assets
npm run build

# Start development server
php artisan serve
```

### Default Roles Setup
Filament Shield will automatically create default roles. You can customize them via the admin panel:
- **Super Admin** (full access)
- **Admin** (configured permissions)
- **Project Manager**
- **Developer**
- **QA**
- **Freelancer**
- **Finance**

## 📦 Key Packages

```json
{
  "filament/filament": "^3.0",
  "bezhansalleh/filament-shield": "^3.0",
  "spatie/laravel-medialibrary": "^11.0",
  "spatie/laravel-settings": "^3.0",
  "spatie/laravel-backup": "^9.0",
  "spatie/laravel-activitylog": "^4.0"
}
```

**Why Filament Shield?**
- Seamlessly integrates with FilamentPHP
- Auto-generates permissions for all resources
- Built-in role management UI
- Super admin support out of the box
- User-friendly permission assignment interface

## 🔐 Security Features

- ✅ Role-based access control via Filament Shield
- ✅ Resource-level permissions (auto-generated)
- ✅ Row-level security (users see only their data)
- ✅ Document access control
- ✅ Audit logging (Spatie Activity Log)
- ✅ Secure file uploads with validation
- ✅ CSRF protection
- ✅ XSS prevention
- ✅ SQL injection prevention
- ✅ Encrypted sensitive data

## 📊 Key Features Summary

| Feature | Module | Access |
|---------|--------|--------|
| Project Management | Projects, Tasks, Milestones | PM, Admin |
| Daily Standups | Standup Module | All (PM sees all) |
| QA & Testing | QA Board, Bugs, Test Cases | QA, PM, Admin |
| Code Integration | PR Tracking, Commits | Dev, PM, Admin |
| Risk Management | Risk Log, Mitigation | PM, Admin |
| Freelancer Tracking | Freelancer DB, Performance | PM, Admin, Finance |
| Client Communication | Communication Hub | PM, Admin |
| Document Repository | Spatie Media Library | Role-based |
| Financial Tracking | Budgets, Payments, P&L | Finance, Admin |
| Reporting & Analytics | Custom Reports, Dashboards | Role-based |
| Post-Project Closure | Closure Checklist, Retrospective | PM, Admin |
| Notifications | Auto-alerts, Reminders | All (configurable) |

## 🎨 UI/UX Principles

- **Minimal & Clean**: No clutter, focus on essential information
- **Role-based Views**: Each user sees only what they need
- **Quick Actions**: Common tasks accessible in 1-2 clicks
- **Smart Defaults**: Pre-filled forms based on context
- **Mobile Responsive**: Works on desktop, tablet, and mobile
- **Dark Mode Support**: Built-in Filament dark mode
- **Fast Loading**: Optimized queries and caching

## 📝 SOP Integration

The system enforces the Standard Operating Procedure through:

1. **Mandatory Documentation**: BRD/FRD required before development
2. **Approval Workflows**: Client sign-off required at each stage
3. **Change Request Process**: Automatic CR creation for scope changes
4. **Daily Standup Enforcement**: Auto-alerts for missed updates
5. **QA Gate**: Tasks can't be "Done" without QA approval
6. **Freelancer Compliance**: 24h/48h unresponsive alerts
7. **Financial Controls**: Payment only after PM sign-off
8. **Post-Project Checklist**: Mandatory closure steps

## 🔄 Workflow Automation

- **Auto-assign**: Tasks auto-assigned based on rules
- **Auto-alerts**: Deadline, delay, and risk alerts
- **Auto-escalation**: Unresponsive freelancers escalated to PM
- **Auto-archive**: Closed projects auto-archived after 30 days
- **Auto-backup**: Daily automated backups
- **Auto-reports**: Weekly reports sent to stakeholders

## 🧪 Testing Strategy

- **Unit Tests**: Laravel Pest/PHPUnit
- **Feature Tests**: API and functionality tests
- **Browser Tests**: Laravel Dusk for UI testing
- **Role Tests**: Verify access control for each role
- **Integration Tests**: GitHub/GitLab integration tests

## 📚 Documentation

- **User Manual**: Role-specific guides
- **Admin Guide**: System configuration
- **API Documentation**: For integrations
- **Developer Guide**: For customization
- **SOP Reference**: Standard operating procedures

## 🤝 Contributing

This is an internal tool. For feature requests or bug reports, contact the development team.

## 📄 License

Proprietary - Internal Use Only

## 📞 Support

For support and questions:
- Email: support@yourcompany.com
- Slack: #project-management-tool

---

## 🎯 Next Steps

1. ✅ Review this README
2. ✅ Confirm technology stack
3. ✅ Start Phase 1 implementation
4. ✅ Setup development environment
5. ✅ Begin database design

**Estimated Timeline**: 10-12 weeks for full implementation
**Team Size**: 2-3 developers recommended

---

Built with ❤️ using FilamentPHP
