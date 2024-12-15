# **TryHackMe Writeup: Day 9 - GRC (Advent of Cyber 2024)**

## **Overview**
- **Room Name**: Day 9: Nine o'clock, make GRC fun, tell no one
- **Difficulty**: Medium
- **Category**: Governance, Risk, and Compliance
- **Objective**: Understand and apply principles of governance, risk management, and compliance (GRC) in a cybersecurity context.
- **Tools**: Risk Register, Risk Assessment Frameworks

---

## **Table of Contents**
1. [Introduction](#introduction)
2. [Performing a Risk Assessment](#performing-a-risk-assessment)
3. [Internal and Third-Party Risk Assessments](#internal-and-third-party-risk-assessments)
4. [Procuring a Partner](#procuring-a-partner)
5. [Conclusion](#conclusion)

---

## **Introduction**

Governance, Risk, and Compliance (GRC) are critical components of an organization's cybersecurity strategy. This challenge focuses on performing risk assessments to identify potential threats and vulnerabilities within an organization and its third-party vendors. By understanding GRC principles, participants can better manage risks and ensure compliance with security standards.

---

## **Performing a Risk Assessment**

A risk assessment involves identifying potential risks, evaluating their likelihood and impact, and determining appropriate mitigation strategies.

### **Risk Identification**
Identify factors that can cause revenue or reputation loss from cyber threats by assessing the attack surface of the organization. Examples include:
- Unpatched web servers.
- High-privileged user accounts without proper security controls.
- Third-party vendors with inadequate security measures.

### **Assigning Risk Likelihood**
Evaluate how likely it is for each risk to materialize. Assign a likelihood score (1 to 5) based on probability:
1. **Improbable**: Very unlikely to occur.
2. **Remote**: Unlikely but possible.
3. **Occasional**: Likely to happen occasionally.
4. **Probable**: Likely to happen several times.
5. **Frequent**: Likely to happen often.

### **Assigning Risk Impact**
Assess the potential impact of each risk using a scale from 1 to 5:
1. **Informational**: Minimal impact.
2. **Low**: Limited impact on operations.
3. **Medium**: Significant impact on one area.
4. **High**: Major impact on multiple areas.
5. **Critical**: Existential threat to the organization.

### **Risk Ownership/Risk Score**
Calculate the risk score by multiplying likelihood by impact. Assign ownership to responsible team members for further investigation and mitigation planning.

---

## **Internal and Third-Party Risk Assessments**

### **Internal Risk Assessments**
Conduct internal assessments to identify vulnerabilities within the organization:
- Identify outdated software or systems.
- Prioritize updates and patches to prevent attacks.

### **Third-Party Risk Assessments**
Evaluate risks from external vendors or partners:
- Ensure vendors have robust security measures.
- Verify compliance with data protection regulations.

---

## **Procuring a Partner**

Assess potential partners using a risk register:

### Vendor 1: Purple Hawk
1. Data encryption for transit and rest is lacking.
   - Impact: High (3/4), Likelihood: Very Likely (4/4), Risk Score: 12/16
2. Inadequate access controls.
   - Impact: Critical (4/4), Likelihood: Very Likely (4/4), Risk Score: 16/16

### Vendor 2: Golden Tiger
1. Uses AES-256 for data in transit but none for data at rest.
   - Impact: High (3/4), Likelihood: Possible (2/4), Risk Score: 6/16
2. Access controls allow broad access within teams.
   - Impact: Critical (4/4), Likelihood: Likely (3/4), Risk Score: 12/16

### Vendor 3: Indigo Bear
1. No encryption for data in transit; AES-256 for data at rest.
   - Impact: High (3/4), Likelihood: Likely (3/4), Risk Score: 9/16
2. Access controls need improvement.
   - Impact: Critical (4/4), Likelihood: Possible (2/4), Risk Score: 8/16

#### Final Selection:
Indigo Bear is selected based on the lowest total risk score.

---

## **Conclusion**

This challenge highlighted the importance of GRC in managing cybersecurity risks effectively.

### Key Takeaways:
1. GRC frameworks help organizations identify and mitigate risks systematically.
2. Internal assessments ensure vulnerabilities are addressed proactively.
3. Third-party assessments protect against external threats from vendors or partners.

By implementing robust GRC practices, organizations can enhance their security posture and ensure compliance with industry standards.

---

### Answer the Questions Below

What does GRC stand for?
- Governance, Risk, and Compliance

What is the flag you receive after performing the risk assessment?
- THM{R15K_M4N4G3D}

---