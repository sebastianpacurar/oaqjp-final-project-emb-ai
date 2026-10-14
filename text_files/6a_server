from flask import Flask, render_template, request
from EmotionDetection.emotion_detection import emotion_detector

app = Flask(__name__)


@app.route("/")
def root_path():
    return render_template("index.html")


@app.route("/emotionDetector")
def get_emotion():
    input_text = request.args.get("textToAnalyze")
    emotions = emotion_detector(input_text)
    dominant_emotion = emotions.get("dominant_emotion")
    emotions.pop("dominant_emotion")
    input_formatted = ", ".join(f"'{k}': {v}" for k, v in emotions.items())
    return f"For the given statement, the system response is {input_formatted}. The dominant emotion is {dominant_emotion}."


if __name__ == "__main__":
    app.run(debug=True)
