# 🚀 AWS CI/CD Pipeline with Live Monitoring Dashboard

![CI/CD Pipeline](https://github.com/jenishkhadka/aws-cicd-monitor/actions/workflows/deploy.yml/badge.svg)

A production-style DevOps project demonstrating the full software delivery lifecycle — every `git push` automatically tests, deploys, and monitors a live Flask application on AWS.

**[🔴 Live Dashboard](https://jenishkhadka.github.io/aws-cicd-monitor)**

---

## 🏗️ Architecture

Developer → GitHub → GitHub Actions → AWS EC2
↓
Run Tests
↓
Deploy App
↓
Update Status Dashboard
↓
CloudWatch → SNS → Email Alert

---

## ⚙️ Tech Stack

| Layer | Tool |
|---|---|
| App | Python Flask |
| CI/CD | GitHub Actions |
| Cloud | AWS EC2 (t3.micro) |
| Monitoring | AWS CloudWatch |
| Alerts | AWS SNS |
| Dashboard | GitHub Pages |

---

## 🔄 Pipeline Flow

1. **Push code** to `main` branch
2. **GitHub Actions** spins up a fresh Ubuntu runner
3. **Tests run** via pytest — pipeline stops if they fail
4. **Code deploys** to AWS EC2 via SSH
5. **Systemd restarts** the Flask app automatically
6. **Status checked** and written to `status.json`
7. **Dashboard updates** at [jenishkhadka.github.io/aws-cicd-monitor](https://jenishkhadka.github.io/aws-cicd-monitor)

---

## 📊 Monitoring

- **CloudWatch** watches CPU utilization 24/7
- **SNS** sends an email alert if CPU exceeds 80%
- **Live dashboard** shows server health, response time, and check history

---

## 🚀 How to Run Locally

```bash
git clone https://github.com/jenishkhadka/aws-cicd-monitor
cd aws-cicd-monitor
pip install -r requirements.txt
python app.py
```

Visit `http://localhost:5000`

---

## 🧪 Run Tests

```bash
python -m pytest test_app.py -v
```

---

## 📁 Project Structure
aws-cicd-monitor/
├── .github/
│   └── workflows/
│       └── deploy.yml    # CI/CD pipeline
├── app.py                # Flask application
├── test_app.py           # Pytest tests
├── requirements.txt      # Dependencies
├── index.html            # Live status dashboard
└── status.json           # Auto-updated server status