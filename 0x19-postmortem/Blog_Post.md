Issue Overview:
After rolling out a new feature on our Ruby on Rails site, we received a flood of user complaints within 5 minutes, totaling 127 emails reporting sign-in and sign-up issues. Concerned about retaining users, we investigated and found that the site failed to start due to outdated project requirements. The site experienced dysfunction from 9:55 AM to 11:20 AM GMT+1.

Timeline:
- **05-02-2022 9:55 AM GMT+1:** Initial user complaint about sign-in issues.
- **05-02-2022 10:20 AM GMT+1:** Backend developer Winus encountered the same issues.
- **05-02-2022 10:35 AM GMT+1:** Investigation into controllers and views for inconsistencies.
- **05-02-2022 10:40 AM GMT+1:** Suspected bcrypt gem issues due to an error on the site.
- **05-02-2022 10:42 AM GMT+1:** Checked views for form field bindings (turned out false).
- **05-02-2022 10:45 AM GMT+1:** Misled by assuming controllers were creating a different hash.
- **05-02-2022 10:50 AM GMT+1:** Suspected improper password hashing.
- **05-02-2022 11:00 AM GMT+1:** Incident escalated to the backend development team.
- **05-02-2022 11:20 AM GMT+1:** Incident resolved by updating the bcrypt gem version in project requirements.

Root Cause and Resolution:
The issue stemmed from using an outdated bcrypt gem version, causing errors with a valid hash. Winus manually updated the Gemfile.lock to a newer bcrypt version and reinstalled the required gems, resolving the problem.

Corrective and Preventative Measures:
1. **Continuous Integration Pipeline:** Implement a CI pipeline to run builds on each pull request branch, ensuring builds pass before merging with the deployment branch.
2. **Monitoring System:** Set up a monitoring system for both the database and application servers to promptly detect and address any issues.
3. **Test-driven Development:** Develop tests for new features, requiring successful test completion before merging with the deployment branch. This ensures that issues are caught early in the development process.
