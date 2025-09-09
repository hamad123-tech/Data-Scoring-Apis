# Data-Scoring-Apis
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route("/predict", methods=["POST"])
def predict():
    data = request.get_json()

    income = data.get("income", 0)
    debt = data.get("debt", 0)
    history = data.get("history", 0)

    # Simple scoring logic for demo
    score = (income - debt) + history

    if score > 5000:
        result = "Creditworthy"
    else:
        result = "Not Creditworthy"

    return jsonify({"result": result})

if __name__ == "__main__":
    app.run(debug=True)
