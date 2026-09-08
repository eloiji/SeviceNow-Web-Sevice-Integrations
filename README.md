# ServiceNow Web Service Integrations

A comprehensive ServiceNow application package for training exercises and practical implementations of web service integration patterns.

## 📚 Overview

This repository contains a complete ServiceNow application package designed for learning and implementing web service integrations. The package includes:

- **Training Course Management System** - Database tables and fields for managing training courses
- **Training Attendee Tracking** - Employee enrollment and course attendance management
- **Web Service Configuration** - OAuth setup and REST API infrastructure
- **Integration Patterns** - Best practices for building reliable web service integrations

## 🚀 Quick Start - How to Import into ServiceNow

### Prerequisites

- Access to a ServiceNow instance (Madrid release or later recommended)
- Administrator or Application Administrator role
- Git access to this repository

### Method 1: Using Studio (Recommended for Beginners)

1. **Log into your ServiceNow instance**
   - Navigate to your ServiceNow instance URL

2. **Open Studio**
   - Search for "Studio" in the search bar
   - Click on "Studio" under the Application Development section

3. **Import from Git**
   - In Studio, click **Import Application** → **From Git**
   - Paste the repository URL: `https://github.com/eloiji/SeviceNow-Web-Sevice-Integrations.git`
   - Select the branch: `sn_instances/dev342328`
   - Click **Import**

4. **Review and Activate**
   - Wait for the import to complete
   - The application will be installed in your instance
   - Navigate to **System Applications** → **Applications** to verify

### Method 2: Using Update Sets (Traditional Approach)

1. **Export Update Set from Source**
   - In your source ServiceNow instance (dev342328)
   - Navigate to **System Update Sets** → **Update Sets**
   - Select the "Web Service Integrations" update set
   - Click **Export** to download the XML file

2. **Import Update Set to Target Instance**
   - Log into your target ServiceNow instance
   - Navigate to **System Update Sets** → **Update Sets to Commit**
   - Click **Import Update Set from XML**
   - Upload the downloaded XML file
   - Click **Upload**

3. **Preview and Commit**
   - Click **Preview Update Set** to review changes
   - Verify all components load correctly
   - Click **Commit Update Set** to apply changes
   - The application will now be active in your instance

### Method 3: Manual File Import (Advanced)

1. **Clone the Repository**
   ```bash
   git clone https://github.com/eloiji/SeviceNow-Web-Sevice-Integrations.git
   cd SeviceNow-Web-Sevice-Integrations
   ```

2. **Create Update Set Manually**
   - In your ServiceNow instance, navigate to **System Update Sets** → **Update Sets**
   - Click **New** to create a new update set
   - Name it "Web Service Integrations Import"

3. **Use MID Server or SOAP (if available)**
   - For enterprise deployments with MID servers
   - Use the CI/CD integration pipelines
   - Contact your ServiceNow administrator

## 📁 What's Included

### Database Tables
- **Training Course** (`x_1931947_web_se_0_training_course`)
  - Stores course information, scheduling, and capacity
  - Fields: Name, State, Course Offering Level, Capacity, Minimum Threshold, Assigned To, Start/End Dates, Attendee Count

- **Training Attendee** (`x_1931947_web_se_0_training_attendee`)
  - Links employees to training courses
  - Fields: Course (Reference), Employee (Reference), Number

### Web Service Components
- OAuth Entity Configuration for secure authentication
- Scripted REST API operations for integration patterns
- Choice lists for standardized values
- Database indices for performance optimization

### Application Metadata
- Complete sys_app configuration
- Database object definitions with access controls
- Field dictionaries with validation rules
- Package checksum for integrity verification

## ✅ Verification Checklist

After importing, verify these components are in place:

- [ ] Application appears in **System Applications** → **Applications**
- [ ] Training Course table is accessible in the database
- [ ] Training Attendee table is accessible in the database
- [ ] OAuth entity "WebKit HTML to PDF" appears in **System OAuth** → **OAuth Entities**
- [ ] Web Service Integrations module appears in the navigation menu
- [ ] No import errors in the activity log

## 🔧 Troubleshooting

### Import Fails with Checksum Error
This repository contains a checksum file to ensure data integrity. If checksum validation fails:

1. **Verify file integrity**
   - Ensure no files were modified during download
   - Re-download or re-clone the repository

2. **Remove problem commits**
   - Clone your repository to a personal computer with git installed
   - Run `git log` to view commit history
   - Run `git revert SHA1` for commits edited outside ServiceNow
   - Push changes back to the repository

3. **Reset to known good state**
   - Locate a known good commit: `git log`
   - Run `git reset --hard SHA1` to revert to that commit
   - Run `git reset HEAD~1`
   - Stage and commit: `git add -A && git commit -m "Reset to stable version"`
   - Run `git push`

### Tables or Fields Not Appearing
- Check instance logs: **System Logs** → **Application Logs**
- Verify user role has access to view these tables
- Confirm no conflicting table names exist
- Try clearing browser cache and logging out/in

### OAuth Configuration Issues
- Navigate to **System OAuth** → **OAuth Entities**
- Verify the entity is marked as Active
- Check token lifespan settings (default: 1800 seconds)
- Ensure authentication requirements are set correctly

## 📖 Usage Guide

### Creating a Training Course
1. Navigate to **Web Service Integrations** → **Training Courses**
2. Click **New** to create a new course
3. Fill in required fields:
   - **Name**: Course title
   - **Course Offering**: Select level (Beginner, Intermediate, Advanced, Bootcamp, Certification)
   - **State**: Set initial state (Ready, In Progress, Ended, Archived)
   - **Capacity**: Maximum number of attendees
   - **Assigned To**: Instructor name
   - **Start/End Dates**: Course duration

### Enrolling an Attendee
1. Navigate to **Web Service Integrations** → **Training Attendees**
2. Click **New** to enroll an employee
3. Select the **Course** from the dropdown
4. Select the **Employee** to enroll
5. The system automatically generates a **Number** identifier
6. Click **Save**

## 🔐 Security Considerations

- Application is scope-restricted to `x_1931947_web_se_0`
- OAuth tokens are encrypted in transit and at rest
- Access controls defined at table and field level
- Regular security updates recommended for long-term deployments

## 📝 Application Information

- **Scope**: x_1931947_web_se_0
- **Version**: 1.0.0
- **License**: See LICENSE file
- **Created**: 2026-09-08
- **Last Updated**: 2026-09-08

## 🤝 Support & Issues

For issues or questions:
1. Check the **Troubleshooting** section above
2. Review ServiceNow documentation on update sets and applications
3. Open an issue on GitHub with detailed information about your error

## 📚 Additional Resources

- [ServiceNow Studio Documentation](https://docs.servicenow.com/bundle/latest/page/build/applications/concept_studio.html)
- [Update Sets Guide](https://docs.servicenow.com/bundle/latest/page/build/update_sets/concept_update_sets.html)
- [REST API Development](https://docs.servicenow.com/bundle/latest/page/build/applications/concept_rest_api_scripted.html)
- [OAuth Integration](https://docs.servicenow.com/bundle/latest/page/integrate/authentication/concept_oauth.html)

## 📄 License

Please refer to the LICENSE file in this repository for licensing information.

---

**Last Updated**: 2026-09-08  
**Repository Branch**: sn_instances/dev342328  
**Target Instances**: ServiceNow Madrid and later
