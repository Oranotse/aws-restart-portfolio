# Using Amazon Inspector for Vulnerability Assessment and Remediation 🔍

The detailed steps for this lab can be seen clearly in the folder titled **Lab Steps Screenshots**.

## What This Lab Is About

In this lab, I worked with **Amazon Inspector** to scan for vulnerabilities in AWS Lambda functions. The goal was to activate Amazon Inspector, review vulnerability reports, and fix the issues found. Amazon Inspector is an automated security tool that scans for vulnerable software packages and code vulnerabilities in Lambda functions, EC2 instances, and Amazon ECR images.

### Task 1: Activating Amazon Inspector

I navigated to the **Amazon Inspector** console and clicked **Activate Inspector** to turn it on for the account. After activation, a message appeared saying "Welcome to Inspector. Your first scan is underway." I refreshed the page until the **Dashboard** showed **Lambda functions** at 100% under **Environment coverage**. By default, Amazon Inspector scans Amazon EC2, Amazon ECR, and AWS Lambda.

### Task 2: Reviewing the Inspected Resources

I navigated to **Findings** and chose **All findings** to see the scan results. Three vulnerabilities were found in the Lambda functions, each showing **Severity: Medium**, the **Impacted resource**, and the **Title** explaining the issue. I selected the finding **CVE-2023-32681 - requests** to view more details. Under **Vulnerability details**, I clicked the external link which took me to the National Vulnerability Database (NVD) website with detailed information about the vulnerability. The **Remediation** section recommended upgrading the requests package because it was outdated and vulnerable.

### Task 3: Remediating the Vulnerability

I went to the **Lambda** console and selected the **get-request** function. I opened the **requirements.txt** file and changed `requests==2.20.0` to just `requests`. This tells Lambda to install the latest version of the package instead of the old vulnerable version. I clicked **Deploy** to update the function, which triggered Amazon Inspector to scan it again. I returned to **Amazon Inspector** and changed **Finding status** from **Active** to **Closed**. The finding **CVE-2023-32681 - requests** now appeared in the closed findings list, confirming that the vulnerability was fixed.

## What I Learned

This lab taught me how to use **Amazon Inspector** to automatically scan AWS resources for security vulnerabilities. I learned how to read vulnerability reports by checking the severity level, affected resources, and remediation steps. I learned how to fix vulnerabilities in Lambda functions by updating the **requirements.txt** file to use the latest package versions. Seeing the vulnerability move from **Active** to **Closed** after deploying the fix showed me that Amazon Inspector continuously monitors resources and automatically rescans them after changes are made.
