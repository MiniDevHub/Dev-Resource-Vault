<div align="center">

# 🔍 Security Scanners - Complete Vulnerability Detection Guide

![Security](https://img.shields.io/badge/Security-Scanners-red?style=for-the-badge&logo=security)
![Testing](https://img.shields.io/badge/Testing-Automated-blue?style=for-the-badge)
![Level](https://img.shields.io/badge/Level-All_Levels-green?style=for-the-badge)

### _Because finding vulnerabilities before attackers do is critical_ 🛡️

**Unscanned code = Unknown vulnerabilities** 🚨

</div>

---

## 📚 Table of Contents

- [🎯 Security Scanning Fundamentals](#-security-scanning-fundamentals)
- [🔬 Static Analysis (SAST)](#-static-analysis-sast)
- [🌐 Dynamic Analysis (DAST)](#-dynamic-analysis-dast)
- [📦 Dependency Scanning (SCA)](#-dependency-scanning-sca)
- [🐳 Container Scanning](#-container-scanning)
- [☁️ Infrastructure Scanning](#️-infrastructure-scanning)
- [🔐 Secret Scanning](#-secret-scanning)
- [🌍 Network Scanning](#-network-scanning)
- [📱 Mobile App Scanning](#-mobile-app-scanning)
- [🤖 CI/CD Integration](#-cicd-integration)
- [📊 Vulnerability Management](#-vulnerability-management)
- [✅ Best Practices](#-best-practices)

---

<div align="center">

## 🎯 Security Scanning Fundamentals

</div>

### Understanding Security Scanners 🔍

```bash
# ═══════════════════════════════════════════
# WHAT ARE SECURITY SCANNERS?
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SCANNER TYPES OVERVIEW                   ║
╚════════════════════════════════════════════════════════════╝

Definition:
─────────────────────────────────────────────────────────────
Security scanners = Automated tools that detect vulnerabilities,
misconfigurations, and security issues in your applications,
infrastructure, and code.

Why Scan:
─────────────────────────────────────────────────────────────
• Find vulnerabilities before attackers do
• Continuous security monitoring
• Compliance requirements (PCI-DSS, HIPAA, SOC 2)
• Reduce manual security testing effort
• Shift security left (find issues early)
• Track security posture over time

# ═══════════════════════════════════════════
# SCANNER TYPES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SECURITY SCANNING LANDSCAPE              ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

| Type          | Scans          | When               | Speed  | Accuracy | False Positives |
| ------------- | -------------- | ------------------ | ------ | -------- | --------------- |
| **SAST**      | Source code    | Development        | Fast   | Medium   | High            |
| **DAST**      | Running app    | Testing/Production | Slow   | High     | Low             |
| **SCA**       | Dependencies   | Development        | Fast   | High     | Low             |
| **IAST**      | Runtime + code | Testing            | Medium | High     | Low             |
| **Container** | Images         | Build/Deploy       | Fast   | High     | Low             |
| **IaC**       | Config files   | Development        | Fast   | High     | Medium          |
| **Secret**    | Credentials    | All stages         | Fast   | High     | Low             |

</div>

```bash
# ═══════════════════════════════════════════
# SCANNER COMPARISON
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SAST vs DAST vs SCA                      ║
╚════════════════════════════════════════════════════════════╝

SAST (Static Application Security Testing)
─────────────────────────────────────────────────────────────
What: Analyzes source code without executing it
When: During development (pre-commit, CI/CD)
Finds: Code-level vulnerabilities, insecure patterns

Pros:
✅ Finds issues early
✅ Identifies exact location in code
✅ Fast scanning
✅ No running app needed

Cons:
❌ High false positives
❌ Misses runtime issues
❌ Requires source code access

Examples:
• SQL injection patterns
• Cross-site scripting (XSS)
• Hard-coded credentials
• Insecure cryptography
• Buffer overflows

Tools: SonarQube, Semgrep, CodeQL, Checkmarx

DAST (Dynamic Application Security Testing)
─────────────────────────────────────────────────────────────
What: Tests running application (black-box testing)
When: In staging/testing environment
Finds: Runtime vulnerabilities, configuration issues

Pros:
✅ Low false positives
✅ Language/framework agnostic
✅ Finds runtime issues
✅ Tests like real attacker

Cons:
❌ Requires running app
❌ Slower scanning
❌ Doesn't show code location
❌ Limited code coverage

Examples:
• Authentication bypass
• SQL injection (actual exploitation)
• Cross-site scripting (XSS)
• CSRF vulnerabilities
• Security misconfigurations

Tools: OWASP ZAP, Burp Suite, Nikto, Nuclei

SCA (Software Composition Analysis)
─────────────────────────────────────────────────────────────
What: Scans dependencies for known vulnerabilities
When: Continuous (development to production)
Finds: Vulnerable third-party libraries

Pros:
✅ Fast
✅ High accuracy
✅ Easy to fix (update dependency)
✅ CVE database-backed

Cons:
❌ Only finds known vulnerabilities
❌ Doesn't detect custom code issues

Examples:
• Log4Shell (CVE-2021-44228)
• Spring4Shell (CVE-2022-22965)
• Outdated OpenSSL
• Vulnerable npm packages

Tools: Snyk, Dependabot, npm audit, OWASP Dependency-Check

IAST (Interactive Application Security Testing)
─────────────────────────────────────────────────────────────
What: Combines SAST + DAST (monitors running app from inside)
When: During testing
Finds: Vulnerabilities with high accuracy

Pros:
✅ Best of both SAST and DAST
✅ Low false positives
✅ Shows exact code location
✅ Runtime context

Cons:
❌ Performance overhead
❌ Requires instrumentation
❌ Complex setup

Tools: Contrast Security, Hdiv, Seeker

# ═══════════════════════════════════════════
# SCANNING WORKFLOW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   COMPREHENSIVE SECURITY PIPELINE          ║
╚════════════════════════════════════════════════════════════╝

Development Phase:
─────────────────────────────────────────────────────────────
┌─────────────────────────────────────┐
│ 1. IDE Plugins                      │  Real-time feedback
│    • Snyk, SonarLint                │
└─────────────────────────────────────┘
          ↓
┌─────────────────────────────────────┐
│ 2. Pre-commit Hooks                 │  Catch before commit
│    • git-secrets, detect-secrets    │
└─────────────────────────────────────┘
          ↓
┌─────────────────────────────────────┐
│ 3. SAST Scanning                    │  Code analysis
│    • SonarQube, Semgrep             │
└─────────────────────────────────────┘
          ↓
┌─────────────────────────────────────┐
│ 4. SCA Scanning                     │  Dependency check
│    • Snyk, npm audit                │
└─────────────────────────────────────┘

Build Phase:
─────────────────────────────────────────────────────────────
┌─────────────────────────────────────┐
│ 5. Container Scanning               │  Image analysis
│    • Trivy, Grype                   │
└─────────────────────────────────────┘
          ↓
┌─────────────────────────────────────┐
│ 6. IaC Scanning                     │  Config analysis
│    • Checkov, tfsec                 │
└─────────────────────────────────────┘

Deploy Phase:
─────────────────────────────────────────────────────────────
┌─────────────────────────────────────┐
│ 7. DAST Scanning                    │  Runtime testing
│    • OWASP ZAP, Nuclei              │
└─────────────────────────────────────┘
          ↓
┌─────────────────────────────────────┐
│ 8. Infrastructure Scanning          │  Cloud security
│    • Prowler, ScoutSuite            │
└─────────────────────────────────────┘

Production Phase:
─────────────────────────────────────────────────────────────
┌─────────────────────────────────────┐
│ 9. Runtime Protection               │  Active monitoring
│    • Falco, Aqua                    │
└─────────────────────────────────────┘
          ↓
┌─────────────────────────────────────┐
│ 10. Continuous Monitoring           │  Ongoing assessment
│     • Security dashboards           │
└─────────────────────────────────────┘

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔬 Static Analysis (SAST)

</div>

### Code Security Analysis 🔍

```bash
# ═══════════════════════════════════════════
# SONARQUBE (POPULAR SAST)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SONARQUBE SETUP                          ║
╚════════════════════════════════════════════════════════════╝

What is SonarQube:
─────────────────────────────────────────────────────────────
• Open-source code quality & security platform
• Supports 25+ languages
• Finds bugs, vulnerabilities, code smells
• Continuous inspection

Setup with Docker:
─────────────────────────────────────────────────────────────
# docker-compose.yml
version: "3"

services:
  sonarqube:
    image: sonarqube:latest
    ports:
      - "9000:9000"
    environment:
      - SONAR_ES_BOOTSTRAP_CHECKS_DISABLE=true
    volumes:
      - sonarqube_data:/opt/sonarqube/data
      - sonarqube_extensions:/opt/sonarqube/extensions
      - sonarqube_logs:/opt/sonarqube/logs

volumes:
  sonarqube_data:
  sonarqube_extensions:
  sonarqube_logs:

# Start
docker-compose up -d

# Access: http://localhost:9000
# Default credentials: admin/admin

Scan a Project:
─────────────────────────────────────────────────────────────
# Install SonarScanner
npm install -g sonarqube-scanner

# Create sonar-project.properties
cat > sonar-project.properties << EOF
sonar.projectKey=my-project
sonar.projectName=My Project
sonar.projectVersion=1.0
sonar.sources=src
sonar.exclusions=**/node_modules/**,**/*.test.js
sonar.tests=tests
sonar.host.url=http://localhost:9000
sonar.login=YOUR_TOKEN
EOF

# Run scan
sonar-scanner

# Or with npm
npx sonar-scanner

CI/CD Integration (GitHub Actions):
─────────────────────────────────────────────────────────────
# .github/workflows/sonarqube.yml
name: SonarQube Scan

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  sonarqube:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
        with:
          fetch-depth: 0  # Full history for better analysis

      - name: SonarQube Scan
        uses: sonarsource/sonarqube-scan-action@master
        env:
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
          SONAR_HOST_URL: ${{ secrets.SONAR_HOST_URL }}

      - name: Quality Gate
        uses: sonarsource/sonarqube-quality-gate-action@master
        timeout-minutes: 5
        env:
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}

Quality Gate (fail build on issues):
─────────────────────────────────────────────────────────────
# Define thresholds in SonarQube UI:
• Coverage: > 80%
• Duplications: < 3%
• Maintainability Rating: A
• Reliability Rating: A
• Security Rating: A

# Or in sonar-project.properties
sonar.qualitygate.wait=true

# ═══════════════════════════════════════════
# SEMGREP (FAST & FLEXIBLE)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SEMGREP - MODERN SAST                    ║
╚════════════════════════════════════════════════════════════╝

What is Semgrep:
─────────────────────────────────────────────────────────────
• Fast, lightweight SAST tool
• Write custom rules easily
• 30+ languages
• Free & open source

Install:
─────────────────────────────────────────────────────────────
# macOS
brew install semgrep

# pip
pip install semgrep

# npx (no install)
npx semgrep

Basic Scan:
─────────────────────────────────────────────────────────────
# Scan with default rules
semgrep --config=auto .

# Scan with OWASP Top 10 rules
semgrep --config=p/owasp-top-ten .

# Scan with security rules
semgrep --config=p/security-audit .

# Scan specific language
semgrep --config=p/javascript .

# Output formats
semgrep --config=auto --json -o results.json .
semgrep --config=auto --sarif -o results.sarif .

Custom Rules:
─────────────────────────────────────────────────────────────
# rules/sql-injection.yml
rules:
  - id: sql-injection-risk
    patterns:
      - pattern: db.query($SQL + $INPUT)
      - pattern-not: db.query("...")
    message: Potential SQL injection. Use parameterized queries.
    languages: [javascript]
    severity: ERROR
    metadata:
      cwe: "CWE-89: SQL Injection"
      owasp: "A03:2021 - Injection"

# Run with custom rules
semgrep --config=rules/ .

Real-World Examples:
─────────────────────────────────────────────────────────────
# Detect hardcoded secrets
rules:
  - id: hardcoded-password
    pattern: |
      password = "..."
    message: Hardcoded password detected
    severity: ERROR

# Detect XSS vulnerabilities
rules:
  - id: xss-innerHTML
    pattern: |
      $ELEMENT.innerHTML = $USER_INPUT
    message: Potential XSS via innerHTML
    severity: ERROR

# Detect insecure crypto
rules:
  - id: weak-crypto
    patterns:
      - pattern: crypto.createHash("md5")
      - pattern: crypto.createHash("sha1")
    message: Weak hashing algorithm (MD5/SHA1)
    severity: WARNING

CI/CD Integration:
─────────────────────────────────────────────────────────────
# .github/workflows/semgrep.yml
name: Semgrep

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  semgrep:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Run Semgrep
        run: |
          python -m pip install semgrep
          semgrep --config=auto --sarif -o semgrep.sarif .

      - name: Upload results
        uses: github/codeql-action/upload-sarif@v2
        with:
          sarif_file: semgrep.sarif

# ═══════════════════════════════════════════
# CODEQL (GITHUB ADVANCED SECURITY)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CODEQL ANALYSIS                          ║
╚════════════════════════════════════════════════════════════╝

What is CodeQL:
─────────────────────────────────────────────────────────────
• GitHub's semantic code analysis engine
• Query language for code analysis
• Deep analysis (understands code semantics)
• Free for open source

Setup (GitHub Actions):
─────────────────────────────────────────────────────────────
# .github/workflows/codeql.yml
name: CodeQL Analysis

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]
  schedule:
    - cron: '0 0 * * 0'  # Weekly

jobs:
  analyze:
    runs-on: ubuntu-latest
    permissions:
      security-events: write

    strategy:
      matrix:
        language: [javascript, python]

    steps:
      - uses: actions/checkout@v3

      - name: Initialize CodeQL
        uses: github/codeql-action/init@v2
        with:
          languages: ${{ matrix.language }}
          queries: security-extended

      - name: Autobuild
        uses: github/codeql-action/autobuild@v2

      - name: Perform CodeQL Analysis
        uses: github/codeql-action/analyze@v2

Custom Queries:
─────────────────────────────────────────────────────────────
// queries/XSS.ql
import javascript

from DataFlow::Node source, DataFlow::Node sink
where
  source.asExpr() instanceof DomPropRead and
  sink.asExpr() instanceof InnerHtmlWrite and
  DataFlow::pathExists(source, sink)
select sink, "Potential XSS vulnerability"

# ═══════════════════════════════════════════
# ESLint SECURITY PLUGINS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   ESLINT FOR JAVASCRIPT                    ║
╚════════════════════════════════════════════════════════════╝

Setup:
─────────────────────────────────────────────────────────────
# Install
npm install --save-dev \
  eslint \
  eslint-plugin-security \
  eslint-plugin-no-secrets

# .eslintrc.json
{
  "plugins": ["security", "no-secrets"],
  "extends": ["plugin:security/recommended"],
  "rules": {
    "no-secrets/no-secrets": "error",
    "security/detect-object-injection": "error",
    "security/detect-non-literal-regexp": "warn",
    "security/detect-unsafe-regex": "error",
    "security/detect-buffer-noassert": "error",
    "security/detect-child-process": "warn",
    "security/detect-disable-mustache-escape": "error",
    "security/detect-eval-with-expression": "error",
    "security/detect-no-csrf-before-method-override": "error",
    "security/detect-non-literal-fs-filename": "warn",
    "security/detect-non-literal-require": "warn",
    "security/detect-possible-timing-attacks": "error",
    "security/detect-pseudoRandomBytes": "error"
  }
}

# Run
npx eslint .

Common Issues Detected:
─────────────────────────────────────────────────────────────
// ❌ Detected: eval usage
eval(userInput);

// ❌ Detected: unsafe regex
const regex = new RegExp(userInput);

// ❌ Detected: timing attack
if (password === storedPassword) { }

// ❌ Detected: object injection
obj[userInput] = value;

// ✅ Fixed versions
// Use JSON.parse instead of eval
// Validate regex input
// Use constant-time comparison
// Whitelist object keys

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🌐 Dynamic Analysis (DAST)

</div>

### Runtime Security Testing 🕵️

```bash
# ═══════════════════════════════════════════
# OWASP ZAP (POPULAR DAST)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   OWASP ZAP SETUP                          ║
╚════════════════════════════════════════════════════════════╝

What is OWASP ZAP:
─────────────────────────────────────────────────────────────
• Zed Attack Proxy
• Free, open-source web app scanner
• Active & passive scanning
• Intercepting proxy
• Automated & manual testing

Install:
─────────────────────────────────────────────────────────────
# Docker
docker pull owasp/zap2docker-stable

# macOS
brew install --cask owasp-zap

# Linux
wget https://github.com/zaproxy/zaproxy/releases/download/v2.14.0/ZAP_2.14.0_Linux.tar.gz
tar -xvf ZAP_2.14.0_Linux.tar.gz

Basic Scan (Command Line):
─────────────────────────────────────────────────────────────
# Baseline scan (passive)
docker run -t owasp/zap2docker-stable zap-baseline.py \
  -t https://example.com \
  -r zap-report.html

# Full scan (active)
docker run -t owasp/zap2docker-stable zap-full-scan.py \
  -t https://example.com \
  -r zap-report.html

# API scan
docker run -t owasp/zap2docker-stable zap-api-scan.py \
  -t https://api.example.com/openapi.json \
  -f openapi \
  -r zap-api-report.html

Authenticated Scan:
─────────────────────────────────────────────────────────────
# Create context file (zap-context.context)
<?xml version="1.0" encoding="UTF-8"?>
<configuration>
  <context>
    <name>MyApp</name>
    <authentication>
      <type>form</type>
      <loginUrl>https://example.com/login</loginUrl>
      <usernameParameter>username</usernameParameter>
      <passwordParameter>password</passwordParameter>
    </authentication>
    <users>
      <user>
        <name>testuser</name>
        <credentials>
          <username>test@example.com</username>
          <password>testpassword</password>
        </credentials>
      </user>
    </users>
  </context>
</configuration>

# Run with context
docker run -v $(pwd):/zap/wrk/:rw -t owasp/zap2docker-stable \
  zap-full-scan.py \
  -t https://example.com \
  -n zap-context.context \
  -r zap-report.html

CI/CD Integration:
─────────────────────────────────────────────────────────────
# .github/workflows/zap-scan.yml
name: OWASP ZAP Scan

on:
  schedule:
    - cron: '0 0 * * 0'  # Weekly
  workflow_dispatch:

jobs:
  zap_scan:
    runs-on: ubuntu-latest
    steps:
      - name: ZAP Baseline Scan
        uses: zaproxy/action-baseline@v0.7.0
        with:
          target: 'https://staging.example.com'
          rules_file_name: '.zap/rules.tsv'
          cmd_options: '-a'

      - name: Upload Report
        uses: actions/upload-artifact@v3
        with:
          name: zap-report
          path: report_html.html

Custom Rules:
─────────────────────────────────────────────────────────────
# .zap/rules.tsv
# Format: RULE_ID  ACTION  URL_PATTERN

# Ignore false positives
10202   IGNORE  https://example.com/js/
10021   IGNORE  https://example.com/images/

# Fail on critical/high
10015   FAIL    .*
10016   FAIL    .*

# ═══════════════════════════════════════════
# NUCLEI (FAST SCANNER)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   NUCLEI - TEMPLATE-BASED SCANNER          ║
╚════════════════════════════════════════════════════════════╝

What is Nuclei:
─────────────────────────────────────────────────────────────
• Fast vulnerability scanner
• Template-based (YAML)
• 5000+ built-in templates
• Actively maintained
• Great for CVE detection

Install:
─────────────────────────────────────────────────────────────
# macOS/Linux
brew install nuclei

# Go
go install -v github.com/projectdiscovery/nuclei/v2/cmd/nuclei@latest

# Update templates
nuclei -update-templates

Basic Scan:
─────────────────────────────────────────────────────────────
# Scan single target
nuclei -u https://example.com

# Scan multiple targets
nuclei -l targets.txt

# Scan with specific templates
nuclei -u https://example.com -t cves/
nuclei -u https://example.com -t vulnerabilities/

# Scan severity
nuclei -u https://example.com -severity critical,high

# Output
nuclei -u https://example.com -json -o results.json

Template Examples:
─────────────────────────────────────────────────────────────
# nuclei-templates/custom/sql-injection.yaml
id: sql-injection-test

info:
  name: SQL Injection Test
  author: security-team
  severity: critical
  tags: sqli

requests:
  - method: GET
    path:
      - "{{BaseURL}}/search?q=test' OR '1'='1"
      - "{{BaseURL}}/product?id=1' AND 1=1--"

    matchers:
      - type: word
        words:
          - "SQL syntax"
          - "mysql_fetch"
          - "ORA-01"

# nuclei-templates/custom/xss-test.yaml
id: xss-reflected

info:
  name: Reflected XSS
  severity: high

requests:
  - method: GET
    path:
      - "{{BaseURL}}/search?q=<script>alert(1)</script>"

    matchers:
      - type: word
        part: body
        words:
          - "<script>alert(1)</script>"

CI/CD Integration:
─────────────────────────────────────────────────────────────
# .github/workflows/nuclei.yml
name: Nuclei Scan

on:
  schedule:
    - cron: '0 0 * * *'  # Daily

jobs:
  nuclei:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Install Nuclei
        run: |
          go install -v github.com/projectdiscovery/nuclei/v2/cmd/nuclei@latest
          nuclei -update-templates

      - name: Run Scan
        run: |
          nuclei -u https://staging.example.com \
            -severity critical,high \
            -json -o nuclei-results.json

      - name: Upload Results
        uses: actions/upload-artifact@v3
        with:
          name: nuclei-results
          path: nuclei-results.json

# ═══════════════════════════════════════════
# NIKTO (WEB SERVER SCANNER)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   NIKTO WEB SCANNER                        ║
╚════════════════════════════════════════════════════════════╝

What is Nikto:
─────────────────────────────────────────────────────────────
• Web server vulnerability scanner
• Tests for 6700+ vulnerabilities
• Checks server configuration
• Old but still useful

Install:
─────────────────────────────────────────────────────────────
# Docker
docker pull sullo/nikto

# Ubuntu/Debian
sudo apt install nikto

# macOS
brew install nikto

Basic Scan:
─────────────────────────────────────────────────────────────
# Scan target
nikto -h https://example.com

# Scan with SSL
nikto -h https://example.com -ssl

# Scan specific port
nikto -h example.com -p 8080

# Save output
nikto -h https://example.com -o nikto-report.html -Format html

# Tuning options
nikto -h https://example.com -Tuning 123456789

# Tuning options:
# 1: File upload
# 2: Misconfiguration
# 3: Information disclosure
# 4: Injection (XSS/Script/HTML)
# 5: Remote file retrieval
# 6: Denial of service
# 7: Remote file execution
# 8: Command execution
# 9: SQL injection

Docker Usage:
─────────────────────────────────────────────────────────────
docker run --rm sullo/nikto:latest \
  -h https://example.com \
  -o /tmp/nikto-results.html \
  -Format html

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 📦 Dependency Scanning (SCA)

</div>

### Vulnerable Dependencies Detection 🔍

```bash
# ═══════════════════════════════════════════
# NPM AUDIT (BUILT-IN)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   NPM AUDIT                                ║
╚════════════════════════════════════════════════════════════╝

Basic Usage:
─────────────────────────────────────────────────────────────
# Check for vulnerabilities
npm audit

# Output:
# ┌──────────────────────────────────────────────────────────┐
# │                                                          │
# │  High            Regular Expression Denial of Service   │
# │                                                          │
# │  Package         trim                                    │
# │  Patched in      >= 0.0.3                                │
# │  Dependency of   express                                 │
# │  Path            express > body-parser > trim            │
# │  More info       https://npmjs.com/advisories/1000       │
# └──────────────────────────────────────────────────────────┘

# 5 vulnerabilities (2 low, 1 moderate, 1 high, 1 critical)

# Fix automatically
npm audit fix

# Fix with breaking changes
npm audit fix --force

# JSON output
npm audit --json > audit-results.json

# Only specific severity
npm audit --audit-level=high

CI/CD Integration:
─────────────────────────────────────────────────────────────
# .github/workflows/npm-audit.yml
name: NPM Audit

on: [push, pull_request]

jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - uses: actions/setup-node@v3
        with:
          node-version: 18

      - name: Install dependencies
        run: npm ci

      - name: Run npm audit
        run: npm audit --audit-level=moderate

      - name: Check for outdated packages
        run: npm outdated

# ═══════════════════════════════════════════
# SNYK (COMPREHENSIVE SCA)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SNYK - DEVELOPER SECURITY                ║
╚════════════════════════════════════════════════════════════╝

What is Snyk:
─────────────────────────────────────────────────────────────
• Comprehensive security platform
• SCA (dependencies) + SAST (code) + Container + IaC
• Free tier available
• Great developer experience
• Auto-fix pull requests

Install:
─────────────────────────────────────────────────────────────
# npm
npm install -g snyk

# macOS
brew install snyk

# Authenticate
snyk auth

Scan Dependencies:
─────────────────────────────────────────────────────────────
# Test project
snyk test

# Output:
# Testing /path/to/project...
#
# ✗ High severity vulnerability found in lodash
#   Description: Prototype Pollution
#   Info: https://snyk.io/vuln/SNYK-JS-LODASH-590103
#   From: lodash@4.17.15
#   Remediation: Upgrade to lodash@4.17.21
#
# Organization:      my-org
# Package manager:   npm
# Target file:       package-lock.json
# Project name:      my-project
# Open source:       no
# Project path:      /path/to/project
# Licenses:          enabled
#
# Tested 500 dependencies for known issues, found 8 issues.

# Test and monitor
snyk test
snyk monitor  # Upload results to Snyk dashboard

# Fix vulnerabilities
snyk fix

# Test Docker image
snyk container test node:18-alpine

# Test Infrastructure as Code
snyk iac test terraform/

# Test code (SAST)
snyk code test

CI/CD Integration:
─────────────────────────────────────────────────────────────
# .github/workflows/snyk.yml
name: Snyk Security

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  security:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Run Snyk to check for vulnerabilities
        uses: snyk/actions/node@master
        env:
          SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}
        with:
          args: --severity-threshold=high

      - name: Upload result to GitHub Code Scanning
        uses: github/codeql-action/upload-sarif@v2
        with:
          sarif_file: snyk.sarif

Auto-Fix Pull Requests:
─────────────────────────────────────────────────────────────
# Snyk can automatically create PRs to fix vulnerabilities
# Enable in: https://app.snyk.io

# Example PR:
# Title: [Snyk] Security upgrade lodash from 4.17.15 to 4.17.21
# Description:
#   Snyk has created this PR to fix 1 vulnerabilities in npm dependencies.
#
#   ✗ High severity vulnerability found in lodash
#     Prototype Pollution
#     https://snyk.io/vuln/SNYK-JS-LODASH-590103

# ═══════════════════════════════════════════
# DEPENDABOT (GITHUB)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DEPENDABOT CONFIGURATION                 ║
╚════════════════════════════════════════════════════════════╝

Setup:
─────────────────────────────────────────────────────────────
# .github/dependabot.yml
version: 2
updates:
  # npm dependencies
  - package-ecosystem: "npm"
    directory: "/"
    schedule:
      interval: "weekly"
      day: "monday"
      time: "09:00"
    open-pull-requests-limit: 10
    reviewers:
      - "security-team"
    labels:
      - "dependencies"
      - "security"
    commit-message:
      prefix: "chore"
      include: "scope"

    # Group updates
    groups:
      development-dependencies:
        dependency-type: "development"
      production-dependencies:
        dependency-type: "production"

    # Ignore specific dependencies
    ignore:
      - dependency-name: "lodash"
        versions: ["4.17.x"]

  # Docker dependencies
  - package-ecosystem: "docker"
    directory: "/"
    schedule:
      interval: "weekly"

  # GitHub Actions
  - package-ecosystem: "github-actions"
    directory: "/"
    schedule:
      interval: "monthly"

Features:
─────────────────────────────────────────────────────────────
✅ Automatic dependency updates
✅ Security vulnerability alerts
✅ Automated pull requests
✅ Version compatibility checks
✅ Free for public repositories

# ═══════════════════════════════════════════
# OWASP DEPENDENCY-CHECK
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DEPENDENCY-CHECK CLI                     ║
╚════════════════════════════════════════════════════════════╝

What is OWASP Dependency-Check:
─────────────────────────────────────────────────────────────
• Free, open-source SCA tool
• Multi-language support
• CVE database integration
• CI/CD friendly

Install:
─────────────────────────────────────────────────────────────
# Download
wget https://github.com/jeremylong/DependencyCheck/releases/download/v8.4.0/dependency-check-8.4.0-release.zip
unzip dependency-check-8.4.0-release.zip

# Or Docker
docker pull owasp/dependency-check

Scan Project:
─────────────────────────────────────────────────────────────
# Scan directory
./dependency-check/bin/dependency-check.sh \
  --project "My Project" \
  --scan ./src \
  --out ./reports \
  --format HTML

# With Docker
docker run --rm \
  -v $(pwd):/src \
  -v $(pwd)/reports:/report \
  owasp/dependency-check \
  --scan /src \
  --format HTML \
  --out /report

# Fail on CVSS score
./dependency-check.sh \
  --project "My Project" \
  --scan ./src \
  --failOnCVSS 7 \
  --out ./reports

CI/CD Integration:
─────────────────────────────────────────────────────────────
# .github/workflows/dependency-check.yml
name: OWASP Dependency-Check

on:
  schedule:
    - cron: '0 0 * * 0'  # Weekly

jobs:
  dependency-check:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Run Dependency-Check
        uses: dependency-check/Dependency-Check_Action@main
        with:
          project: 'my-project'
          path: '.'
          format: 'HTML'

      - name: Upload Report
        uses: actions/upload-artifact@v3
        with:
          name: dependency-check-report
          path: reports/

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🐳 Container Scanning

</div>

### Docker & Kubernetes Security 🐋

```bash
# ═══════════════════════════════════════════
# TRIVY (COMPREHENSIVE CONTAINER SCANNER)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   TRIVY - AQUA SECURITY                    ║
╚════════════════════════════════════════════════════════════╝

What is Trivy:
─────────────────────────────────────────────────────────────
• Comprehensive vulnerability scanner
• Container images, filesystems, Git repos
• Finds OS packages & language-specific dependencies
• Fast & easy to use

Install:
─────────────────────────────────────────────────────────────
# macOS
brew install trivy

# Linux
wget -qO - https://aquasecurity.github.io/trivy-repo/deb/public.key | sudo apt-key add -
echo "deb https://aquasecurity.github.io/trivy-repo/deb $(lsb_release -sc) main" | sudo tee -a /etc/apt/sources.list.d/trivy.list
sudo apt update
sudo apt install trivy

# Docker
docker pull aquasec/trivy

Scan Docker Image:
─────────────────────────────────────────────────────────────
# Scan image
trivy image node:18-alpine

# Output:
# node:18-alpine (alpine 3.18.4)
# ==============================
# Total: 5 (UNKNOWN: 0, LOW: 0, MEDIUM: 3, HIGH: 2, CRITICAL: 0)
#
# ┌────────────┬────────────────┬──────────┬───────────────────┬───────────────┬──────────────────────────────────────────────────────────────┐
# │  Library   │ Vulnerability  │ Severity │ Installed Version │ Fixed Version │ Title                                                        │
# ├────────────┼────────────────┼──────────┼───────────────────┼───────────────┼──────────────────────────────────────────────────────────────┤
# │ openssl    │ CVE-2023-5363  │ HIGH     │ 3.1.3-r0          │ 3.1.4-r0      │ openssl: Incorrect cipher key and IV length processing      │
# │            │                │          │                   │               │ https://avd.aquasec.com/nvd/cve-2023-5363                   │
# └────────────┴────────────────┴──────────┴───────────────────┴───────────────┴──────────────────────────────────────────────────────────────┘

# Scan with severity threshold
trivy image --severity HIGH,CRITICAL node:18-alpine

# Scan local Dockerfile
trivy config Dockerfile

# Scan built image
docker build -t myapp:latest .
trivy image myapp:latest

# JSON output
trivy image --format json -o results.json node:18-alpine

# Scan filesystem
trivy fs /path/to/project

# Scan git repository
trivy repo https://github.com/user/repo

CI/CD Integration:
─────────────────────────────────────────────────────────────
# .github/workflows/trivy.yml
name: Trivy Security Scan

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  trivy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Build image
        run: docker build -t myapp:${{ github.sha }} .

      - name: Run Trivy vulnerability scanner
        uses: aquasecurity/trivy-action@master
        with:
          image-ref: 'myapp:${{ github.sha }}'
          format: 'sarif'
          output: 'trivy-results.sarif'
          severity: 'CRITICAL,HIGH'

      - name: Upload Trivy results to GitHub Security
        uses: github/codeql-action/upload-sarif@v2
        with:
          sarif_file: 'trivy-results.sarif'

Ignore Specific Vulnerabilities:
─────────────────────────────────────────────────────────────
# .trivyignore
# CVE-2023-1234
# CVE-2023-5678

# Ignore with expiration
CVE-2023-9999 exp:2024-12-31

# ═══════════════════════════════════════════
# GRYPE (VULNERABILITY SCANNER)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   GRYPE BY ANCHORE                         ║
╚════════════════════════════════════════════════════════════╝

Install:
─────────────────────────────────────────────────────────────
# macOS
brew install grype

# Linux
curl -sSfL https://raw.githubusercontent.com/anchore/grype/main/install.sh | sh -s -- -b /usr/local/bin

Scan:
─────────────────────────────────────────────────────────────
# Scan Docker image
grype node:18-alpine

# Scan directory
grype dir:.

# Scan SBOM
syft node:18-alpine -o json | grype

# Fail on severity
grype node:18-alpine --fail-on high

# ═══════════════════════════════════════════
# HADOLINT (DOCKERFILE LINTER)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DOCKERFILE BEST PRACTICES                ║
╚════════════════════════════════════════════════════════════╝

Install:
─────────────────────────────────────────────────────────────
# macOS
brew install hadolint

# Docker
docker pull hadolint/hadolint

Scan Dockerfile:
─────────────────────────────────────────────────────────────
# Scan
hadolint Dockerfile

# Output:
# Dockerfile:1 DL3006 warning: Always tag the version of an image explicitly
# Dockerfile:5 DL3008 warning: Pin versions in apt-get install
# Dockerfile:10 DL3045 warning: `COPY` to a relative destination without `WORKDIR` set

# With Docker
docker run --rm -i hadolint/hadolint < Dockerfile

# Ignore rules
hadolint --ignore DL3006 --ignore DL3008 Dockerfile

# Configuration file (.hadolint.yaml)
ignored:
  - DL3006
  - DL3008

Example Fixes:
─────────────────────────────────────────────────────────────
# ❌ Bad Dockerfile
FROM node
COPY . .
RUN npm install
CMD ["node", "app.js"]

# ✅ Good Dockerfile
FROM node:18-alpine@sha256:...
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production && \
    npm cache clean --force
COPY . .
USER node
CMD ["node", "app.js"]

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## ☁️ Infrastructure Scanning

</div>

### Cloud & IaC Security 🌩️

```bash
# ═══════════════════════════════════════════
# CHECKOV (IAC SCANNER)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   CHECKOV - IAC SECURITY                   ║
╚════════════════════════════════════════════════════════════╝

What is Checkov:
─────────────────────────────────────────────────────────────
• Infrastructure as Code security scanner
• Terraform, CloudFormation, Kubernetes, Dockerfile, ARM, etc.
• 1000+ built-in policies
• Free & open source

Install:
─────────────────────────────────────────────────────────────
# pip
pip install checkov

# Docker
docker pull bridgecrew/checkov

# Homebrew
brew install checkov

Scan Infrastructure:
─────────────────────────────────────────────────────────────
# Scan Terraform
checkov -d terraform/

# Scan CloudFormation
checkov -f cloudformation-template.yaml

# Scan Kubernetes
checkov -d k8s/

# Scan Dockerfile
checkov -f Dockerfile

# Scan with specific frameworks
checkov -d . --framework terraform kubernetes

# Output formats
checkov -d . -o json
checkov -d . -o sarif

# Skip specific checks
checkov -d . --skip-check CKV_AWS_20,CKV_AWS_21

Example Terraform Scan:
─────────────────────────────────────────────────────────────
# main.tf
resource "aws_s3_bucket" "example" {
  bucket = "my-bucket"
  # ❌ No encryption
  # ❌ Public access
  # ❌ No versioning
}

# Run Checkov
checkov -f main.tf

# Output:
# Check: CKV_AWS_18: "Ensure the S3 bucket has access logging enabled"
#   FAILED for resource: aws_s3_bucket.example
#   File: /main.tf:1-3
#
# Check: CKV_AWS_19: "Ensure all data stored in S3 is encrypted"
#   FAILED for resource: aws_s3_bucket.example
#   File: /main.tf:1-3
#
# Check: CKV_AWS_21: "Ensure S3 bucket has versioning enabled"
#   FAILED for resource: aws_s3_bucket.example
#   File: /main.tf:1-3

Fixed Version:
─────────────────────────────────────────────────────────────
# ✅ Fixed main.tf
resource "aws_s3_bucket" "example" {
  bucket = "my-bucket"

  server_side_encryption_configuration {
    rule {
      apply_server_side_encryption_by_default {
        sse_algorithm = "AES256"
      }
    }
  }

  versioning {
    enabled = true
  }

  logging {
    target_bucket = aws_s3_bucket.logs.id
    target_prefix = "access-logs/"
  }
}

resource "aws_s3_bucket_public_access_block" "example" {
  bucket = aws_s3_bucket.example.id

  block_public_acls       = true
  block_public_policy     = true
  ignore_public_acls      = true
  restrict_public_buckets = true
}

CI/CD Integration:
─────────────────────────────────────────────────────────────
# .github/workflows/checkov.yml
name: Checkov IaC Scan

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  checkov:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Run Checkov
        uses: bridgecrewio/checkov-action@master
        with:
          directory: terraform/
          framework: terraform
          output_format: sarif
          output_file_path: checkov-results.sarif

      - name: Upload SARIF file
        uses: github/codeql-action/upload-sarif@v2
        with:
          sarif_file: checkov-results.sarif

Custom Policies:
─────────────────────────────────────────────────────────────
# custom-policies/require-tags.yaml
metadata:
  id: CUSTOM_AWS_1
  name: Ensure all resources have required tags
  category: General

definition:
  cond_type: attribute
  resource_types:
    - aws_instance
    - aws_s3_bucket
  attribute: tags
  operator: contains
  value:
    - Environment
    - Owner
    - Project

# Run with custom policies
checkov -d . --external-checks-dir custom-policies/

# ═══════════════════════════════════════════
# TFSEC (TERRAFORM SCANNER)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   TFSEC - TERRAFORM SECURITY               ║
╚════════════════════════════════════════════════════════════╝

Install:
─────────────────────────────────────────────────────────────
# macOS
brew install tfsec

# Go
go install github.com/aquasecurity/tfsec/cmd/tfsec@latest

# Docker
docker pull aquasec/tfsec

Scan:
─────────────────────────────────────────────────────────────
# Scan directory
tfsec .

# Scan specific directory
tfsec terraform/

# Output formats
tfsec . --format json
tfsec . --format sarif

# Exclude checks
tfsec . --exclude aws-s3-enable-bucket-logging

# Minimum severity
tfsec . --minimum-severity HIGH

Example Output:
─────────────────────────────────────────────────────────────
Result #1 HIGH Bucket does not have logging enabled.
──────────────────────────────────────────────────────────────
  main.tf:1-3
──────────────────────────────────────────────────────────────
   1    resource "aws_s3_bucket" "example" {
   2      bucket = "my-bucket"
   3    }
──────────────────────────────────────────────────────────────
  Impact:     There is no way to determine the access to this bucket
  Resolution: Add a logging block to the resource
  More Info:  https://tfsec.dev/docs/aws/s3/enable-bucket-logging/

Ignore Specific Issues:
─────────────────────────────────────────────────────────────
# In Terraform code
resource "aws_s3_bucket" "example" {
  #tfsec:ignore:aws-s3-enable-bucket-logging
  bucket = "my-bucket"
}

# Or use .tfsec/config.yml
exclude:
  - aws-s3-enable-bucket-logging
  - aws-s3-enable-versioning

# ═══════════════════════════════════════════
# PROWLER (AWS SECURITY)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PROWLER - AWS SECURITY ASSESSMENT        ║
╚════════════════════════════════════════════════════════════╝

What is Prowler:
─────────────────────────────────────────────────────────────
• AWS security best practices assessment
• CIS AWS Foundations Benchmark
• 300+ checks
• Supports AWS, Azure, GCP

Install:
─────────────────────────────────────────────────────────────
# pip
pip install prowler

# Docker
docker pull prowler/prowler

# Git clone
git clone https://github.com/prowler-cloud/prowler
cd prowler
pip install -r requirements.txt

Run Assessment:
─────────────────────────────────────────────────────────────
# Basic scan (uses default AWS credentials)
prowler aws

# Specific region
prowler aws -r us-east-1

# Specific profile
prowler aws -p production-profile

# Specific checks
prowler aws -c check11,check12,check21

# By service
prowler aws -s s3 ec2 rds

# Output formats
prowler aws -M json -o output.json
prowler aws -M html -o report.html
prowler aws -M csv -o findings.csv

# Compliance frameworks
prowler aws -f cis_1.5_aws
prowler aws -f pci_3.2.1_aws
prowler aws -f hipaa_aws

Example Findings:
─────────────────────────────────────────────────────────────
[CHECK] check11: Avoid the use of root account. Show used in last 30 days [root]
  Status: FAIL
  Region: global
  Risk: Critical
  Remediation: Configure MFA and limit root account usage

[CHECK] check12: Ensure MFA is enabled for root account [root]
  Status: FAIL
  Region: global
  Risk: Critical
  Remediation: Enable MFA for root account

[CHECK] check21: Ensure IAM password policy requires minimum length of 14
  Status: FAIL
  Region: global
  Risk: Medium
  Remediation: Update password policy

CI/CD Integration:
─────────────────────────────────────────────────────────────
# .github/workflows/prowler.yml
name: AWS Security Scan

on:
  schedule:
    - cron: '0 0 * * 0'  # Weekly

jobs:
  prowler:
    runs-on: ubuntu-latest
    steps:
      - name: Run Prowler
        run: |
          pip install prowler
          prowler aws \
            -M json \
            -o prowler-results.json \
            -f cis_1.5_aws
        env:
          AWS_ACCESS_KEY_ID: ${{ secrets.AWS_ACCESS_KEY_ID }}
          AWS_SECRET_ACCESS_KEY: ${{ secrets.AWS_SECRET_ACCESS_KEY }}

      - name: Upload Results
        uses: actions/upload-artifact@v3
        with:
          name: prowler-results
          path: prowler-results.json

# ═══════════════════════════════════════════
# SCOUTSUITE (MULTI-CLOUD)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SCOUTSUITE - MULTI-CLOUD SCANNER         ║
╚════════════════════════════════════════════════════════════╝

What is ScoutSuite:
─────────────────────────────────────────────────────────────
• Multi-cloud security auditing tool
• AWS, Azure, GCP, Alibaba Cloud, Oracle Cloud
• HTML reports
• Open source

Install:
─────────────────────────────────────────────────────────────
pip install scoutsuite

Scan Cloud Providers:
─────────────────────────────────────────────────────────────
# AWS
scout aws

# Azure
scout azure --cli

# GCP
scout gcp --user-account

# All regions
scout aws --all-regions

# Specific services
scout aws --services s3 ec2 iam

# Custom report name
scout aws --report-name my-aws-audit

# Output directory
scout aws --report-dir ./reports

Report Features:
─────────────────────────────────────────────────────────────
✅ Interactive HTML dashboard
✅ Risk scoring
✅ Compliance mapping
✅ Remediation guidance
✅ Trend analysis

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🔐 Secret Scanning

</div>

### Detecting Exposed Credentials 🔑

```bash
# ═══════════════════════════════════════════
# GITLEAKS (SECRET DETECTION)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   GITLEAKS - SECRET SCANNER                ║
╚════════════════════════════════════════════════════════════╝

What is Gitleaks:
─────────────────────────────────────────────────────────────
• Scan git repos for secrets
• API keys, passwords, tokens
• Fast & configurable
• Pre-commit hook support

Install:
─────────────────────────────────────────────────────────────
# macOS
brew install gitleaks

# Go
go install github.com/gitleaks/gitleaks/v8@latest

# Docker
docker pull zricethezav/gitleaks

Scan Repository:
─────────────────────────────────────────────────────────────
# Scan current directory
gitleaks detect

# Scan specific directory
gitleaks detect --source /path/to/repo

# Scan with verbose output
gitleaks detect -v

# Output formats
gitleaks detect --report-format json --report-path gitleaks-report.json
gitleaks detect --report-format sarif --report-path gitleaks-report.sarif

# Scan uncommitted changes
gitleaks protect

# Scan specific branch
gitleaks detect --log-opts="origin/main..HEAD"

Example Findings:
─────────────────────────────────────────────────────────────
Finding:     AWS API Key
Secret:      AKIAIOSFODNN7EXAMPLE
RuleID:      aws-access-token
Entropy:     3.854164
File:        config.js
Line:        15
Commit:      1a2b3c4d
Author:      developer@example.com
Date:        2024-01-15

    13 | const config = {
    14 |   database: 'mongodb://localhost',
    15 |   awsKey: 'AKIAIOSFODNN7EXAMPLE',
    16 |   awsSecret: 'wJalrXUtnFEMI/K7MDENG/bPxRfiCYEXAMPLEKEY'
    17 | };

Pre-commit Hook:
─────────────────────────────────────────────────────────────
# Install pre-commit
pip install pre-commit

# .pre-commit-config.yaml
repos:
  - repo: https://github.com/gitleaks/gitleaks
    rev: v8.18.0
    hooks:
      - id: gitleaks

# Install hook
pre-commit install

# Now gitleaks runs before every commit!

Custom Configuration:
─────────────────────────────────────────────────────────────
# .gitleaks.toml
title = "Gitleaks Config"

[[rules]]
id = "custom-api-key"
description = "Custom API Key Pattern"
regex = '''api[_-]?key\s*=\s*['"][a-zA-Z0-9]{32,}['"]'''
tags = ["api", "key"]

[[rules.allowlist]]
paths = [
  '''\.env\.example$''',
  '''README\.md$'''
]

CI/CD Integration:
─────────────────────────────────────────────────────────────
# .github/workflows/gitleaks.yml
name: Gitleaks Secret Scan

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

jobs:
  gitleaks:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
        with:
          fetch-depth: 0

      - name: Run Gitleaks
        uses: gitleaks/gitleaks-action@v2
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
          GITLEAKS_LICENSE: ${{ secrets.GITLEAKS_LICENSE }}

# ═══════════════════════════════════════════
# TRUFFLEHOG (DEEP SECRET SEARCH)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   TRUFFLEHOG - SECRET HUNTING              ║
╚════════════════════════════════════════════════════════════╝

What is TruffleHog:
─────────────────────────────────────────────────────────────
• Deep secret scanning
• Scans git history, files, containers, S3, etc.
• Entropy-based detection
• 700+ credential detectors

Install:
─────────────────────────────────────────────────────────────
# macOS
brew install trufflesecurity/trufflehog/trufflehog

# Docker
docker pull trufflesecurity/trufflehog:latest

# Go
go install github.com/trufflesecurity/trufflehog/v3@latest

Scan Different Sources:
─────────────────────────────────────────────────────────────
# Scan git repository
trufflehog git https://github.com/user/repo

# Scan GitHub org
trufflehog github --org=trufflesecurity

# Scan filesystem
trufflehog filesystem /path/to/files

# Scan Docker image
trufflehog docker --image=myapp:latest

# Scan S3 bucket
trufflehog s3 --bucket=my-bucket

# JSON output
trufflehog git https://github.com/user/repo --json

# Only verified secrets
trufflehog git https://github.com/user/repo --only-verified

Example Finding:
─────────────────────────────────────────────────────────────
🐷🔑🐷  TruffleHog. Unearth your secrets. 🐷🔑🐷

Found verified result 🐷🔑
Detector Type: AWS
Decoder Type: PLAIN
Raw result: AKIAIOSFODNN7EXAMPLE
File: config/production.js
Line: 23
Commit: a1b2c3d4e5f6g7h8i9j0
Timestamp: 2024-01-15 10:30:00
Email: dev@example.com

# ═══════════════════════════════════════════
# DETECT-SECRETS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DETECT-SECRETS - BASELINE APPROACH       ║
╚════════════════════════════════════════════════════════════╝

Install:
─────────────────────────────────────────────────────────────
pip install detect-secrets

Create Baseline:
─────────────────────────────────────────────────────────────
# Scan and create baseline
detect-secrets scan > .secrets.baseline

# Scan with exclusions
detect-secrets scan \
  --exclude-files '.*\.min\.js$' \
  --exclude-files 'package-lock\.json' \
  > .secrets.baseline

# Audit baseline (review findings)
detect-secrets audit .secrets.baseline

# Check against baseline
detect-secrets scan --baseline .secrets.baseline

Pre-commit Hook:
─────────────────────────────────────────────────────────────
# .pre-commit-config.yaml
repos:
  - repo: https://github.com/Yelp/detect-secrets
    rev: v1.4.0
    hooks:
      - id: detect-secrets
        args: ['--baseline', '.secrets.baseline']

# ═══════════════════════════════════════════
# GIT-SECRETS (AWS)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   GIT-SECRETS - AWS FOCUSED                ║
╚════════════════════════════════════════════════════════════╝

Install:
─────────────────────────────────────────────────────────────
# macOS
brew install git-secrets

# Manual
git clone https://github.com/awslabs/git-secrets
cd git-secrets
make install

Setup:
─────────────────────────────────────────────────────────────
# Install hooks in current repo
git secrets --install

# Install hooks in all repos
git secrets --install ~/.git-templates/git-secrets
git config --global init.templateDir ~/.git-templates/git-secrets

# Register AWS patterns
git secrets --register-aws

# Add custom patterns
git secrets --add 'api[_-]?key\s*=\s*[a-zA-Z0-9]{32,}'

Scan:
─────────────────────────────────────────────────────────────
# Scan current changes
git secrets --scan

# Scan entire history
git secrets --scan-history

# Scan specific file
git secrets --scan /path/to/file

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🌍 Network Scanning

</div>

### Network & Port Security 🔍

```bash
# ═══════════════════════════════════════════
# NMAP (NETWORK MAPPER)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   NMAP - THE CLASSIC                       ║
╚════════════════════════════════════════════════════════════╝

What is Nmap:
─────────────────────────────────────────────────────────────
• Network exploration & security auditing
• Port scanning
• Service/version detection
• OS detection
• Network mapping

Install:
─────────────────────────────────────────────────────────────
# macOS
brew install nmap

# Linux
sudo apt install nmap

# Windows
# Download from: https://nmap.org/download.html

Basic Scans:
─────────────────────────────────────────────────────────────
# Scan single host
nmap 192.168.1.1

# Scan subnet
nmap 192.168.1.0/24

# Scan range
nmap 192.168.1.1-50

# Scan specific ports
nmap -p 80,443,8080 192.168.1.1

# Scan port range
nmap -p 1-1000 192.168.1.1

# Scan all ports
nmap -p- 192.168.1.1

Advanced Scans:
─────────────────────────────────────────────────────────────
# Service version detection
nmap -sV 192.168.1.1

# OS detection
nmap -O 192.168.1.1

# Aggressive scan (OS, version, scripts, traceroute)
nmap -A 192.168.1.1

# Fast scan (top 100 ports)
nmap -F 192.168.1.1

# Verbose output
nmap -v 192.168.1.1

# Save output
nmap -oN scan.txt 192.168.1.1
nmap -oX scan.xml 192.168.1.1

Stealth Scans:
─────────────────────────────────────────────────────────────
# SYN scan (stealth)
nmap -sS 192.168.1.1

# UDP scan
nmap -sU 192.168.1.1

# Don't ping (assume host is up)
nmap -Pn 192.168.1.1

# Fragmented packets
nmap -f 192.168.1.1

NSE Scripts (Nmap Scripting Engine):
─────────────────────────────────────────────────────────────
# Vulnerability scan
nmap --script vuln 192.168.1.1

# Default scripts
nmap --script default 192.168.1.1

# HTTP methods
nmap --script http-methods 192.168.1.1

# SSL/TLS vulnerabilities
nmap --script ssl-heartbleed,ssl-poodle,ssl-ccs-injection 192.168.1.1

# SMB vulnerabilities
nmap --script smb-vuln* 192.168.1.1

Example Output:
─────────────────────────────────────────────────────────────
Starting Nmap 7.94

Nmap scan report for example.com (93.184.216.34)
Host is up (0.015s latency).
Not shown: 996 filtered ports

PORT     STATE SERVICE    VERSION
22/tcp   open  ssh        OpenSSH 8.2p1 Ubuntu
80/tcp   open  http       nginx 1.18.0
443/tcp  open  ssl/http   nginx 1.18.0
3306/tcp open  mysql      MySQL 8.0.33

OS details: Linux 5.4
Network Distance: 10 hops

Nmap done: 1 IP address (1 host up) scanned in 15.42 seconds

# ═══════════════════════════════════════════
# MASSCAN (FAST PORT SCANNER)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   MASSCAN - SPEED DEMON                    ║
╚════════════════════════════════════════════════════════════╝

What is Masscan:
─────────────────────────────────────────────────────────────
• Fastest port scanner
• Scan entire internet in 6 minutes (theoretically)
• Asynchronous transmission
• Similar syntax to Nmap

Install:
─────────────────────────────────────────────────────────────
# macOS
brew install masscan

# Linux
sudo apt install masscan

# Build from source
git clone https://github.com/robertdavidgraham/masscan
cd masscan
make
sudo make install

Fast Scans:
─────────────────────────────────────────────────────────────
# Scan subnet
sudo masscan 192.168.1.0/24 -p80,443

# Scan at specific rate (packets/second)
sudo masscan 192.168.1.0/24 -p80,443 --rate 10000

# Scan all ports
sudo masscan 192.168.1.1 -p0-65535

# Save output
sudo masscan 192.168.1.0/24 -p80,443 -oL scan.txt
sudo masscan 192.168.1.0/24 -p80,443 -oX scan.xml

Example:
─────────────────────────────────────────────────────────────
# Scan 10.0.0.0/8 for web servers
sudo masscan 10.0.0.0/8 -p80,443,8080,8443 --rate 100000

# Output:
Discovered open port 443/tcp on 10.0.0.5
Discovered open port 80/tcp on 10.0.0.15
Discovered open port 8080/tcp on 10.0.0.23
...

# ═══════════════════════════════════════════
# TESTSSL.SH (SSL/TLS SCANNER)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   TESTSSL.SH - TLS TESTING                 ║
╚════════════════════════════════════════════════════════════╝

Install:
─────────────────────────────────────────────────────────────
# Clone repo
git clone --depth 1 https://github.com/drwetter/testssl.sh.git
cd testssl.sh

# Or download
wget https://testssl.sh/testssl.sh
chmod +x testssl.sh

Test SSL/TLS:
─────────────────────────────────────────────────────────────
# Basic test
./testssl.sh https://example.com

# Test specific port
./testssl.sh example.com:8443

# Quick test
./testssl.sh --fast https://example.com

# Severity levels
./testssl.sh --severity HIGH https://example.com

# Output formats
./testssl.sh --jsonfile results.json https://example.com
./testssl.sh --htmlfile results.html https://example.com

# Check specific vulnerabilities
./testssl.sh --heartbleed --poodle --crime https://example.com

Example Output:
─────────────────────────────────────────────────────────────
Testing SSL/TLS on example.com:443

 Testing protocols via sockets

 SSLv2      not offered (OK)
 SSLv3      not offered (OK)
 TLS 1      not offered (OK)
 TLS 1.1    not offered (OK)
 TLS 1.2    offered (OK)
 TLS 1.3    offered (OK)

 Testing cipher suites

 Strong ciphers (AEAD)              offered (OK)
 Forward Secrecy (OK)               available

 Testing vulnerabilities

 Heartbleed (CVE-2014-0160)         not vulnerable (OK)
 CCS (CVE-2014-0224)                not vulnerable (OK)
 Ticketbleed (CVE-2016-9244)        not vulnerable (OK)
 ROBOT                              not vulnerable (OK)
 POODLE, SSL (CVE-2014-3566)        not vulnerable (OK)

Rating: A+

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 📱 Mobile App Scanning

</div>

### Mobile Security Testing 📲

```bash
# ═══════════════════════════════════════════
# MOBSF (MOBILE SECURITY FRAMEWORK)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   MOBSF - AUTOMATED MOBILE TESTING         ║
╚════════════════════════════════════════════════════════════╝

What is MobSF:
─────────────────────────────────────────────────────────────
• Automated mobile app security testing
• Android (APK, AAB) & iOS (IPA)
• Static & Dynamic analysis
• Web interface
• REST API

Install (Docker):
─────────────────────────────────────────────────────────────
# Pull image
docker pull opensecurity/mobile-security-framework-mobsf

# Run
docker run -it --rm -p 8000:8000 opensecurity/mobile-security-framework-mobsf

# Access: http://localhost:8000

Features:
─────────────────────────────────────────────────────────────
✅ Static Analysis
   • Manifest analysis
   • Source code analysis
   • Binary analysis
   • Certificate analysis

✅ Dynamic Analysis
   • Runtime behavior
   • API monitoring
   • Data leakage
   • Network traffic

✅ Malware Detection
   • VirusTotal integration
   • Known malware patterns

Scan via API:
─────────────────────────────────────────────────────────────
# Upload APK
curl -X POST "http://localhost:8000/api/v1/upload" \
  -H "Authorization: YOUR_API_KEY" \
  -F "file=@app.apk"

# Scan
curl -X POST "http://localhost:8000/api/v1/scan" \
  -H "Authorization: YOUR_API_KEY" \
  -d "hash=FILE_HASH"

# Get results
curl -X POST "http://localhost:8000/api/v1/report_json" \
  -H "Authorization: YOUR_API_KEY" \
  -d "hash=FILE_HASH"

# ═══════════════════════════════════════════
# APKLEAKS (APK INFORMATION LEAKAGE)
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   APKLEAKS - ANDROID SCANNER               ║
╚════════════════════════════════════════════════════════════╝

Install:
─────────────────────────────────────────────────────────────
pip install apkleaks

Scan APK:
─────────────────────────────────────────────────────────────
# Basic scan
apkleaks -f app.apk

# JSON output
apkleaks -f app.apk -o results.json

# Custom patterns
apkleaks -f app.apk -p custom-patterns.json

Findings:
─────────────────────────────────────────────────────────────
• API keys
• URLs
• AWS credentials
• Firebase configs
• Database credentials
• Hardcoded secrets

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🤖 CI/CD Integration

</div>

### Complete Security Pipeline 🔄

```bash
# ═══════════════════════════════════════════
# COMPREHENSIVE CI/CD SECURITY PIPELINE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   GITHUB ACTIONS EXAMPLE                   ║
╚════════════════════════════════════════════════════════════╝

# .github/workflows/security-pipeline.yml
name: Comprehensive Security Scan

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]
  schedule:
    - cron: '0 0 * * 0'  # Weekly full scan

jobs:
  # ═══════════════════════════════════════════
  # JOB 1: SECRET SCANNING
  # ═══════════════════════════════════════════
  secrets:
    name: Secret Scanning
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
        with:
          fetch-depth: 0

      - name: Gitleaks
        uses: gitleaks/gitleaks-action@v2
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

      - name: TruffleHog
        run: |
          docker run --rm -v $(pwd):/src \
            trufflesecurity/trufflehog:latest \
            filesystem /src --json > trufflehog-results.json

      - name: Upload Results
        uses: actions/upload-artifact@v3
        with:
          name: secret-scan-results
          path: |
            trufflehog-results.json

  # ═══════════════════════════════════════════
  # JOB 2: DEPENDENCY SCANNING
  # ═══════════════════════════════════════════
  dependencies:
    name: Dependency Scanning
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - uses: actions/setup-node@v3
        with:
          node-version: 18

      - name: Install dependencies
        run: npm ci

      - name: NPM Audit
        run: npm audit --audit-level=moderate
        continue-on-error: true

      - name: Snyk Test
        uses: snyk/actions/node@master
        env:
          SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}
        with:
          args: --severity-threshold=high

      - name: OWASP Dependency-Check
        uses: dependency-check/Dependency-Check_Action@main
        with:
          project: 'my-project'
          path: '.'
          format: 'HTML'

      - name: Upload Reports
        uses: actions/upload-artifact@v3
        with:
          name: dependency-reports
          path: reports/

  # ═══════════════════════════════════════════
  # JOB 3: SAST (CODE ANALYSIS)
  # ═══════════════════════════════════════════
  sast:
    name: Static Code Analysis
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: SonarQube Scan
        uses: sonarsource/sonarqube-scan-action@master
        env:
          SONAR_TOKEN: ${{ secrets.SONAR_TOKEN }}
          SONAR_HOST_URL: ${{ secrets.SONAR_HOST_URL }}

      - name: Semgrep
        run: |
          python -m pip install semgrep
          semgrep --config=auto --sarif -o semgrep.sarif .

      - name: CodeQL Analysis
        uses: github/codeql-action/analyze@v2

      - name: Upload SARIF
        uses: github/codeql-action/upload-sarif@v2
        with:
          sarif_file: semgrep.sarif

  # ═══════════════════════════════════════════
  # JOB 4: CONTAINER SCANNING
  # ═══════════════════════════════════════════
  container:
    name: Container Scanning
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Build Docker Image
        run: docker build -t myapp:${{ github.sha }} .

      - name: Trivy Scan
        uses: aquasecurity/trivy-action@master
        with:
          image-ref: 'myapp:${{ github.sha }}'
          format: 'sarif'
          output: 'trivy-results.sarif'
          severity: 'CRITICAL,HIGH'

      - name: Hadolint
        uses: hadolint/hadolint-action@v3.1.0
        with:
          dockerfile: Dockerfile

      - name: Upload Results
        uses: github/codeql-action/upload-sarif@v2
        with:
          sarif_file: trivy-results.sarif

  # ═══════════════════════════════════════════
  # JOB 5: IAC SCANNING
  # ═══════════════════════════════════════════
  iac:
    name: Infrastructure as Code
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3

      - name: Checkov
        uses: bridgecrewio/checkov-action@master
        with:
          directory: terraform/
          framework: terraform
          output_format: sarif
          output_file_path: checkov-results.sarif

      - name: TFSec
        uses: aquasecurity/tfsec-action@v1.0.0
        with:
          working_directory: terraform/

      - name: Upload SARIF
        uses: github/codeql-action/upload-sarif@v2
        with:
          sarif_file: checkov-results.sarif

  # ═══════════════════════════════════════════
  # JOB 6: DAST (DYNAMIC TESTING)
  # ═══════════════════════════════════════════
  dast:
    name: Dynamic Application Testing
    runs-on: ubuntu-latest
    needs: [sast, dependencies]
    if: github.event_name == 'schedule'
    steps:
      - uses: actions/checkout@v3

      - name: Deploy to Staging
        run: |
          # Deploy application to staging environment
          echo "Deploying to staging..."

      - name: OWASP ZAP Scan
        uses: zaproxy/action-baseline@v0.7.0
        with:
          target: 'https://staging.example.com'
          rules_file_name: '.zap/rules.tsv'

      - name: Nuclei Scan
        run: |
          docker run projectdiscovery/nuclei:latest \
            -u https://staging.example.com \
            -severity critical,high \
            -json -o nuclei-results.json

      - name: Upload Results
        uses: actions/upload-artifact@v3
        with:
          name: dast-results
          path: |
            nuclei-results.json
            report_html.html

  # ═══════════════════════════════════════════
  # JOB 7: SECURITY REPORT
  # ═══════════════════════════════════════════
  report:
    name: Generate Security Report
    runs-on: ubuntu-latest
    needs: [secrets, dependencies, sast, container, iac]
    if: always()
    steps:
      - name: Download all artifacts
        uses: actions/download-artifact@v3

      - name: Generate Summary Report
        run: |
          echo "# Security Scan Summary" > report.md
          echo "Generated: $(date)" >> report.md
          echo "" >> report.md
          echo "## Scan Results" >> report.md
          # Aggregate results from all jobs

      - name: Post to Slack
        uses: slackapi/slack-github-action@v1.24.0
        with:
          payload: |
            {
              "text": "Security scan completed",
              "blocks": [
                {
                  "type": "section",
                  "text": {
                    "type": "mrkdwn",
                    "text": "Security scan completed for ${{ github.repository }}"
                  }
                }
              ]
            }
        env:
          SLACK_WEBHOOK_URL: ${{ secrets.SLACK_WEBHOOK }}

# ═══════════════════════════════════════════
# GITLAB CI EXAMPLE
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   .gitlab-ci.yml                           ║
╚════════════════════════════════════════════════════════════╝

stages:
  - secrets
  - sast
  - dependencies
  - container
  - dast
  - report

# Secret Scanning
gitleaks:
  stage: secrets
  image: zricethezav/gitleaks:latest
  script:
    - gitleaks detect --report-format json --report-path gitleaks-report.json
  artifacts:
    reports:
      secret_detection: gitleaks-report.json

# SAST
semgrep:
  stage: sast
  image: returntocorp/semgrep
  script:
    - semgrep --config=auto --sarif -o semgrep.sarif .
  artifacts:
    reports:
      sast: semgrep.sarif

# Dependency Scanning
npm-audit:
  stage: dependencies
  image: node:18
  script:
    - npm ci
    - npm audit --audit-level=moderate

snyk:
  stage: dependencies
  image: snyk/snyk:node
  script:
    - snyk test --severity-threshold=high
  allow_failure: true

# Container Scanning
trivy:
  stage: container
  image: aquasec/trivy:latest
  script:
    - trivy image --severity HIGH,CRITICAL myapp:latest

# DAST
zap:
  stage: dast
  image: owasp/zap2docker-stable
  script:
    - zap-baseline.py -t https://staging.example.com -r zap-report.html
  artifacts:
    paths:
      - zap-report.html
  only:
    - schedules

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 📊 Vulnerability Management

</div>

### Tracking & Remediation 📈

```bash
# ═══════════════════════════════════════════
# VULNERABILITY MANAGEMENT WORKFLOW
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PRIORITIZATION FRAMEWORK                 ║
╚════════════════════════════════════════════════════════════╝

Severity Levels:
─────────────────────────────────────────────────────────────
🔴 CRITICAL (CVSS 9.0-10.0)
   • Remote code execution
   • Authentication bypass
   • SQL injection with data access

   Response: Fix immediately (24 hours)

🟠 HIGH (CVSS 7.0-8.9)
   • Privilege escalation
   • Cross-site scripting (stored)
   • Sensitive data exposure

   Response: Fix within 7 days

🟡 MEDIUM (CVSS 4.0-6.9)
   • Cross-site scripting (reflected)
   • Information disclosure
   • CSRF vulnerabilities

   Response: Fix within 30 days

🟢 LOW (CVSS 0.1-3.9)
   • Version disclosure
   • Weak SSL/TLS ciphers
   • Missing headers

   Response: Fix in next release

Triage Process:
─────────────────────────────────────────────────────────────
1. Verify vulnerability is real (not false positive)
2. Assess exploitability
3. Determine business impact
4. Check if actively exploited (CISA KEV)
5. Prioritize based on risk
6. Assign to developer
7. Track remediation
8. Verify fix
9. Deploy

Risk Calculation:
─────────────────────────────────────────────────────────────
Risk = Severity × Exploitability × Exposure

Exposure Factors:
• Public-facing vs internal
• Authenticated vs unauthenticated
• Data sensitivity
• Regulatory requirements

# ═══════════════════════════════════════════
# VULNERABILITY TRACKING
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   TRACKING TEMPLATE                        ║
╚════════════════════════════════════════════════════════════╝

vulnerability-tracker.md:
─────────────────────────────────────────────────────────────
# Security Vulnerabilities

## Critical (Must Fix Immediately)

| ID | Vulnerability | CVSS | Component | Status | Assigned | Due Date |
|----|---------------|------|-----------|--------|----------|----------|
| V-001 | SQL Injection | 9.8 | login.js | Open | @dev1 | 2024-01-21 |
| V-002 | RCE in lib | 9.9 | express | In Progress | @dev2 | 2024-01-21 |

## High (Fix Within 7 Days)

| ID | Vulnerability | CVSS | Component | Status | Assigned | Due Date |
|----|---------------|------|-----------|--------|----------|----------|
| V-003 | XSS (Stored) | 8.1 | comments | Open | @dev3 | 2024-01-28 |
| V-004 | Auth Bypass | 8.5 | middleware | Testing | @dev1 | 2024-01-28 |

## Medium (Fix Within 30 Days)

| ID | Vulnerability | CVSS | Component | Status | Assigned | Due Date |
|----|---------------|------|-----------|--------|----------|----------|
| V-005 | CSRF | 6.5 | forms | Open | @dev4 | 2024-02-15 |

## Fixed

| ID | Vulnerability | Fixed In | Fix Date | Verified |
|----|---------------|----------|----------|----------|
| V-000 | Log4Shell | v2.17.0 | 2024-01-15 | ✅ |

GitHub Issues Integration:
─────────────────────────────────────────────────────────────
# Auto-create issues from scan results

name: Create Security Issues

on:
  workflow_run:
    workflows: ["Security Scan"]
    types: [completed]

jobs:
  create-issues:
    runs-on: ubuntu-latest
    steps:
      - name: Download scan results
        uses: actions/download-artifact@v3

      - name: Parse results and create issues
        uses: actions/github-script@v6
        with:
          script: |
            const results = require('./scan-results.json');

            for (const vuln of results.vulnerabilities) {
              if (vuln.severity === 'CRITICAL' || vuln.severity === 'HIGH') {
                await github.rest.issues.create({
                  owner: context.repo.owner,
                  repo: context.repo.repo,
                  title: `[Security] ${vuln.title}`,
                  body: `
## Vulnerability Details

- **Severity**: ${vuln.severity}
- **CVSS Score**: ${vuln.cvss}
- **Component**: ${vuln.component}
- **CVE**: ${vuln.cve}

## Description
${vuln.description}

## Remediation
${vuln.remediation}

## References
${vuln.references.join('\n')}
                  `,
                  labels: ['security', vuln.severity.toLowerCase()]
                });
              }
            }

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## ✅ Best Practices

</div>

### Security Scanning Guidelines 📋

```bash
# ═══════════════════════════════════════════
# SECURITY SCANNING BEST PRACTICES
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   COMPREHENSIVE CHECKLIST                  ║
╚════════════════════════════════════════════════════════════╝

Scanning Strategy:
─────────────────────────────────────────────────────────────
✅ Scan Early & Often
   ☐ IDE plugins for real-time feedback
   ☐ Pre-commit hooks for secrets
   ☐ PR checks for code quality
   ☐ Daily scans on develop branch
   ☐ Weekly full security scans

✅ Multiple Layers
   ☐ SAST (code)
   ☐ SCA (dependencies)
   ☐ Container scanning
   ☐ IaC scanning
   ☐ Secret scanning
   ☐ DAST (runtime)

✅ Automate Everything
   ☐ CI/CD integration
   ☐ Automatic issue creation
   ☐ Auto-fix where possible
   ☐ Scheduled scans
   ☐ Continuous monitoring

✅ Prioritize Findings
   ☐ Focus on critical/high first
   ☐ Consider exploitability
   ☐ Check active exploitation
   ☐ Assess business impact
   ☐ Fix false positives

✅ Track & Measure
   ☐ Vulnerability trends
   ☐ Time to remediation
   ☐ False positive rate
   ☐ Scanner coverage
   ☐ Security debt

Tool Selection:
─────────────────────────────────────────────────────────────
☐ Choose tools for your stack
☐ Prefer open source where possible
☐ Ensure CI/CD integration
☐ Check false positive rate
☐ Consider cost vs value
☐ Evaluate support & community

Configuration:
─────────────────────────────────────────────────────────────
☐ Tune scanner settings
☐ Configure severity thresholds
☐ Exclude false positives
☐ Set up proper authentication
☐ Define scanning scope
☐ Configure output formats

Results Management:
─────────────────────────────────────────────────────────────
☐ Centralize results
☐ Deduplicate findings
☐ Track remediation status
☐ Document exceptions
☐ Archive historical scans
☐ Generate compliance reports

Team Practices:
─────────────────────────────────────────────────────────────
☐ Security training for developers
☐ Clear ownership of findings
☐ SLA for remediation
☐ Regular security reviews
☐ Threat modeling sessions
☐ Post-incident reviews

╔════════════════════════════════════════════════════════════╗
║                   COMMON PITFALLS TO AVOID                 ║
╚════════════════════════════════════════════════════════════╝

❌ Don't:
─────────────────────────────────────────────────────────────
☐ Rely on a single scanner type
☐ Ignore scanner output
☐ Trust scanners blindly (validate findings)
☐ Scan only before release
☐ Block deployments without triage
☐ Let security debt accumulate
☐ Forget to update scanner rules
☐ Skip fixing false positives
☐ Ignore low-severity findings forever
☐ Run scans without ownership

✅ Do:
─────────────────────────────────────────────────────────────
☐ Use defense in depth (multiple scanners)
☐ Act on findings promptly
☐ Verify vulnerabilities manually
☐ Scan continuously
☐ Allow overrides with justification
☐ Fix vulnerabilities incrementally
☐ Keep scanners updated
☐ Document false positives
☐ Review all findings eventually
☐ Assign clear ownership

╔════════════════════════════════════════════════════════════╗
║                   FALSE POSITIVE MANAGEMENT                ║
╚════════════════════════════════════════════════════════════╝

Handling False Positives:
─────────────────────────────────────────────────────────────
1. Verify it's actually a false positive
   • Test manually
   • Understand the context
   • Consult security team

2. Document the reasoning
   • Why is it not exploitable?
   • What mitigations are in place?
   • Any compensating controls?

3. Suppress in scanner
   • Use scanner-specific ignore syntax
   • Add inline comments
   • Create exclusion rules

4. Track suppressions
   • Review quarterly
   • Verify still valid
   • Update if code changes

Example Suppression:
─────────────────────────────────────────────────────────────
// Semgrep
// nosemgrep: javascript.express.security.audit.xss.direct-response-write
app.get('/safe', (req, res) => {
  // This is safe because input is sanitized above
  res.send(sanitizedOutput);
});

# Trivy
# .trivyignore
CVE-2023-1234 # False positive: library not used in affected way
CVE-2023-5678 # Risk accepted: isolated environment

# SonarQube
// NOSONAR - Suppressed because this is safe in this context

╔════════════════════════════════════════════════════════════╗
║                   SCANNER EFFECTIVENESS METRICS            ║
╚════════════════════════════════════════════════════════════╝

Key Metrics to Track:
─────────────────────────────────────────────────────────────
1. Coverage
   • % of codebase scanned
   • % of dependencies scanned
   • % of infrastructure scanned

2. Detection Rate
   • Vulnerabilities found
   • True positives vs false positives
   • Critical/High findings

3. Time to Remediation
   • Average time to fix critical
   • Average time to fix high
   • Overall remediation velocity

4. Security Debt
   • Total open vulnerabilities
   • Trend over time
   • Aged vulnerabilities (>90 days)

5. False Positive Rate
   • FP / Total findings
   • By scanner
   • By severity

Dashboard Example:
─────────────────────────────────────────────────────────────
┌─────────────────────────────────────────────────────────┐
│  Security Scanning Dashboard - January 2024            │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  Open Vulnerabilities:  42  (↓ 15 from last month)    │
│    Critical: 0                                         │
│    High:     3  [MUST FIX]                            │
│    Medium:   15                                        │
│    Low:      24                                        │
│                                                         │
│  Scans This Month:  450                               │
│    SAST:      120                                      │
│    SCA:       180                                      │
│    Container:  90                                      │
│    DAST:       60                                      │
│                                                         │
│  Avg Time to Fix:                                     │
│    Critical:  2.3 hours  ✅                           │
│    High:      18 hours   ✅                           │
│    Medium:    8 days     ⚠️                            │
│                                                         │
│  False Positive Rate:  12%  (↓ 3% improvement)        │
│                                                         │
└─────────────────────────────────────────────────────────┘

# ═══════════════════════════════════════════
# RECOMMENDED TOOL COMBINATIONS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SCANNER STACK BY PROJECT TYPE            ║
╚════════════════════════════════════════════════════════════╝

Startup / Small Team (Free Tools):
─────────────────────────────────────────────────────────────
SAST:           Semgrep (free)
SCA:            npm audit + Dependabot (free)
Container:      Trivy (free)
IaC:            Checkov (free)
Secret:         Gitleaks (free)
DAST:           OWASP ZAP (free)

Total Cost: $0/month
Setup Time: 1-2 days

Mid-Size Company (Mixed):
─────────────────────────────────────────────────────────────
SAST:           SonarQube Community + Semgrep
SCA:            Snyk (paid tier)
Container:      Trivy + Snyk Container
IaC:            Checkov + Snyk IaC
Secret:         Gitleaks + GitGuardian
DAST:           OWASP ZAP + Nuclei

Total Cost: ~$500-2000/month
Setup Time: 1 week

Enterprise (Comprehensive):
─────────────────────────────────────────────────────────────
SAST:           SonarQube Enterprise + CodeQL
SCA:            Snyk Enterprise + BlackDuck
Container:      Aqua Security + Snyk
IaC:            Bridgecrew + Checkov
Secret:         GitGuardian Enterprise
DAST:           Burp Suite Enterprise + ZAP
Cloud:          Prowler + ScoutSuite
Compliance:     Wiz + Orca Security

Total Cost: $10,000-50,000+/month
Setup Time: 2-4 weeks

Open Source Project:
─────────────────────────────────────────────────────────────
SAST:           Semgrep + CodeQL (free for OSS)
SCA:            Dependabot + Snyk (free for OSS)
Container:      Trivy
IaC:            Checkov
Secret:         Gitleaks
DAST:           OWASP ZAP

Total Cost: $0/month
Setup Time: 1 day

╔════════════════════════════════════════════════════════════╗
║                   LANGUAGE-SPECIFIC RECOMMENDATIONS        ║
╚════════════════════════════════════════════════════════════╝

JavaScript/Node.js:
─────────────────────────────────────────────────────────────
✅ npm audit (built-in)
✅ ESLint + security plugins
✅ Semgrep (JavaScript rules)
✅ Snyk
✅ RetireJS (client-side)

Python:
─────────────────────────────────────────────────────────────
✅ Bandit (SAST)
✅ Safety (SCA)
✅ Semgrep (Python rules)
✅ pip-audit
✅ Snyk

Java:
─────────────────────────────────────────────────────────────
✅ SpotBugs + Find Security Bugs
✅ SonarQube
✅ OWASP Dependency-Check
✅ Snyk
✅ Checkmarx

Go:
─────────────────────────────────────────────────────────────
✅ gosec (SAST)
✅ govulncheck (SCA)
✅ Semgrep (Go rules)
✅ Snyk

Rust:
─────────────────────────────────────────────────────────────
✅ cargo audit (SCA)
✅ cargo-geiger (unsafe code)
✅ Semgrep (Rust rules)

.NET/C#:
─────────────────────────────────────────────────────────────
✅ Security Code Scan
✅ SonarQube
✅ OWASP Dependency-Check
✅ Snyk

# ═══════════════════════════════════════════
# SCANNER COMPARISON MATRIX
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   DETAILED SCANNER COMPARISON              ║
╚════════════════════════════════════════════════════════════╝
```

<div align="center">

### SAST Tools

| Tool                | Languages | Price      | Accuracy   | Speed      | IDE Support | CI/CD |
| ------------------- | --------- | ---------- | ---------- | ---------- | ----------- | ----- |
| **SonarQube**       | 25+       | Free-$$$   | ⭐⭐⭐⭐   | ⭐⭐⭐     | ✅          | ✅    |
| **Semgrep**         | 30+       | Free-$$    | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ✅          | ✅    |
| **CodeQL**          | 15+       | Free (OSS) | ⭐⭐⭐⭐⭐ | ⭐⭐⭐     | ✅          | ✅    |
| **Checkmarx**       | 25+       | $$$        | ⭐⭐⭐⭐   | ⭐⭐       | ✅          | ✅    |
| **Veracode**        | 20+       | $$$        | ⭐⭐⭐⭐   | ⭐⭐       | ✅          | ✅    |
| **ESLint Security** | JS only   | Free       | ⭐⭐⭐     | ⭐⭐⭐⭐⭐ | ✅          | ✅    |

### SCA Tools

| Tool            | Features | Price    | Accuracy   | Auto-Fix | License Check |
| --------------- | -------- | -------- | ---------- | -------- | ------------- |
| **Snyk**        | Full     | Free-$$$ | ⭐⭐⭐⭐⭐ | ✅       | ✅            |
| **Dependabot**  | Basic    | Free     | ⭐⭐⭐⭐   | ✅       | ✅            |
| **npm audit**   | Basic    | Free     | ⭐⭐⭐     | ✅       | ❌            |
| **OWASP DC**    | Full     | Free     | ⭐⭐⭐⭐   | ❌       | ✅            |
| **BlackDuck**   | Full     | $$$      | ⭐⭐⭐⭐⭐ | ❌       | ✅            |
| **WhiteSource** | Full     | $$$      | ⭐⭐⭐⭐   | ✅       | ✅            |

### DAST Tools

| Tool           | Type           | Price    | Coverage   | Speed      | API Testing |
| -------------- | -------------- | -------- | ---------- | ---------- | ----------- |
| **OWASP ZAP**  | Active/Passive | Free     | ⭐⭐⭐⭐   | ⭐⭐⭐     | ✅          |
| **Burp Suite** | Active/Passive | Free-$$$ | ⭐⭐⭐⭐⭐ | ⭐⭐⭐     | ✅          |
| **Nuclei**     | Active         | Free     | ⭐⭐⭐⭐   | ⭐⭐⭐⭐⭐ | ✅          |
| **Nikto**      | Active         | Free     | ⭐⭐⭐     | ⭐⭐⭐⭐   | ❌          |
| **Acunetix**   | Active         | $$$      | ⭐⭐⭐⭐⭐ | ⭐⭐⭐     | ✅          |

### Container Scanners

| Tool               | Features | Price    | Speed      | Accuracy   | K8s Support |
| ------------------ | -------- | -------- | ---------- | ---------- | ----------- |
| **Trivy**          | Full     | Free     | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ | ✅          |
| **Grype**          | Full     | Free     | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐   | ✅          |
| **Snyk Container** | Full     | Free-$$$ | ⭐⭐⭐⭐   | ⭐⭐⭐⭐⭐ | ✅          |
| **Aqua**           | Full     | $$$      | ⭐⭐⭐⭐   | ⭐⭐⭐⭐⭐ | ✅          |
| **Anchore**        | Full     | Free-$$  | ⭐⭐⭐     | ⭐⭐⭐⭐   | ✅          |

</div>

```bash
# ═══════════════════════════════════════════
# IMPLEMENTATION ROADMAP
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   PHASED ROLLOUT PLAN                      ║
╚════════════════════════════════════════════════════════════╝

Phase 1: Foundation (Week 1-2)
─────────────────────────────────────────────────────────────
☐ Set up secret scanning (Gitleaks)
   • Pre-commit hooks
   • CI/CD integration
   • Scan git history

☐ Enable dependency scanning
   • npm audit / pip-audit
   • Dependabot
   • Fix critical vulnerabilities

☐ Establish baseline
   • Document current state
   • Count existing vulnerabilities
   • Set initial goals

Phase 2: Code Analysis (Week 3-4)
─────────────────────────────────────────────────────────────
☐ Deploy SAST tool (Semgrep)
   • Configure rules
   • Run initial scan
   • Triage findings

☐ Add linter security plugins
   • ESLint security
   • Language-specific linters
   • IDE integration

☐ Create security gates
   • Block critical findings in PRs
   • Require review for high findings

Phase 3: Container & IaC (Week 5-6)
─────────────────────────────────────────────────────────────
☐ Implement container scanning (Trivy)
   • Scan base images
   • Scan application images
   • CI/CD integration

☐ Add IaC scanning (Checkov)
   • Scan Terraform
   • Scan CloudFormation
   • Scan Kubernetes manifests

☐ Dockerfile best practices
   • Add Hadolint
   • Fix common issues

Phase 4: Dynamic Testing (Week 7-8)
─────────────────────────────────────────────────────────────
☐ Set up DAST (OWASP ZAP)
   • Configure scanning rules
   • Scan staging environment
   • Schedule weekly scans

☐ Add API security testing
   • Test authentication
   • Test authorization
   • Test input validation

Phase 5: Monitoring & Optimization (Week 9-10)
─────────────────────────────────────────────────────────────
☐ Create security dashboard
   • Aggregate scan results
   • Track metrics
   • Generate reports

☐ Tune scanners
   • Reduce false positives
   • Optimize scan performance
   • Refine rules

☐ Training & documentation
   • Developer training
   • Runbooks for findings
   • Response procedures

Phase 6: Continuous Improvement (Ongoing)
─────────────────────────────────────────────────────────────
☐ Regular review cycles
   • Monthly: Review metrics
   • Quarterly: Update scanners
   • Annually: Assess strategy

☐ Stay updated
   • New vulnerabilities (CVEs)
   • New scanning techniques
   • Tool updates

╔════════════════════════════════════════════════════════════╗
║                   SUCCESS CRITERIA                         ║
╚════════════════════════════════════════════════════════════╝

30-Day Goals:
─────────────────────────────────────────────────────────────
☐ All secrets removed from code
☐ No critical vulnerabilities in production
☐ Dependency scanning in CI/CD
☐ SAST running on every PR
☐ Security dashboard operational

90-Day Goals:
─────────────────────────────────────────────────────────────
☐ All high vulnerabilities remediated
☐ Container scanning implemented
☐ IaC scanning implemented
☐ DAST running weekly
☐ False positive rate < 20%
☐ Avg remediation time < 7 days (high)

1-Year Goals:
─────────────────────────────────────────────────────────────
☐ All medium vulnerabilities addressed
☐ Comprehensive scanning coverage
☐ False positive rate < 10%
☐ Avg remediation time < 3 days (high)
☐ Zero security incidents from known vulns
☐ Security-first culture established

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 🎓 Resources & Further Learning

</div>

### Essential Security Scanner Resources 📚

```
📘 Official Documentation
   OWASP ZAP: https://www.zaproxy.org/docs/
   Semgrep: https://semgrep.dev/docs/
   Trivy: https://aquasecurity.github.io/trivy/
   SonarQube: https://docs.sonarqube.org/
   Snyk: https://docs.snyk.io/

📗 Security Standards
   OWASP ASVS: https://owasp.org/www-project-application-security-verification-standard/
   CWE Top 25: https://cwe.mitre.org/top25/
   NIST SSDF: https://csrc.nist.gov/Projects/ssdf
   PCI DSS: https://www.pcisecuritystandards.org/

📙 Learning Resources
   OWASP Top 10: https://owasp.org/www-project-top-ten/
   PortSwigger Academy: https://portswigger.net/web-security
   SANS Reading Room: https://www.sans.org/reading-room/
   NIST Vulnerability Database: https://nvd.nist.gov/

🔧 Tool Collections
   Awesome Security: https://github.com/sbilly/awesome-security
   Security Tools: https://github.com/topics/security-tools
   DevSecOps Tools: https://github.com/topics/devsecops

📱 Communities
   r/netsec: https://reddit.com/r/netsec
   Security StackExchange: https://security.stackexchange.com/
   OWASP Slack: https://owasp.org/slack/invite
   DevSecOps Community: https://www.devsecops.org/

🎥 YouTube Channels
   OWASP Foundation
   PwnFunction
   IppSec
   The Cyber Mentor
   HackerSploit

📊 Vulnerability Databases
   CVE: https://cve.mitre.org/
   NVD: https://nvd.nist.gov/
   GitHub Advisory: https://github.com/advisories
   Snyk Vuln DB: https://security.snyk.io/

🛠️ Online Scanners
   SSL Labs: https://www.ssllabs.com/ssltest/
   Security Headers: https://securityheaders.com/
   Mozilla Observatory: https://observatory.mozilla.org/
   Qualys FreeScan: https://freescan.qualys.com/

📜 Compliance Resources
   CIS Benchmarks: https://www.cisecurity.org/cis-benchmarks/
   NIST Cybersecurity Framework: https://www.nist.gov/cyberframework
   ISO 27001: https://www.iso.org/isoiec-27001-information-security.html

💬 Podcasts
   Darknet Diaries
   Security Now
   Risky Business
   The CyberWire Daily
```

---

<div align="center">

## 🎯 Quick Reference

</div>

### Scanner Commands Cheat Sheet 📋

```bash
# ═══════════════════════════════════════════
# QUICK REFERENCE COMMANDS
# ═══════════════════════════════════════════

╔════════════════════════════════════════════════════════════╗
║                   SAST / CODE SCANNING                     ║
╚════════════════════════════════════════════════════════════╝

# Semgrep
semgrep --config=auto .                          # Auto-detect rules
semgrep --config=p/security-audit .              # Security audit
semgrep --config=p/owasp-top-ten .              # OWASP Top 10

# SonarQube
sonar-scanner                                    # Scan project
sonar-scanner -Dsonar.projectKey=my-project     # With project key

# ESLint
npx eslint --ext .js,.jsx,.ts,.tsx .            # Scan JS/TS
npx eslint --plugin security .                   # With security plugin

╔════════════════════════════════════════════════════════════╗
║                   SCA / DEPENDENCIES                       ║
╚════════════════════════════════════════════════════════════╝

# npm
npm audit                                        # Check vulnerabilities
npm audit fix                                    # Auto-fix
npm audit --audit-level=high                    # Only high+

# Snyk
snyk test                                        # Test dependencies
snyk monitor                                     # Monitor project
snyk fix                                         # Auto-fix

# OWASP Dependency-Check
dependency-check.sh --project "My App" --scan .  # Full scan

╔════════════════════════════════════════════════════════════╗
║                   CONTAINER SCANNING                       ║
╚════════════════════════════════════════════════════════════╝

# Trivy
trivy image node:18-alpine                       # Scan image
trivy fs .                                       # Scan filesystem
trivy config .                                   # Scan configs

# Grype
grype node:18-alpine                             # Scan image
grype dir:.                                      # Scan directory

# Hadolint
hadolint Dockerfile                              # Lint Dockerfile

╔════════════════════════════════════════════════════════════╗
║                   SECRET SCANNING                          ║
╚════════════════════════════════════════════════════════════╝

# Gitleaks
gitleaks detect                                  # Scan repo
gitleaks protect                                 # Scan uncommitted

# TruffleHog
trufflehog git https://github.com/user/repo     # Scan git repo
trufflehog filesystem /path                      # Scan files

# git-secrets
git secrets --scan                               # Scan changes
git secrets --scan-history                       # Scan history

╔════════════════════════════════════════════════════════════╗
║                   DAST / WEB SCANNING                      ║
╚════════════════════════════════════════════════════════════╝

# OWASP ZAP
zap-baseline.py -t https://example.com          # Baseline scan
zap-full-scan.py -t https://example.com         # Full scan

# Nuclei
nuclei -u https://example.com                    # Basic scan
nuclei -u https://example.com -severity high    # High severity only

# Nikto
nikto -h https://example.com                     # Scan host

╔════════════════════════════════════════════════════════════╗
║                   INFRASTRUCTURE                           ║
╚════════════════════════════════════════════════════════════╝

# Checkov
checkov -d terraform/                            # Scan Terraform
checkov -f k8s-deployment.yaml                  # Scan K8s

# TFSec
tfsec .                                          # Scan current dir
tfsec terraform/                                # Scan specific dir

# Prowler
prowler aws                                      # Scan AWS
prowler aws -f cis_1.5_aws                      # CIS benchmark

╔════════════════════════════════════════════════════════════╗
║                   NETWORK SCANNING                         ║
╚════════════════════════════════════════════════════════════╝

# Nmap
nmap 192.168.1.1                                # Basic scan
nmap -sV -A 192.168.1.1                         # Aggressive scan
nmap --script vuln 192.168.1.1                  # Vulnerability scan

# testssl.sh
./testssl.sh https://example.com                # SSL/TLS test

═══════════════════════════════════════════════════════════
```

---

<div align="center">

## 📝 Summary

</div>

### Key Takeaways 🎯

```bash
╔════════════════════════════════════════════════════════════╗
║                   ESSENTIAL POINTS                         ║
╚════════════════════════════════════════════════════════════╝

1. Shift Left
   • Scan early in development
   • IDE plugins for instant feedback
   • Pre-commit hooks prevent issues
   • Fix bugs before they reach production

2. Defense in Depth
   • SAST + SCA + DAST + Container + IaC
   • No single scanner catches everything
   • Multiple layers of security
   • Different scanners have different strengths

3. Automate Everything
   • CI/CD integration is essential
   • Automatic scans on every commit
   • Auto-fix when possible
   • Scheduled comprehensive scans

4. Prioritize Wisely
   • Focus on critical/high first
   • Consider exploitability & exposure
   • Check for active exploitation
   • Balance security vs velocity

5. Continuous Improvement
   • Track metrics over time
   • Reduce false positives
   • Update scanners regularly
   • Learn from findings

6. Team Empowerment
   • Train developers on security
   • Make scanners easy to use
   • Provide clear remediation guidance
   • Foster security culture

╔════════════════════════════════════════════════════════════╗
║                   MINIMUM VIABLE SECURITY                  ║
╚════════════════════════════════════════════════════════════╝

Every project should have AT MINIMUM:
─────────────────────────────────────────────────────────────
✅ Secret scanning (Gitleaks)
✅ Dependency scanning (npm audit / Snyk)
✅ Basic SAST (Semgrep / ESLint)
✅ Container scanning if using Docker (Trivy)
✅ Pre-commit hooks
✅ CI/CD integration

This provides baseline security with minimal effort!

╔════════════════════════════════════════════════════════════╗
║                   FINAL THOUGHTS                           ║
╚════════════════════════════════════════════════════════════╝

Security scanning is not a silver bullet, but it's essential:
─────────────────────────────────────────────────────────────
• Catches low-hanging fruit
• Reduces manual review burden
• Enforces consistent standards
• Provides audit trail
• Builds security awareness

Remember:
─────────────────────────────────────────────────────────────
🔍 Scan early, scan often
🔧 Fix quickly, track progress
📊 Measure and improve
🎓 Learn from findings
🤝 Security is everyone's responsibility

═══════════════════════════════════════════════════════════
```

---

<div align="center">

**Built with 🔍 by MrDib, for secure software development**

_Remember: "Security is not a product, but a process"_ 🛡️

**Scan Everything!** 🚀

---

### 🔗 Related Guides

- [Web Security](./Web-Security.md)
- [Authentication Tools](./Authentication-Tools.md)
- [Encryption Tools](./Encryption-Tools.md)

</div>
