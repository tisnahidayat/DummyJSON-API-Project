## 🧪 API Test Automation with Postman CLI + GitHub Actions
This repository automates API testing using Postman CLI, executed via GitHub Actions on every push to the repository.

### 🚀 Key Features
- Uses Postman CLI to run API test collections
- Authenticates using an API key stored in GitHub Secrets
- Automatically logs bugs to bug_log.txt when tests fail
- Uploads the bug log as a build artifact

### 🧱 Repository Structure
```bash
.github/workflows/
└── postman-ci.yml         # GitHub Actions workflow file
```
### ⚙️ CI/CD Workflow
Triggered on every push. The steps include:
Checkout the code
1. Install Postman CLI on a Windows runner
2. Log in to Postman CLI using POSTMAN_API_KEY
3. Run the collection with ID:
26429971-040c7827-1f9e-49b2-ab36-6e8367565ad6
4. On test failure, append bug info to bug_log.txt
5. Upload the log file as an artifact

### 🔐 API Key Setup
To add your Postman API key to GitHub:
1. Go to your repo → Settings → Secrets and variables → Actions
2. Click New repository secret
3. Name: POSTMAN_API_KEY
4. Value: (your actual Postman API key)

### ✅ Running Tests Manually (Optional)
You can also run the tests locally using:
```bash
postman login --with-api-key <YOUR_API_KEY>
postman collection run "26429971-040c7827-1f9e-49b2-ab36-6e8367565ad6"
```
### 📦 Artifact Output
If any test fails, the results are written to bug_log.txt and uploaded as an artifact in GitHub Actions. You can view and download it from the Actions UI.

### 📌 Additional Notes
- Use the Postman web app to get your Collection ID
- Bug logging is currently handled manually using echo. This can be improved by parsing test output for better error reporting.
