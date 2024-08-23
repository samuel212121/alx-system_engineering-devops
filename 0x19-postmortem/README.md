# Bernostech Website Outage Postmortem

## Overview

This document outlines the details of the Bernostech website outage that occurred on August 11, 2024. It covers the incident timeline, root cause analysis, resolution, and corrective actions to prevent future occurrences.

---

## Issue Summary

- **Outage Duration:** 2 hours and 35 minutes (14:20 - 16:55 EAT)
- **Impact:** The Bernostech website was inaccessible to 85% of users. Visitors encountered a "502 Bad Gateway" error, preventing access to all services and resources.
- **Root Cause:** A misconfiguration in the Nginx server, which prevented proper communication between the front-end server and backend application servers.

---

## Timeline

- **14:20** - **Issue detected**: Monitoring alert triggered due to high error rates, followed by customer complaints about website downtime.
- **14:25** - **Initial investigation**: The DevOps team checked server status and logs, initially suspecting a server overload.
- **14:35** - **Assumption tested**: Server resources were increased, but the issue persisted, ruling out overload.
- **14:45** - **Misleading path**: Investigation focused on a possible database connection issue, which was later disproven.
- **15:10** - **Escalation**: Incident escalated to the senior DevOps engineer.
- **15:30** - **Root cause identified**: Configuration error in the Nginx server, preventing routing to the backend servers.
- **15:45** - **Resolution initiated**: Nginx configuration was corrected, and the server was restarted.
- **16:10** - **Monitoring confirmed**: The site became accessible, with continued monitoring to ensure stability.
- **16:55** - **Full resolution**: Website stability confirmed, normal operations resumed.

---

## Root Cause and Resolution

### Root Cause

The outage was caused by a missing routing directive in the Nginx configuration file after a recent update. This misconfiguration prevented the Nginx server from connecting to the backend application servers, resulting in a "502 Bad Gateway" error for users.

### Resolution

The configuration file was corrected by re-adding the missing directive, and the Nginx server was restarted. This restored normal operation, and the website became fully accessible.

---

## Corrective and Preventative Measures

### Improvements

1. **Configuration Review Process:** Implement a mandatory review process for all server configuration changes, with automated validation checks.
2. **Enhanced Monitoring:** Add alerts for Nginx configuration errors and backend connectivity issues.
3. **Documentation:** Update internal documentation with detailed steps for verifying Nginx configurations post-update.

### Tasks

- [ ] Implement automated checks for critical configuration files before server restarts.
- [ ] Add a monitoring alert for Nginx routing failures to the server management system.
- [ ] Conduct a training session for the DevOps team on Nginx best practices and configuration management.
- [ ] Update the standard operating procedure (SOP) to include a checklist for configuration changes.

---
