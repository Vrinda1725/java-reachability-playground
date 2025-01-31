# Java Reachability Playground

This is an intentionally vulnerable application. It was purposely designed to demonstrate the capabilities of Snyk's Reachable
Vulnerabilities feature and includes both a "Reachable" vulnerability (with a direct data flow to the vulnerable function) and a "Potentially Reachable" vulnerability (where only partial data exists for determining reachability).

## GitHub Actions Integration: Snyk Security Scanning
This repository is integrated with **GitHub Actions** to automatically scan for vulnerabilities in Maven dependencies using Snyk.
Whenever a push is made to the repository, the workflow runs a security check to detect potential risks.

### **GitHub Actions Workflow**

```yaml
name: Example workflow for Maven using Snyk
on: push
jobs:
  security:
    runs-on: ubuntu-latest
    steps:
        # Checks out the repository code
      - name: Checkout Repository
        uses: actions/checkout@master

        # Runs Snyk security scan on Maven dependencies
      - name: Run Snyk to check for vulnerabilities
        uses: snyk/actions/maven@master  
        env:
          [SNYK_TOKEN]: ${{ secrets.[SNYK_TOKEN] }}  # Uses a secret token for Snyk authentication
```
### **Inputs**
- SNYK_TOKEN: [Snyk Website](https://snyk.io)

### **How It Works**
- The workflow runs **automatically on every push** to check for security vulnerabilities in Maven dependencies.
- It **retrieves the repository code** so that Snyk can analyze the dependencies.
- The **Snyk Maven Action** (`snyk/actions/maven@master`) scans the `pom.xml` file for known vulnerabilities.
- The scan results are displayed in **GitHub Actions logs** and can be further analyzed using **Snyk UI**.

## Screenshots

### CLI
![image](https://github.com/user-attachments/assets/9a39fa82-8809-41de-bffe-fdcf19a4dd85)


### Snyk UI
![image](https://github.com/user-attachments/assets/afe91173-93a7-442c-bc1f-64e286f7a0c4)



