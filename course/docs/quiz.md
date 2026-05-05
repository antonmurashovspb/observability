<div id="quiz-container">
  <h2>🧪 Observability Quiz</h2>

  <form id="quiz-form">

    <!-- Question 1 -->
    <div class="question">
      <p>1. What is the main purpose of logging?</p>
      <label data-value="a"><input type="radio" name="q1" value="a"> Show system health over time</label><br>
      <label data-value="b"><input type="radio" name="q1" value="b"> Record discrete events</label><br>
      <label data-value="c"><input type="radio" name="q1" value="c"> Track request flow</label>
      <div class="explanation"></div>
    </div>

    <!-- Question 2 -->
    <div class="question">
      <p>2. What do metrics primarily help with?</p>
      <label data-value="a"><input type="radio" name="q2" value="a"> Understanding code structure</label><br>
      <label data-value="b"><input type="radio" name="q2" value="b"> Debugging logs</label><br>
      <label data-value="c"><input type="radio" name="q2" value="c"> Monitoring system health</label>
      <div class="explanation"></div>
    </div>

    <!-- Question 3 -->
    <div class="question">
      <p>3. What is the key benefit of distributed tracing?</p>
      <label data-value="a"><input type="radio" name="q3" value="a"> Shows where time is spent</label><br>
      <label data-value="b"><input type="radio" name="q3" value="b"> Reduces CPU usage</label><br>
      <label data-value="c"><input type="radio" name="q3" value="c"> Stores logs</label>
      <div class="explanation"></div>
    </div>

    <!-- Question 4 -->
    <div class="question">
      <p>4. What is a common mistake in observability?</p>
      <label data-value="a"><input type="radio" name="q4" value="a"> Using structured logging</label><br>
      <label data-value="b"><input type="radio" name="q4" value="b"> Logging everything</label><br>
      <label data-value="c"><input type="radio" name="q4" value="c"> Using metrics</label>
      <div class="explanation"></div>
    </div>

    <!-- Question 5 -->
    <div class="question">
      <p>5. What connects logs, metrics, and traces?</p>
      <label data-value="a"><input type="radio" name="q5" value="a"> Correlation/Trace ID</label><br>
      <label data-value="b"><input type="radio" name="q5" value="b"> CPU usage</label><br>
      <label data-value="c"><input type="radio" name="q5" value="c"> Thread pool</label>
      <div class="explanation"></div>
    </div>

    <button type="button" onclick="submitQuiz()">Submit</button>
    <button type="button" onclick="resetQuiz()">Try Again</button>

  </form>

  <div id="result" style="margin-top:20px; font-weight:bold;"></div>
</div>

<style>
  #quiz-container {
    border: 1px solid #ddd;
    padding: 20px;
    border-radius: 10px;
    margin-top: 20px;
  }

  .question {
    margin-bottom: 15px;
    padding: 10px;
    border-radius: 6px;
  }

  .correct {
    background-color: #d4edda;
  }

  .incorrect {
    background-color: #f8d7da;
  }

  .correct-option {
    font-weight: bold;
    text-decoration: underline;
  }

  .explanation {
    margin-top: 8px;
    font-size: 0.9em;
    color: #333;
  }

  button {
    margin-top: 10px;
    margin-right: 10px;
    padding: 8px 16px;
    cursor: pointer;
  }
</style>

<script>
  function submitQuiz() {
    const answers = {
      q1: "b",
      q2: "c",
      q3: "a",
      q4: "b",
      q5: "a"
    };

    const explanations = {
      q1: "Logging records discrete events that happened in the system. It answers: 'What happened?'",
      q2: "Metrics track system health over time (latency, errors, throughput). They answer: 'Is the system healthy?'",
      q3: "Tracing shows the full path of a request and where time is spent. It answers: 'Where is the bottleneck?'",
      q4: "Logging everything creates noise and hides useful signals—this is a common anti-pattern.",
      q5: "Correlation/Trace IDs connect logs, metrics, and traces into a single request flow."
    };

    let score = 0;

    for (let q in answers) {
      const questionDiv = document.querySelector(`input[name="${q}"]`).closest(".question");

      // Reset state
      questionDiv.classList.remove("correct", "incorrect");

      const explanationDiv = questionDiv.querySelector(".explanation");
      explanationDiv.innerHTML = explanations[q];

      const selected = document.querySelector(`input[name="${q}"]:checked`);

      // Highlight correct option
      questionDiv.querySelectorAll("label").forEach(label => {
        label.classList.remove("correct-option");
        if (label.dataset.value === answers[q]) {
          label.classList.add("correct-option");
        }
      });

      if (selected && selected.value === answers[q]) {
        score++;
        questionDiv.classList.add("correct");
      } else {
        questionDiv.classList.add("incorrect");
      }
    }

    const result = document.getElementById("result");
    result.innerHTML = `You scored ${score}/5`;

    if (score === 5) {
      result.innerHTML += " 🎉 Excellent!";
    } else if (score >= 3) {
      result.innerHTML += " 👍 Good job!";
    } else {
      result.innerHTML += " 📘 Consider reviewing the material.";
    }
  }

  function resetQuiz() {
    document.getElementById("quiz-form").reset();
    document.getElementById("result").innerHTML = "";

    document.querySelectorAll(".question").forEach(q => {
      q.classList.remove("correct", "incorrect");
      q.querySelector(".explanation").innerHTML = "";

      q.querySelectorAll("label").forEach(label => {
        label.classList.remove("correct-option");
      });
    });
  }
</script>