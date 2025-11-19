# Security Scanning Quick Reference

## Workflow Summary

| Workflow | Trigger | Purpose | Duration |
|----------|---------|---------|----------|
| CodeQL Analysis | Push, PR, Weekly | SAST scanning | 5-10 min |
| Snyk Security | Push, PR, Weekly | Dependency & code scanning | 3-5 min |
| Dependency Review | Pull Requests | Dependency validation | 1-2 min |

## Expected Scan Results

### High Severity Issues to Watch For
- SQL Injection
- Command Injection
- Cross-Site Scripting (XSS)
- Path Traversal
- Hardcoded Credentials
- Insecure Deserialization

### Dependency Issues
- Known CVEs in dependencies
- Outdated packages with security fixes
- License compliance issues

## Manual Scan Instructions

### Run All Scans Manually
1. Go to **Actions** tab
2. For each workflow:
   - Click workflow name
   - Click **"Run workflow"** dropdown
   - Select branch (usually `main`)
   - Click **"Run workflow"** button
3. Wait for completion
4. Check **Security** tab for results

### Run Snyk Scan Locally (Optional)
```bash
# Install Snyk CLI
npm install -g snyk

# Authenticate
snyk auth

# Run tests
snyk test --all-projects
snyk code test

# Monitor project (sends to Snyk dashboard)
snyk monitor
```

## Troubleshooting

### Workflow Fails to Run
- Check if SNYK_TOKEN secret is set
- Verify repository is public or has GitHub Advanced Security
- Check Actions permissions in Settings → Actions → General

### No Vulnerabilities Found
- Ensure code files are committed
- Check workflow logs for language detection
- Verify autobuild completed successfully

### Too Many Alerts
- Filter by severity (High/Critical only)
- Review in batches by category
- Use Snyk fix suggestions for quick remediation

## DoD Compliance Checklist

- [ ] SBOM generated (use GitHub dependency graph export)
- [ ] SAST execution documented (CodeQL results)
- [ ] Dependency scanning completed (Snyk/Dependabot)
- [ ] Vulnerability severity scored (CVSS available in alerts)
- [ ] Remediation plan documented
- [ ] Scan frequency meets requirements (weekly minimum)

## Report Generation

### Export from GitHub
1. **Security** → **Code scanning**
2. Click **"Download as CSV"** or use API

### Export from Snyk
1. Visit [app.snyk.io](https://app.snyk.io/)
2. Select project
3. Click **"Reports"** → **"Export"**
4. Choose format (PDF, CSV, JSON)

## Integration with Tools

### SBOM Generation
```bash
# Using GitHub CLI
gh api repos/OWNER/REPO/dependency-graph/sbom --jq .sbom > sbom.json
```

### API Access
```bash
# Get code scanning alerts
gh api repos/OWNER/REPO/code-scanning/alerts

# Get Dependabot alerts  
gh api repos/OWNER/REPO/dependabot/alerts
```
