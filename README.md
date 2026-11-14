# Cedar Bridge — Logon Analysis & Network Investigation (CB-002)

**Role:** SOC Analyst · **Date:** 12 Oct 2026 (simulated) · **Verdict:** Investigate Further (Suspicious Activity)

A deep-dive investigation into a SIEM alert (A01) triggered by multiple failed logons across Windows and Linux systems, followed by a successful authentication. This project demonstrates log normalization, hypothesis testing, and network traffic analysis.

## Scenario
A SIEM rule fired after an external IP (`198.51.100.77`) generated three failed Windows network logons and two failed SSH attempts against the account `amara`, followed by successful authentications on both hosts within an 80-second window. A suspicious phishing email (E01) was delivered to the same user seven minutes prior. 

**Key finding:** While the failures-then-success pattern looks like a brute-force attack, temporal correlation alone does not prove causation. The investigation remains open pending VPN mapping, MFA logs, and user confirmation to distinguish between an external compromise (H1) and legitimate remote access with password typos (H2).

## Skills demonstrated
- **Log Analysis:** Analyzed Windows Security Logs (Event IDs 4624/4625) and Linux SSH auth logs (`/var/log/auth.log`).
- **Timeline Normalization:** Converted mixed time zones (UTC and WAT/+01:00) into a single coherent WAT timeline.
- **Hypothesis Testing:** Evaluated two competing hypotheses (External Guessing vs. Legitimate Remote Access) without jumping to conclusions based on temporal proximity alone.
- **Network Forensics:** Interpreted PCAP data showing DNS queries to an unapproved domain (`billing-review.example`) and identified a plaintext HTTP GET request (noting that a 200 OK does not mean credentials were submitted).
- **Malware Triage:** Drafted hypothetical evidence requests for three different malware scenarios (Ransomware, Infostealer, Dropper) without claiming they occurred.
- **Email Analysis:** Reviewed phishing indicators (urgency, password request, display name mismatch) and noted the absence of SPF/DKIM/DMARC results.

## Repository contents
- `report/`: The sanitized final investigation report and timeline analysis (PDF).

## Sanitization note
All IPs are RFC 5737 documentation ranges, all domains use the reserved `.example` TLD, and all data is fictional. No real client data, credentials, or live infrastructure is included.

## Author
**Umar Mohammed**
