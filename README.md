<a name="readme-top"></a>

<div align="center">
  <img src="frontend/public/logo.svg" alt="Silent Talk Logo" width="120" height="120" />
  
  <h3 align="center">Silent Talk</h3>

  <p align="center">
    ASL Fingerspelling Recognition Prototype
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
    <li><a href="#status--limitations">Status & Limitations</a></li>
    <li><a href="#license">License</a></li>
    <li><a href="#contact">Contact</a></li>
  </ol>
</details>

## About The Project

**Silent Talk** is a webcam prototype that classifies ASL fingerspelled letters and displays the accumulated text. It recognizes hand poses from individual frames; it does not translate continuous sign language or provide two-way interpretation.

This project was selected as a **Top 30 Semifinalist** (out of 300+ teams) in the **Samsung Solve for Tomorrow 2024** competition.

* **Reported training data:** A custom dataset of **~50,000 images**.
* **Reported competition result:** **>90% accuracy** on validation samples during competition trials. Training scripts, the validation split, and evaluation results are not included here, so this figure cannot be reproduced from the repository alone.
* **Execution:** Hand tracking and letter classification run locally without requiring a GPU. Text spacing uses an external OpenAI API call.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

### Built With

* [![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://www.python.org/)
* [![React](https://img.shields.io/badge/React-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)](https://reactjs.org/)
* [![OpenCV](https://img.shields.io/badge/OpenCV-5C3EE8?style=for-the-badge&logo=opencv&logoColor=white)](https://opencv.org/)
* [![MediaPipe](https://img.shields.io/badge/MediaPipe-00BACC?style=for-the-badge&logo=google&logoColor=white)](https://developers.google.com/mediapipe)
* [![Scikit-Learn](https://img.shields.io/badge/scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)](https://scikit-learn.org/)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## System Architecture

The prototype has a Flask backend and a React frontend.

### 1. Vision Engine (Backend)
Located in `backend/`, the recognition flow is:
* **Hand Tracking:** MediaPipe extracts skeletal landmarks (21 points per hand) in real-time.
* **Letter classification:** A saved classifier predicts one of 26 letter labels from hand landmarks. A prediction must remain stable for 1.5 seconds before it is appended.
* **Text spacing:** The backend sends accumulated text to `gpt-4o-mini` with instructions to insert spaces. There is no speech-synthesis implementation in this snapshot.

### 2. User Interface (Frontend)
Located in `/frontend`, the client is built with **React**:
* **Display:** Shows the backend camera feed and polls recognized text once per second.
* **Controls:** Includes camera-display and text-reset controls, plus a light/dark theme.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Getting Started

The original setup targets **Python 3.9+** and **Node.js**. The backend needs access to the host computer’s camera, the bundled `backend/model.p`, and an `OPENAI_API_KEY` environment variable. Starting it without an API key fails when the OpenAI client is created.

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
export OPENAI_API_KEY="<your-api-key>"  # backend environment only
python app.py
```


3. **Setup Frontend (React), in a second terminal from the repository root**
```bash
cd frontend
npm install
npm run dev
```



<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Status & Limitations

**Status: Competition proof of concept**

This codebase represents the **competition snapshot** of Silent Talk submitted for the Samsung Solve for Tomorrow semifinals.

* **Code Quality:** Experimental / Prototype Grade.
* **Maintenance:** This competition snapshot is not currently maintained.
* **Integration limits:** The settings client calls `/set_stable_time`, but the Flask backend does not implement that route. Some service helpers use relative URLs while Vite has no API proxy. The camera and main text display use `localhost:5000` directly.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## License

Distributed under the MIT License. See [LICENSE](LICENSE) for more information.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

## Contact

**Alex Tkachyov** - Lead Developer - [LinkedIn](https://linkedin.com/in/alexandr-tkachyov)

Project Link: [Silent Talk on GitHub](https://github.com/alexandr-tk/silent-talk)

<p align="right">(<a href="#readme-top">back to top</a>)</p>
