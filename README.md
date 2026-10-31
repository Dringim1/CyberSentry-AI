# CyberSentry AI

### An Offline-First Cybersecurity Incident Analysis Workbench

CyberSentry AI is an educational, browser-based cybersecurity workbench for analysing suspicious patterns in security logs. It combines deterministic local detection rules with optional locally running QVAC inference for AI-generated explanations.

The application is designed to work without cloud AI services. Its detection engine and optional AI explanation assistant can operate locally without an internet connection once the application, QVAC runtime, and model have been installed.

## Features

* Rule-based detection of suspicious activity.
* Identification of repeated authentication failures.
* Detection of possible SQL injection patterns.
* Detection of possible cross-site scripting (XSS) payloads.
* Detection of possible path traversal attempts.
* Severity classification and defensive recommendations.
* Evidence associated with individual findings.
* Local incident case history.
* JSON export of investigation records.
* Optional QVAC-powered AI explanations.
* Basic consistency validation of AI-generated explanations.
* Offline operation with locally running services.

## Technology

* HTML, CSS, and JavaScript.
* Deterministic local detection engine.
* QVAC CLI/server 0.16.0.
* Qwen3 0.6B Instruct Q4_0 (`qwen3-600m-inst-q4`).
* Local OpenAI-compatible API.
* Python HTTP server for local application hosting.

## How It Works

CyberSentry AI uses three separate layers:

**1. Local Detection Engine**

Analyses supplied logs using predefined detection rules. Findings include matching evidence, severity classifications, and recommended defensive actions.

**2. Local AI Explanation Assistant**

Uses a locally running QVAC model to explain existing findings in plain language. The AI does not control detection results or determine finding severity.

**3. AI Response Validation**

Checks basic consistency between the AI response and the trusted rule-based report. Responses that fail validation are withheld.

AI explanations are unverified commentary, not proof that an attack occurred or that a system is vulnerable.

## Running Without QVAC

1. Clone or download this repository.
2. Open `index.html` in a modern browser, or serve the folder using a local HTTP server.
3. Load a sample log or enter your own security logs.
4. Select **Analyze Logs**.
5. Review findings and export investigation records as JSON.

The rule-based detection engine does not require QVAC.

## Running with Local QVAC

The optional AI explanation assistant requires QVAC and its model to run on the same computer as the browser.

### 1. Install QVAC

Install QVAC CLI version 0.16.0 and obtain the model:

`qwen3-600m-inst-q4`

Initial installation and model download require internet access.

### 2. Start the QVAC server

In the terminal where QVAC is installed, run:

```bash
qvac serve --openai --port 11434 --verbose --no-cancel-load-on-disconnect --cors --cors-origin https://dringim1.github.io --cors-origin http://127.0.0.1:8000
```

The local API should be available at:

`http://127.0.0.1:11434`

### 3. Serve the application locally

In PowerShell, navigate to the repository directory and run:

```powershell
py -m http.server 8000 --bind 127.0.0.1
```

Open:

`http://127.0.0.1:8000`

Run an analysis and select **Explain Findings**.

## Offline Operation

After the application, QVAC runtime, and model have been installed or downloaded, local detection and QVAC-powered explanations can operate without an internet connection.

The application was tested offline using:

* Routine logs with zero findings.
* Authentication failures with one HIGH finding.
* Web attack samples with three HIGH findings.

Local QVAC explanations passed the application's basic consistency checks in these tests.

For offline use, serve the application locally rather than relying on an initial GitHub Pages download.

## Deployment Note

GitHub Pages hosts the browser application; it does not host the QVAC model.

The optional AI assistant communicates with a QVAC server running locally on the user's computer. No cloud AI inference is required.

## Limitations

* Detection is based on predefined rules and patterns.
* A rule match does not prove that an attack succeeded.
* The absence of findings does not prove that a system is safe.
* AI-generated explanations may contain inaccuracies.
* Basic consistency validation does not guarantee factual correctness.
* This is an educational prototype, not a replacement for professional security monitoring or incident response tools.

## Project Status

CyberSentry AI is an offline-first educational prototype with working local detection, JSON export, case history, and optional QVAC-powered explanations.
