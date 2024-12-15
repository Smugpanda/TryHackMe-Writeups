# **Advent of Cyber 2024**

## **Introduction**
The Advent of Cyber is an annual event hosted by TryHackMe that provides daily cybersecurity challenges throughout December. Each challenge is designed to teach participants new skills in areas such as penetration testing, digital forensics, web exploitation, and more.

This folder contains my writeups for the **Advent of Cyber 2024** challenges. Each writeup includes a detailed walkthrough of the challenge, tools used, and key takeaways.

---

## **Table of Contents**
Below is a list of the challenges completed during Advent of Cyber 2024. Click on a specific day to view its writeup:

1. [Day 1: OPSEC](Day-01-OPSEC/writeup.md)  
   *Investigating malicious link files and analyzing OPSEC failures.*
2. [Day 2: Log Analysis](Day-02-Log-Analysis/writeup.md)  
   *Analyzing logs to uncover suspicious activity.*
3. [Day 3: Log Analysis](Day-03-Log-Analysis/writeup.md)  
   *Exploring further log analysis techniques.*
4. [Day 4: Atomic Red Team](Day-04-Atomic-Red-Team/writeup.md)  
   *Using Atomic Red Team techniques to simulate attacks.* 
5. [Day 5: XXE](Day-05-XXE/writeup.md)  
   *Exploiting XML External Entity vulnerabilities.*  
6. [Day 6: Sandboxes](Day-06-Sandboxes/writeup.md)  
   *Understanding and bypassing sandbox environments.* 
7. [Day 7: AWS Log Analysis](Day-07-AWS-Log-Analysis/writeup.md)  
   *Investigating AWS logs for suspicious activities.*  
8. [Day 8: Shellcodes](Day-08-Shellcodes/writeup.md)  
   *Analyzing and executing shellcode payloads.* 
9. [Day 9: GRC](Day-09-GRC/writeup.md)  
   *Exploring Governance, Risk, and Compliance in cybersecurity.* 
10. [Day 10: Phishing](Day-10-Phishing/writeup.md)  
    *Exploit phishing attacks using Macros.* 
11. [Day 11: Wifi-attacks](Day-11-Wifi-attacks/writeup.md)  
    *Exploring wireless network vulnerabilities.* 
12. [Day 12: Web Timing Attacks](Day-12-Web-Timing-Attacks/writeup.md)  
    *Understanding and exploiting web timing attacks to manipulate application behavior.*

---

## **Purpose**
The purpose of this folder is to document my progress through the Advent of Cyber 2024 challenges while showcasing my problem-solving approach and cybersecurity skills. These writeups are intended to:
1. Serve as a personal reference for future learning.
2. Help others who may be stuck on similar challenges.
3. Demonstrate practical applications of cybersecurity tools and techniques.

---

## **Tools Used**

Throughout these challenges, I utilized a variety of tools and techniques tailored to each specific task. Below is a more detailed breakdown of the tools used in different categories:

### **Forensics Tools**
- **ExifTool**: For extracting metadata from files.
- **Wireshark**: For analyzing network traffic captures.

### **Web Exploitation Tools**
- **Burp Suite**: For intercepting and modifying HTTP requests.
- **OWASP ZAP**: For scanning web applications for vulnerabilities.

### **Scripting Languages**
- **Python**: For automating tasks and data analysis.
- **Bash**: For scripting in Unix-based environments.
- **PowerShell**: For scripting in Windows environments.

### **Cloud Security Tools**
- **AWS CLI**: Used for managing AWS services such as S3 and IAM directly from the command line.
- **CloudTrail**: Utilized for tracking user activity and detecting anomalies in AWS environments.
- **CloudWatch**: Employed for monitoring AWS resources and setting up alerts for suspicious activities.
- **JQ**: Essential for parsing JSON data from CloudTrail logs to identify specific events and actions.

### **General Tools**
- **Nmap**: For network discovery and security auditing.
- **Metasploit**: For penetration testing and exploiting vulnerabilities.

---

## Future Plans
I plan to continue updating these writeups as I complete more challenges, incorporating new tools and techniques learned along the way.

---

## **How to Navigate**
To view a specific day's writeup:
1. Navigate to the corresponding folder (e.g., `Day-1-OPSEC`).
2. Open the `writeup.md` file for a detailed walkthrough.
3. Refer to any accompanying images in the `images/` subfolder for visual context.

Alternatively, you can click on the links in the [Table of Contents](#table-of-contents) above to jump directly to a specific challenge.

---

## **Key Takeaways**
Some key lessons learned from Advent of Cyber 2024 include:
1. The importance of operational security (OPSEC) in preventing identity exposure.
2. Techniques for analyzing logs to detect suspicious activity.
3. How attackers exploit vulnerabilities like XXE and sandbox bypasses.
4. Practical applications of cloud security tools in investigating AWS environments.

---

## **Acknowledgments**
Special thanks to TryHackMe for organizing this event and providing such an excellent platform for learning cybersecurity concepts.

---

### Example Folder Structure
Here’s how this folder is organized:
```plaintext
Advent-of-Cyber-2024/
├── Day-01-OPSEC/
│   ├── writeup.md
│   └── images/
├── Day-02-Log-Analysis/
│   ├── writeup.md
│   └── images/
├── Day-X/
│   ├── writeup.md
│   └── images/
└── README.md
