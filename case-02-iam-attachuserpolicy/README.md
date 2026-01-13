# Case 02 – IAM Privilege Modification via AttachUserPolicy (CloudTrail)

## 📌 Summary
A CloudTrail investigation was conducted to analyze an IAM privilege change event where a managed policy was attached to an IAM user. This case focuses on identifying **write (management) events** in AWS CloudTrail and understanding how permission escalation activities are logged and verified.

---

## 🔍 Detection Source
- **AWS CloudTrail**
- Event history (Management events)

---

## ⏱ Timeline (UTC)
- **2026-01-13 00:03:31** – `AttachUserPolicy` event recorded

---

## 🧾 Event Details
| Field | Value |
|-----|------|
| Event Name | AttachUserPolicy |
| Event Source | iam.amazonaws.com |
| AWS Region | us-east-1 |
| Event Type | AwsApiCall |
| Event Category | Management |
| Read-only | false |
| Management Event | true |

---

## 👤 Actor Analysis
- **Actor Type:** Root
- **Access Method:** AWS Management Console
- **Session Type:** Console session
- **MFA:** Not authenticated at event time

> ⚠️ Root-level privilege changes represent a **high-risk action** and must always be auditable.

---

## 🧠 Why This Is a WRITE Event
Although the AWS CloudTrail UI does not always clearly display the `readOnly` column, the event name itself confirms the operation type:

### AWS API naming convention:
- `Get*`, `List*`, `Describe*` → **READ**
- `Create*`, `Attach*`, `Put*`, `Delete*`, `Enable*` → **WRITE**

**AttachUserPolicy** modifies IAM permissions → **WRITE event**, even if the UI omits the label.

---

## 🧪 Evidence
- Screenshot of the CloudTrail event details:
  - `ct_attachpolicy.png`
- JSON event record confirms:
  - `"readOnly": false`
  - `"managementEvent": true`

---

## 🚨 Security Impact
- IAM permissions were modified
- Potential privilege escalation vector
- Requires monitoring and alerting

---

## ✅ Mitigation & Best Practices
- Enforce MFA for root usage
- Minimize root account activity
- Monitor IAM write events via CloudTrail
- Enable alerts for privilege changes

---

## 🧠 Key Takeaways
- Not all WRITE events are explicitly labeled in the UI
- Understanding API naming patterns is critical
- CloudTrail provides defensible forensic evidence
- IAM changes must always be auditable

---

## 📂 Case Status
✔️ Completed  
✔️ Evidence validated  
✔️ Ready for interview discussion
