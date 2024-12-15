## **TryHackMe Writeup: Day 4 - I'm All Atomic Inside**

## **Overview**

- **Room Name**: Advent of Cyber 2024 - Day 4
- **Difficulty**: Easy
- **Category**: Blue Team, Threat Simulation
- **Objective**: Simulate and detect malicious activity using the MITRE ATT&CK framework and Atomic Red Team.

---

## **Table of Contents**

1. [Introduction](#introduction)
2. [Enumeration](#enumeration)
3. [Exploitation](#exploitation)
4. [Post-Exploitation](#post-exploitation)
5. [Flags](#flags)
6. [Conclusion](#conclusion)

---

## **Introduction**

In this challenge, the Security Operations Center (SOC) team in Wareville detected suspicious activities such as admin access logs, privilege escalations, and unusual system behavior. Initially misinterpreted as an insider threat, it was later revealed that these anomalies were caused by unauthorized attack simulations using the Atomic Red Team framework.

The goal of this task is to:
- Simulate attacks using Atomic Red Team.
- Detect artifacts created during the simulation.
- Develop detection rules to enhance security monitoring.

Key tools and concepts:
- **MITRE ATT&CK Framework**: A comprehensive matrix of adversary tactics and techniques.
- **Atomic Red Team**: A library of tests mapped to MITRE ATT&CK for simulating attacks.
- **Sysmon**: Used for detailed system monitoring and log analysis.

*Sysmon (System Monitor) is a tool from Microsoft Sysinternals that provides detailed information about process creation, network connections, and file changes. It is commonly used by blue teams to detect malicious activity on a system. In this challenge, we use Sysmon to analyze logs for Indicators of Compromise (IoCs) created during the attack simulation.*

---

## **Enumeration**

### Step 1: Understanding the Attack Technique
The SOC team suspects the use of MITRE ATT&CK Technique **T1566.001 (Spearphishing with Attachment)**. To gather details about this technique, we used the following command:

```powershell
Invoke-AtomicTest T1566.001 -ShowDetails
```

Output:
- The test simulates downloading a macro-enabled phishing attachment (`PhishingAttachment.xlsm`) from a URL.
- The file is saved in the `%TEMP%` directory.

### Step 2: Checking Prerequisites
Before running the simulation, we verified dependencies:

```powershell
Invoke-AtomicTest T1566.001 -TestNumbers 1 -CheckPrereq
```
If prerequisites are not met (e.g., missing dependencies like Microsoft Word), you can resolve this by running:
> ```powershell
> Invoke-AtomicTest T1566.001 -TestNumbers 2 -GetPrereqs
> ```
> This command will automatically fetch any required resources.
No additional resources were required for this test.

---

## **Exploitation**

### Step 1: Running the Spearphishing Simulation
To execute the attack simulation:

```powershell
Invoke-AtomicTest T1566.001 -TestNumbers 1
```

This simulated a phishing attack by downloading `PhishingAttachment.xlsm` to the `%TEMP%` directory.

### Step 2: Analyzing Logs for Indicators of Compromise (IoCs)
Using Sysmon logs in Event Viewer:
1. Navigate to `Applications and Services Logs > Microsoft > Windows > Sysmon > Operational`.
2. Look for:
   - PowerShell execution creating `PhishingAttachment.xlsm`.
   - File creation event for `PhishingAttachment.xlsm`.

Key IoCs:
- Command: `Invoke-WebRequest -Uri $url -OutFile $env:TEMP\PhishingAttachment.xlsm`
- File created: `PhishingAttachment.xlsm`.

---

## **Post-Exploitation**

### Step 1: Cleanup
After analyzing artifacts, cleanup was performed using:

```powershell
Invoke-AtomicTest T1566.001 -TestNumbers 1 -Cleanup
```

### Step 2: Creating Detection Rules
Using IoCs, a custom Sigma rule was created to detect:
1. PowerShell commands with `Invoke-WebRequest`.
2. File creation events for `PhishingAttachment.xlsm`.

Example Sigma Rule:
```yaml
title: Detect PowerShell Invoke-WebRequest and File Creation of PhishingAttachment.xlsm
id: 1
description: Detects usage of Invoke-WebRequest to download PhishingAttachment.xlsm and its creation.
logsource:
  category: process_creation
  product: windows
detection:
  selection_invoke_webrequest:
    EventID: 1
    CommandLine|contains:
      - 'Invoke-WebRequest'
      - 'http://localhost/PhishingAttachment.xlsm'
  selection_file_creation:
    EventID: 11 # Sysmon Event ID for File Creation
    TargetFilename|endswith: '\PhishingAttachment.xlsm'
condition: selection_invoke_webrequest or selection_file_creation
falsepositives:
  - Legitimate administration activity may use Invoke-WebRequest.
level: high
tags:
  - attack.t1566.001 # Spearphishing Attachment
```

---

## **Flags**

1. What was the flag found in the .txt file that is found in the same directory as the PhishingAttachment.xslm artefact?
   
   **`THM{GlitchTestingForSpearphishing}`**

2. What ATT&CK technique ID would be our point of interest?

   **`T1059`**

   *This technique represents "Command and Scripting Interpreter," which was used in the ransomware simulation.*

3. What ATT&CK subtechnique ID focuses on the Windows Command Shell?

   **`T1059.003`**
4. What is the name of the Atomic Test to be simulated?

   **`Simulate BlackByte Ransomware Print Bombing`**
5. What is the name of the file used in the test?

   **`Wareville_Ransomware.txt`**
6. What is the flag found from this Atomic Test?

   **`THM{R2xpdGNoIGlzIG5vdCB0aGUgZW5lbXk=}`**

---

## **Conclusion**

This challenge demonstrated how to simulate attacks using Atomic Red Team and detect malicious artifacts using Sysmon logs. Key takeaways include:
- Understanding MITRE ATT&CK techniques like T1566.001 (Spearphishing).
- Using tools like Sysmon for log analysis.
- Creating detection rules to identify IoCs proactively.

By leveraging these skills, blue teams can enhance their ability to detect and respond to real-world threats effectively.