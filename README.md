# CyberSentry AI 🛡️

### An Offline-First Cybersecurity Incident Analysis Workbench

CyberSentry AI is a browser-based educational prototype for analysing suspicious patterns in security logs using predefined local detection rules.

## Features

* Rule-based detection of selected suspicious activity.
* Identification of repeated authentication failures.
* Detection of possible SQL injection, cross-site scripting (XSS), and path traversal patterns.
* Severity classification to help prioritize investigations.
* Explanations and recommendations for detected indicators.
* Local incident case history.
* JSON export of investigation records.
* Simple browser-based dashboard.

## Technology

* HTML
* CSS
* JavaScript
* Local rule-based detection
* JSON

## Running the Application

1. Clone or download this repository.
2. Open `index.html` in a modern web browser.
3. Use the sample logs or enter your own security logs.
4. Review the findings and export investigation records as JSON.

## Current Status

This GitHub version uses local rule-based detection. Optional QVAC-powered AI explanations are being developed and tested separately; they are not yet verified as part of this published version.

## Limitations

CyberSentry AI is an educational prototype, not a replacement for professional security monitoring or incident-response systems.

Detection depends on predefined rules and supplied log data. A detection is an indicator for further investigation, not definitive proof of an attack. Likewise, no detected findings do not prove that a system is safe.
