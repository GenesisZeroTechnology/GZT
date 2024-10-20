# GZT Landing Page
This is a landing page for Genesis Zero Technology

# Genesis Zero Technology - Backend Integration with Brevo

This repository contains the backend integration for email subscription using Brevo (formerly Sendinblue) API. It is configured to automatically handle form submissions and securely use API secrets via GitHub Actions.

## **Setting Up GitHub Actions for Automatic Deployment**

Follow these steps to create the GitHub Actions workflow that will securely use Brevo API keys and handle backend processes automatically.

### Step 1: Create GitHub Actions Workflow

1. **Open your GitHub repository**.
   
2. **Click on "Add file"** (at the top of the file list) and select **"Create new file"**.

3. **Create the directories and YAML file**:
   
   In the "file name" input field, type:


**- This will automatically create both the `.github` directory and the `workflows` subdirectory, along with the `deploy-backend.yml` file.

4. **Add the following YAML content** to the newly created file:

```yaml
name: Deploy Backend

on: [push]

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout code
        uses: actions/checkout@v3

      - name: Set up Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '16'

      - name: Install dependencies
        run: npm install

      - name: Run backend with secrets
        env:
          BREVO_API_KEY: ${{ secrets.BREVO_API_KEY }}
          BREVO_LIST_ID: ${{ secrets.BREVO_LIST_ID }}
        run: |
          npm start
**

BREVO_API_KEY = xxxxxxxxxxxxxxxxxxxxxxxx
BREVO_LIST_ID = 123456

---

### **Explanation of the Sections**:

- **Setting Up GitHub Actions**: Describes how to create the `.github/workflows/deploy-backend.yml` file through the GitHub web interface.
- **Add Brevo Secrets**: Step-by-step guide on how to securely add the Brevo API key and List ID as secrets in GitHub.
- **Why We Did This**: Explanation of the security and automation benefits, ensuring your API keys are kept safe and the deployment process is automatic.

This will make it easy for anyone working with the project to understand how the integration is set up and why certain steps were taken. Let me know if you'd like to adjust or add any additional information!
