# Security Scan Template

This template provides comprehensive automated security scanning for open source software validation, compliant with DoD cybersecurity requirements.

## 🔐 Security Scanning Features

- **CodeQL Analysis (SAST)**: Detects code vulnerabilities including SQL injection, XSS, command injection
- **Snyk Security**: Dependency scanning and code analysis
- **Dependency Review**: Validates dependencies in pull requests
- **Secret Scanning**: Detects hardcoded credentials (requires enabling in Settings)
- **Dependabot**: Automated dependency updates

## 📋 DoD Compliance Support

Configured to support:
- DISA Application Security and Development STIG
- DoDI 8500.01 (Cybersecurity)
- DoDI 8510.01 (Risk Management Framework)
- NIST SP 800-53 controls

## 🚀 Quick Start

### 1. Use This Template

1. Click **"Use this template"** button above
2. Name your repository (e.g., `scan-project-name`)
3. Choose **Public** visibility
4. Click **"Create repository"**

### 2. Add Snyk Token

1. Get your Snyk API token from [snyk.io](https://app.snyk.io/account)
2. In your new repository: **Settings** → **Secrets and variables** → **Actions**
3. Click **"New repository secret"**
4. Name: `SNYK_TOKEN`
5. Value: (paste your token)
6. Click **"Add secret"**

### 3. Import Project Code

Choose one of these methods:

**Option A: Fork existing repository**
```bash
# Fork the target repository first on GitHub
# Then add it as a remote
git clone https://github.com/YOUR_USERNAME/YOUR_NEW_REPO.git
cd YOUR_NEW_REPO
git remote add upstream https://github.com/ORIGINAL_OWNER/ORIGINAL_REPO.git
git pull upstream main
git push origin main
```

**Option B: Import code manually**
1. Clone the open source project locally
2. Copy files to your new repository
3. Commit and push

**Option C: Use GitHub's import feature**
1. Go to your new repository
2. Click **"Import code"** (if available)
3. Enter the URL of the repository to scan

### 4. Enable Security Features

1. Go to **Settings** → **Code security and analysis**
2. Enable all features:
   - ✅ Dependency graph
   - ✅ Dependabot alerts
   - ✅ Dependabot security updates
   - ✅ Secret scanning
   - ✅ Code scanning (should auto-enable)

### 5. Customize Workflow (Optional)

Edit `.github/workflows/codeql-analysis.yml`:
- Remove languages not used in your project from the matrix
- Adjust schedule if needed

### 6. Run Scans

**Automatic triggers:**
- Every push to main/master/develop
- Every pull request
- Weekly schedule (Mondays)

**Manual trigger:**
1. Go to **Actions** tab
2. Select a workflow
3. Click **"Run workflow"**

## 📊 View Results

### Code Scanning Alerts
1. **Security** tab → **Code scanning**
2. Review alerts by severity
3. Click on alert for details and remediation

### Dependabot Alerts
1. **Security** tab → **Dependabot**
2. Review vulnerable dependencies
3. Create pull requests to update

### Snyk Dashboard
1. Visit [app.snyk.io](https://app.snyk.io/)
2. View all monitored projects
3. Get detailed reports and fix recommendations

## 🔄 Routine Scanning Process

For multiple projects:

1. Use this template for each project
2. Projects automatically scan on schedule
3. Review **Security** tab weekly
4. Check Snyk dashboard for centralized view
5. Document findings in your compliance reports

## 📝 Generating Reports

Scan results are available in multiple formats:
- GitHub Security tab (web interface)
- SARIF files (downloadable from Actions artifacts)
- Snyk dashboard (PDF/CSV export available)

## 🛠️ Supported Languages

- JavaScript/TypeScript
- Python
- Java
- Go
- C/C++
- C#
- Ruby

## 📚 Additional Resources

- [GitHub Code Scanning Documentation](https://docs.github.com/en/code-security/code-scanning)
- [Snyk Documentation](https://docs.snyk.io/)
- [DISA STIG Requirements](https://public.cyber.mil/stigs/)


## 🚀 Quick Start (Web Browser Only - No Terminal Needed!)

### Method 1: Automatic Setup (Recommended)

1. **Use this template** → Click "Use this template" button above → Create your repository
2. **Go to Actions tab** → Click "Setup Security Scanning"
3. **Click "Run workflow"** dropdown → Click green "Run workflow" button
4. **Wait 30 seconds** → A new issue will be created with setup instructions
5. **Follow the issue instructions** → Add your Snyk token
6. **Done!** Security scanning is now active 🎉

### Method 2: Manual Setup

If you prefer to add workflows manually:

1. Fork/create your repository
2. Click "Add file" → "Create new file"
3. Name: `.github/workflows/codeql-analysis.yml`
4. Copy content from [this file](https://github.com/hbonesctr/security-scan-template/blob/main/.github/workflows/codeql-analysis.yml)
5. Commit the file
6. Repeat for Snyk workflow if desired

---

## 🤝 Support

For issues or questions about this template, open an issue in this repository.

---

**Last Updated:** 2025-11-19
**Version:** 1.0
