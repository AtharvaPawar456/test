# Tool : arcon-CVEscan

## 1. Information
    Document Title: Report for arcon-cvescan
    Version: 1.0
    Developer: Atharva Pawar
    Role: IoT Developer
    Department: Software Developer
    Mentor: Kalpesh Pusalkar
    Date: 11/12/2024

## 2. Application Overview
### 2.1 Application Name: 
    arcon-cvescan

### 2.2 Purpose:
The arcon-cvescan CLI application is designed to enhance system security by identifying software vulnerabilities on Windows systems. It scans the installed software, retrieves their details, and compares them against a CVE (Common Vulnerabilities and Exposures) online database to identify vulnerabilities.

## 3. Functionality
### 3.1 Features:

**Software Scanning:**
The application scans all installed software on the system.
It collects the following details for each software:
- Vendor Name
- Software Name
- Version

**CVE Database Integration:**
The application connects to an online CVE database while updating the local database.
It compares the software details against reported CVEs from local db(offline db) based on the following parameters:
- Vendor Name
- Software Name
- Version

## Findings:
Shortlists vulnerable software based on matches found in the CVE database.
Tags these software as vulnerable due to reported CVEs.

**Report Generation:**

Outputs the results in two formats:
- `report.html`: A user-friendly report with a structured UI representing findings.
- `findings.json`: A detailed JSON file containing all vulnerable software information for system-level integration.

## 4. Workflow
### 4.1 Input:
The application requires no direct user input for scanning.
It fetches the CVE database details through an internet connection.

### 4.2 Process:
**System Scan:**

Scans the Windows system for installed software.

**Data Extraction:**

Extracts vendor name, software name, and version for each installed software.

**Comparison Algorithm:**

- Compares extracted details with the offline CVE database.

- Identifies matches based on vendor name, software name, and version.

**Findings:**

Flags software as vulnerable if a CVE is reported.

**Report Generation:**

Generates an HTML and a JSON report with the findings.

### 4.3 Output:
**HTML Report:**
- html Report: `report.html`Provides a visually organized UI for findings.
- JSON File:
    `findings.json` Contains all details of vulnerable software in a structured format.

## 5. Integration Details
### 5.1 Integration Points:
The application can be integrated with security systems to automatically detect and flag vulnerabilities.
The `findings.json` file can be used as an input for further processing or monitoring tools.

### 5.2 Requirements for Integration:

**System Requirements:**

- Operating System: `Windows`
- Internet Access: Required for CVE offline database updating
- `Python 3.8+` (for CLI execution)

**Execution Instructions:**
- Run the CLI tool in the Windows Command Prompt or PowerShell.
- Ensure the system has internet connectivity for offline database updating.


## 6. Error Handling

**No Internet Connection while updating the db:**

- Displays an error message: "Unable to connect to CVE database. Please check your internet connection."

**Invalid Data in CVE Database:**

- Logs the error in the console and skips the specific entry.

**File Creation Issues:**

- Displays an error message: "Unable to generate report files. Check file permissions."

## 8. Conclusion
The arcon-cvescan application provides a robust mechanism to detect and report vulnerabilities in installed software. Its dual output format (HTML and JSON) ensures user-friendly representation and seamless integration with other systems.
