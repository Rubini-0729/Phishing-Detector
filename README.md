[README.md](https://github.com/user-attachments/files/27630913/README.md)
# 🛡️ AI-Powered Phishing URL Detector

A machine learning-based web application that detects phishing URLs in real time using feature extraction and a Random Forest classifier. Built as a final year project combining **Artificial Intelligence** and **Cybersecurity**.

---

## 📌 Table of Contents

- [About the Project](#about-the-project)
- [How It Works](#how-it-works)
- [Features](#features)
- [Tech Stack](#tech-stack)
- [Dataset](#dataset)
- [Model Performance](#model-performance)
- [Project Structure](#project-structure)
- [Getting Started](#getting-started)
- [Usage](#usage)
- [Screenshots](#screenshots)
- [Future Improvements](#future-improvements)
- [License](#license)

---

## 📖 About the Project

Phishing attacks are one of the most common cybersecurity threats, where attackers create fake websites to steal user credentials and sensitive information. This project uses **Machine Learning** to automatically detect whether a given URL is legitimate or a phishing attempt — without relying on blacklists or manual rules.

> **"Instead of memorizing bad URLs, the model learns the patterns that make a URL suspicious."**

---

## ⚙️ How It Works

```
User enters URL
      ↓
Extract 15+ features from the URL
      ↓
Feed features into trained Random Forest model
      ↓
Model predicts: PHISHING or SAFE
      ↓
Display result with confidence score + reasons
```

---

## ✨ Features

- **Real-time URL analysis** — instant prediction on any URL
- **15+ extracted features** — length, HTTPS, suspicious keywords, TLD, IP check, and more
- **Explainable results** — shows which features triggered the detection
- **Confidence score** — percentage confidence in the prediction
- **Web dashboard** — clean React frontend with visual feedback
- **REST API** — Flask backend for easy integration

---

## 🛠️ Tech Stack

| Layer | Technology |
|-------|-----------|
| Frontend | React.js, CSS |
| Backend | Python, Flask |
| Machine Learning | Scikit-learn (Random Forest) |
| Data Processing | Pandas, NumPy |
| Visualization | Matplotlib, Seaborn |
| Notebook | Google Colab |

---

## 📊 Dataset

| Source | Type | Count |
|--------|------|-------|
| [PhishTank](https://www.phishtank.com/) | Phishing URLs | ~5,000 |
| [Alexa Top 1M](https://www.alexa.com/) | Legitimate URLs | ~5,000 |

**Total:** ~10,000 labeled URLs (balanced dataset)

---

## 🧠 Features Extracted

| Feature | Description |
|---------|-------------|
| `url_length` | Total length of the URL |
| `has_https` | Whether HTTPS is used (1 = yes, 0 = no) |
| `has_at_symbol` | Presence of `@` in URL |
| `dot_count` | Number of dots in the URL |
| `suspicious_word_count` | Count of words like "login", "verify", "secure" |
| `has_ip_address` | Whether URL contains a raw IP address |
| `suspicious_tld` | Suspicious top-level domain (`.xyz`, `.tk`, `.ml`) |
| `has_brand_name` | Presence of known brand names (paypal, amazon, etc.) |
| `url_depth` | Number of path segments |
| `is_shortened` | Whether URL is a shortening service (bit.ly, etc.) |
| `digit_count` | Number of digits in the URL |
| `special_chars` | Count of special characters (`-`, `_`, `=`) |
| `domain_length` | Length of the domain part |
| `has_double_slash` | Presence of `//` after protocol |
| `has_dash_in_domain` | Presence of `-` in domain name |

---

## 📈 Model Performance

| Metric | Score |
|--------|-------|
| Accuracy | ~95% |
| Precision | ~94% |
| Recall | ~96% |
| F1 Score | ~95% |

**Best Model:** Random Forest (100 estimators)

> Models compared: Logistic Regression, Random Forest, Gradient Boosting

---

## 📁 Project Structure

```
phishing-detector/
│
├── backend/
│   ├── app.py                  # Flask API server
│   ├── features.py             # Feature extraction logic
│   ├── train_model.py          # Model training script
│   └── phishing_model.pkl      # Saved trained model
│
├── frontend/
│   ├── src/
│   │   ├── App.jsx             # Main React component
│   │   ├── App.css             # Styling
│   │   └── index.js
│   └── package.json
│
├── dataset/
│   └── phishing_data.csv       # Training dataset
│
├── notebook/
│   └── phishing_detector.ipynb # Google Colab notebook
│
├── requirements.txt            # Python dependencies
└── README.md
```

---

## 🚀 Getting Started

### Prerequisites

- Python 3.8+
- Node.js 16+
- pip

### Installation

**1. Clone the repository**

```bash
git clone https://github.com/yourusername/phishing-detector.git
cd phishing-detector
```

**2. Install Python dependencies**

```bash
pip install -r requirements.txt
```

**3. Train the model**

```bash
cd backend
python train_model.py
```

**4. Start the Flask backend**

```bash
python app.py
```

**5. Start the React frontend**

```bash
cd frontend
npm install
npm start
```

**6. Open in browser**

```
http://localhost:3000
```

### Google Colab (Quickstart)

Open the notebook directly in Google Colab:

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/yourusername/phishing-detector/blob/main/notebook/phishing_detector.ipynb)

---

## 💻 Usage

### Via Web UI

1. Open the web app in your browser
2. Paste any URL in the input field
3. Click **Check URL**
4. View the prediction, confidence score, and feature breakdown

### Via API

```bash
curl -X POST http://localhost:5000/predict \
  -H "Content-Type: application/json" \
  -d '{"url": "http://paypa1-secure-login.xyz/verify"}'
```

**Response:**

```json
{
  "url": "http://paypa1-secure-login.xyz/verify",
  "result": "PHISHING",
  "confidence": 97.4,
  "features": {
    "url_length": 38,
    "has_https": 0,
    "suspicious_tld": 1,
    "suspicious_word_count": 2,
    "has_brand_name": 1
  }
}
```

---

## 🔮 Future Improvements

- [ ] Add email content analysis (not just URLs)
- [ ] Browser extension (Chrome/Firefox)
- [ ] Real-time PhishTank API integration
- [ ] Deep Learning model (LSTM/BERT) for better accuracy
- [ ] Multi-language support
- [ ] Mobile app (React Native)

---

## 📄 License

This project is licensed under the MIT License — see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgements

- [PhishTank](https://www.phishtank.com/) for the phishing URL dataset
- [Scikit-learn](https://scikit-learn.org/) for machine learning tools
- [UCI ML Repository](https://archive.ics.uci.edu/) for reference datasets

---

> ⭐ If you found this project helpful, please give it a star!
