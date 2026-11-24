# Indicators of Compromise (IOCs)

## Incident Reference

- Incident ID: LAB03-001
- Classification: Invoice Payment Phishing
- Verdict: Malicious (Simulated)
- Confidence: High

## 1. Email Indicators

| Indicator Type | Value | Relevance |
|---|---|---|
| Display Name | Harbourline Billing | Claimed business identity |
| Sender Address | accounts@harbourline-freight[.]example | Claimed sender |
| Reply-To Address | payments@collections-recovery[.]example | Alternate reply destination |
| Return-Path | bounce@mailer[.]example[.]net | Envelope sender |
| Subject | URGENT: Overdue invoice – payment required immediately | Social engineering lure |

## 2. Network Indicators

| Indicator Type | Value | Relevance |
|---|---|---|
| Domain | harbourline-freight[.]example | Claimed sender domain |
| Domain | collections-recovery[.]example | Reply-To domain |
| Domain | mailer[.]example[.]net | Envelope sender domain |
| Domain | portal.harbourline-freight[.]example | Displayed payment portal |
| IP Address | 203[.]0[.]113[.]45 | Mail routing and hyperlink destination |
| URL | hxxp://203[.]0[.]113[.]45/pay | Actual payment link destination |

## 3. File Indicators

| Indicator Type | Value |
|---|---|
| Filename | invoice_2026.html |
| Extension | .html |
| MIME Type | application/octet-stream |
| Size | 51 bytes |
| SHA-256 | 88b79c686138c48fb28dc796243238c86533a4796861d2e099d475b511cc033f |

## 4. Authentication Indicators

| Mechanism | Result |
|---|---|
| SPF | Fail |
| DKIM | None |
| DMARC | Fail |

These authentication results are contextual indicators rather than standalone proof of malicious activity.

## 5. Behavioral Indicators

- Urgent payment request.
- Threat of service suspension.
- Account verification request.
- Artificial 24-hour deadline.
- Deceptive hyperlink text.
- Direct IP address used as the actual payment destination.
- Suspicious HTML attachment.
- Inconsistent sender-related domains.

## 6. Recommended Detection and Response

In an equivalent real-world incident, a SOC analyst could use verified indicators to:

- Search email gateway logs for matching sender addresses and subjects.
- Search DNS, proxy, and firewall logs for destination infrastructure.
- Search endpoint telemetry for matching attachment hashes.
- Identify other recipients of the phishing campaign.
- Determine whether users interacted with the message.
- Quarantine related malicious emails.
- Escalate suspicious attachments for approved malware analysis.

## 7. Indicator Handling and Limitations

All URLs and domains have been defanged where appropriate to prevent accidental navigation.

This investigation uses a synthetic training sample. The IP address 203.0.113.45 belongs to the TEST-NET-3 documentation range, and the example domains are reserved for documentation.

These indicators must not be treated as verified real-world threat intelligence or deployed as production blocklist entries.

The attachment hash identifies the analyzed attachment but does not independently establish malicious behavior.
