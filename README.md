**Emotion Detector** — AI-Based Web Application

## Description
This project is an AI-based web application that detects the emotions expressed
in a piece of text using the **Watson NLP EmotionPredict** service. It extends
basic sentiment analysis by extracting finer emotions such as **joy, sadness,
anger, fear, and disgust**, and identifies the **dominant emotion**.

The application is deployed as a **Flask** web app and exposes:
- `GET /` — HTML interface (Bootstrap)
- `GET /emotionDetector?textToAnalyze=<text>` — JSON-to-text API

## Project Structure
final_project/
├── EmotionDetection/
│ ├── init.py
│ └── emotion_detection.py
├── static/
│ └── mywebscript.js
├── templates/
│ └── index.html
├── emotion_detection.py
├── server.py
├── test_emotion_detection.py
├── README.md
└── LICENSE

text

## Installation
```bash
python3 -m pip install requests flask pylint
Usage
1. Test the module directly
bash
python3 -c "from emotion_detection import emotion_detector; print(emotion_detector('I am happy'))"
2. Test the package
bash
python3 -c "from EmotionDetection import emotion_detector; print(emotion_detector('I am happy'))"
3. Run unit tests
bash
python3 -m unittest test_emotion_detection.py
4. Run the Flask web app
bash
python3 server.py
Then open http://localhost:5000/ in a browser.

5. Static code analysis
bash
pylint server.py
pylint emotion_detection.py
pylint test_emotion_detection.py
All files should score 10.00/10.

API Response Example
For textToAnalyze=I am happy:

text
For the given statement, the system response is 'anger': 0.0043079085,
'disgust': 0.00041127237, 'fear': 0.0037504788, 'joy': 0.9918804
and 'sadness': 0.014091322. The dominant emotion is joy.
For an empty input:

text
Invalid text! Please try again!
Error Handling
If the input text is empty or None, emotion_detector() returns a dict
with all scores set to None and dominant_emotion: None.

If the Watson API returns HTTP 400, the same None dict is returned.

server.py checks dominant_emotion is None and returns
"Invalid text! Please try again!" instead of a 500 error.

Tests
5 unit tests cover each emotion:

joy, anger, disgust, sadness, fear