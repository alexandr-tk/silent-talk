<a name="readme-top"></a>

<div align="center">
  <img src="frontend/public/logo.svg" alt="Silent Talk Logo" width="120" height="120" />
  
  <h3 align="center">Silent Talk</h3>

  <p align="center">
    Real-Time Sign Language Translation & Accessibility Platform
  </p>

  <p align="center">
    <a href="https://youtu.be/MuX_m5dPpj4?si=ENCBESx-YJvemE78">
      <img src="https://img.shields.io/badge/▶_Watch_Demo_Video-FF0000?style=for-the-badge&logo=youtube&logoColor=white" alt="Watch Demo Video" />
    </a>
  </p>

  <p align="center">
    <img src="https://img.shields.io/badge/Award-Samsung_Solve_for_Tomorrow_Top_30-blue?style=for-the-badge&logo=samsung&logoColor=white" alt="Samsung Award" />
    <br />
 <a href="https://github.com/alexandr-tk/silent-talk/graphs/contributors">
      <img src="https://img.shields.io/github/contributors/alexandr-tk/silent-talk?style=for-the-badge" alt="Contributors" />
    </a>
    <a href="LICENSE">
      <img src="https://img.shields.io/github/license/alexandr-tk/silent-talk?style=for-the-badge" alt="License" />
    </a>
    <a href="https://linkedin.com/in/alexandr-tkachyov">
      <img src="https://img.shields.io/badge/-LinkedIn-black.svg?style=for-the-badge&logo=linkedin&colorB=555" alt="LinkedIn" />
    </a>

  </p>
</div>

<details>
  <summary>Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
      <ul>
        <li><a href="#built-with">Built With</a></li>
      </ul>
    </li>
    <li><a href="#system-architecture">System Architecture</a></li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#disclaimer">Status & Disclaimer</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>

## About The Project

**Silent Talk** is a computer vision accessibility tool designed to bridge the communication gap for the deaf and hard-of-hearing community. By translating American Sign Language (ASL) gestures into text in real-time, it enables seamless two-way communication.

This project was selected as a **Top 30 Semifinalist** (out of 300+ teams) in the **Samsung Solve for Tomorrow 2024** competition.

* **Metric:** Trained on a custom dataset of **~50,000 images**.
* **Performance:** Achieved **>90% accuracy** on validation samples during competition trials.
* **Optimization:** Engineered to run on standard CPU hardware without requiring GPU acceleration.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Built With

* [![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
* [![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactjs.org/)
* [![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)](https://opencv.org/)
* [![MediaPipe](https://img.shields.io/badge/MediaPipe-00BACC?style=for-the-badge&logo=google&logoColor=white)](https://developers.google.com/mediapipe)
* [![Scikit-Learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## System Architecture

The system is designed as a monolithic prototype optimized for the rapid iteration constraints of a hackathon environment.

### 1. Vision Engine (Backend)
Located in `/backend`, the core logic utilizes a custom lightweight pipeline:
* **Hand Tracking:** MediaPipe extracts skeletal landmarks (21 points per hand) in real-time.
* **Gesture Classification:** A trained **Scikit-Learn** classifier maps the vector geometry to ASL alphabets.
* **Speech Synthesis:** Recognized text streams are converted into audio output.

### 2. User Interface (Frontend)
Located in `/frontend`, the client is built with **React**:
* **Real-Time Feedback:** Visualizes the translation stream with low latency.
* **Accessibility:** High-contrast UI designed for diverse user visibility needs.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Getting Started

To run this research prototype locally, ensure you have **Python 3.9+** and **Node.js** installed.

### Prerequisites

* Python 3.9+
* Node.js & npm

### Installation

1. **Clone the repository**
```bash
git clone https://github.com/alexandr-tk/silent-talk.git
```

2. **Setup Backend (Python)**
```bash
cd silent-talk/backend
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
python app.py
```


3. **Setup Frontend (React)**
```bash
cd ../frontend
npm install
npm run dev
```



<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Status & Disclaimer

**Status: Archived (Proof of Concept)**

This codebase represents the **competition snapshot** of Silent Talk submitted for the Samsung Solve for Tomorrow semifinals. It was optimized for **speed of development** and proof-of-concept validation.

* **Code Quality:** Experimental / Prototype Grade.
* **Maintenance:** This repository is archived and is not currently maintained.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## License

Distributed under the MIT License. See [LICENSE](LICENSE) for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Contact

**Alex Tkachyov** - Lead Developer - [LinkedIn](https://linkedin.com/in/alexandr-tkachyov)

Project Link: [https://github.com/alexandr-tk/silent-talk](https://www.google.com/search?q=https://github.com/alexandr-tk/silent-talk)

<p align="right">(<a href="#readme-top">back to top</a>)</p>
