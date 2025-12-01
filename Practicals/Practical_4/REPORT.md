# Practical 4: SAST Integration with Snyk in GitHub Actions

This practical demonstrates automating security vulnerability scanning by integrating Snyk SAST into GitHub Actions CI/CD pipelines.

---

### Objective

Implement automated Static Application Security Testing (SAST) using Snyk in GitHub Actions to detect dependency and code vulnerabilities early in the CI/CD pipeline.

---

### Project Overview

- **Application type:** Spring Boot REST API (sample endpoints and test data)
- **Primary goal:** Add automated Snyk scans (dependencies, code, container) and upload SARIF results to GitHub Security
- **Key tools:** Snyk, GitHub Actions, SARIF upload (`github/codeql-action/upload-sarif`), optional: SonarCloud, OWASP ZAP

---

### Implementation

1. Created a Snyk account and generated an API token (`SNYK_TOKEN`) stored as a GitHub Actions secret.
2. Added a `security` job to the main `.github/workflows/maven.yml` to run a Snyk scan after build/tests.
3. Configured Snyk to produce SARIF output and uploaded it with `upload-sarif` so findings appear in the GitHub Security tab.
4. Added an `enhanced-security.yml` workflow with a matrix for `dependencies` and `code` scans, change-detection to avoid unnecessary scans, and a scheduled weekly scan.
5. Added a separate job for Docker image scanning using `snyk/actions/docker` when container artifacts exist.

Example Snyk step (simplified):

```yaml
- name: Run Snyk to check for vulnerabilities
  uses: snyk/actions/maven@master
  env:
    SNYK_TOKEN: ${{ secrets.SNYK_TOKEN }}
  with:
    args: --severity-threshold=high --sarif-file-output=snyk.sarif
```

---

### Testing & Validation

- Verified Snyk runs on push and pull request triggers.
- Confirmed SARIF file uploads create code scanning alerts in the GitHub Security tab.
- Tested change-detection by modifying only `pom.xml` (dependency scan) and `src/**` (code scan).
- Tested container scan by building the Docker image in CI and invoking `snyk/actions/docker`.

---

### Evidence of Results

- `images/sync_git_flow.png` — GitHub Actions workflow run showing the Snyk security job status and timing.
- `images/synk_dashboard.png` — Snyk dashboard overview showing vulnerabilities by severity and project health.
- `images/sync_securityscan.png` — Snyk detailed scan results listing CVEs, severity and suggested fixes.
- `images/syc_dependences.png` — Dependency tree visualization highlighting direct and transitive vulnerable packages.
- `images/sonarcube_dashboard.png` — SonarCloud/SonarQube dashboard summary with code quality and security hotspots.
- `images/sonarcube_branchflow.png` — Branch analysis flow in SonarCloud showing per-branch scan results.
- `images/sonarcube_githubflow.png` — Integration flow between GitHub Actions and SonarCloud for code analysis.
- `images/zap_sacnningreport.png` — OWASP ZAP dynamic scan report showing runtime vulnerabilities detected.
- `images/zapsacn_gitflow.png` — OWASP ZAP GitHub Actions workflow run demonstrating DAST execution in CI.


![Workflow](images/sync_git_flow.png)
*GitHub Actions workflow run showing the Snyk security job status and timing.*


![Snyk dashboard](images/synk_dashboard.png)
*Snyk dashboard overview showing vulnerabilities by severity and project health.*


![Snyk scan results](images/sync_securityscan.png)
*Snyk detailed scan results listing CVEs, severity and suggested fixes.*


![Dependencies](images/syc_dependences.png)
*Dependency tree visualization highlighting direct and transitive vulnerable packages.*


![Sonar dashboard](images/sonarcube_dashboard.png)
*SonarCloud / SonarQube dashboard summary showing code quality and security hotspots.*


![Sonar branch flow](images/sonarcube_branchflow.png)
*Branch-level analysis flow and statuses in SonarCloud.*

![Sonar GitHub flow](images/sonarcube_githubflow.png)
*Integration flow between GitHub Actions and SonarCloud for automated code analysis.*

![ZAP report](images/zap_sacnningreport.png)
*OWASP ZAP dynamic scan report with runtime vulnerability findings.*

![ZAP workflow](images/zapsacn_gitflow.png)
*OWASP ZAP GitHub Actions workflow run demonstrating DAST in CI.*

---

### Challenges Faced

- Getting SARIF output format and upload step working reliably — fixed by adding `--sarif-file-output` and `if: always()` on the upload step.
- CI jobs failing due to high-severity findings — mitigated by `continue-on-error` and choosing an appropriate severity threshold for blocking behavior.
- Long workflow times with multiple scans — mitigated with change-detection and matrix parallelism.

---

### Lessons Learned

- Security should be integrated into CI/CD early (shift-left).
- SARIF integration provides a developer-friendly way to view security findings inside GitHub.
- Use change-detection to speed up scans and reduce CI costs.

---

### Conclusion

Practical 4 demonstrates how to integrate Snyk SAST into GitHub Actions to provide automated dependency and code scanning, surface findings in GitHub Security via SARIF, and configure workflows to be efficient and developer-friendly.

---

### Repository

https://github.com/Kinleyjigs/AS2025_SWE302_02230313_practical4.git

