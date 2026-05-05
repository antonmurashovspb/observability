<div id="survey-container">
  <h2>📋 Course Feedback Survey</h2>

  <form id="survey-form">

    <!-- Q1 -->
    <div class="question">
      <p>1. How would you rate the overall quality of the presentation?</p>
      <label><input type="radio" name="q1" value="1"> 1 - Poor</label><br>
      <label><input type="radio" name="q1" value="2"> 2</label><br>
      <label><input type="radio" name="q1" value="3"> 3</label><br>
      <label><input type="radio" name="q1" value="4"> 4</label><br>
      <label><input type="radio" name="q1" value="5"> 5 - Excellent</label>
    </div>

    <!-- Q2 -->
    <div class="question">
      <p>2. How clear were the explanations?</p>
      <label><input type="radio" name="q2" value="1"> 1 - Not clear</label><br>
      <label><input type="radio" name="q2" value="2"> 2</label><br>
      <label><input type="radio" name="q2" value="3"> 3</label><br>
      <label><input type="radio" name="q2" value="4"> 4</label><br>
      <label><input type="radio" name="q2" value="5"> 5 - Very clear</label>
    </div>

    <!-- Q3 -->
    <div class="question">
      <p>3. Was the level of detail appropriate?</p>
      <label><input type="radio" name="q3" value="too_basic"> Too basic</label><br>
      <label><input type="radio" name="q3" value="just_right"> Just right</label><br>
      <label><input type="radio" name="q3" value="too_advanced"> Too advanced</label>
    </div>

    <!-- Q4 -->
    <div class="question">
      <p>4. Would you recommend this course to others?</p>
      <label><input type="radio" name="q4" value="yes"> Yes</label><br>
      <label><input type="radio" name="q4" value="maybe"> Maybe</label><br>
      <label><input type="radio" name="q4" value="no"> No</label>
    </div>

    <!-- Q5 -->
    <div class="question">
      <p>5. Which topics would you like to explore further?</p>
      <label><input type="checkbox" name="q5" value="tracing"> Distributed tracing deep dive (OpenTelemetry, real request flow)</label><br>
      <label><input type="checkbox" name="q5" value="demo"> Building a full observability stack in .NET (hands-on demo)</label><br>
      <label><input type="checkbox" name="q5" value="analysis"> Performance debugging & bottleneck analysis (real scenarios)</label><br>
      <label><input type="checkbox" name="q5" value="microservices"> Observability in microservices (architecture & best practices)</label><br>
      <label>Something else:</label>
      <textarea name="q5" rows="3" style="width:100%;"></textarea>
    </div>

    <!-- Q6 -->
    <div class="question">
      <p>6. What did you like the most?</p>
      <textarea name="q6" rows="3" style="width:100%;"></textarea>
    </div>

    <!-- Q7 -->
    <div class="question">
      <p>7. What could be improved?</p>
      <textarea name="q7" rows="3" style="width:100%;"></textarea>
    </div>

    <button type="button" onclick="submitSurvey()">Submit Feedback</button>
    <button type="button" onclick="resetSurvey()">Reset</button>

  </form>

  <div id="survey-result" style="margin-top:20px; font-weight:bold;"></div>
</div>

<style>
  #survey-container {
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

  textarea {
    margin-top: 5px;
    padding: 6px;
  }

  button {
    margin-top: 10px;
    margin-right: 10px;
    padding: 8px 16px;
    cursor: pointer;
  }
</style>

<script>
  function submitSurvey() {
    const form = document.getElementById("survey-form");
    const result = document.getElementById("survey-result");

    const data = {
      q1: form.q1.value,
      q2: form.q2.value,
      q3: form.q3.value,
      q4: form.q4.value,
      q5: form.q5.value,
      q6: form.q6.value,
      q7: form.q7.value
    };

    // Basic validation
    if (!data.q1 || !data.q2 || !data.q3 || !data.q4 || !data.q5) {
      result.innerHTML = "⚠️ Please answer all required questions.";
      return;
    }

    console.log("Survey results:", data);

    result.innerHTML = "✅ Thank you for your feedback!";

    // Optional: disable form after submit
    Array.from(form.elements).forEach(el => el.disabled = true);
  }

  function resetSurvey() {
    const form = document.getElementById("survey-form");
    const result = document.getElementById("survey-result");

    form.reset();
    result.innerHTML = "";

    Array.from(form.elements).forEach(el => el.disabled = false);
  }
</script>