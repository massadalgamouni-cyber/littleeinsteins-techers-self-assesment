<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Preschool Teacher Self-Assessment</title>
<style>
  body { font-family: Arial; max-width: 600px; margin: auto; padding: 20px; }
  h1 { text-align: center; }
  .question { margin-bottom: 15px; }
  select { margin-left: 10px; }
  #result { margin-top: 20px; padding: 10px; border: 1px solid #ccc; }
</style>
</head>
<body>

<h1>Preschool Teacher Self-Assessment</h1>

<form id="assessmentForm">

<div class="question">1. Clear daily routines
  <select name="q1">
    <option value="1">1</option><option value="2">2</option><option value="3">3</option>
    <option value="4">4</option><option value="5">5</option>
  </select>
</div>

<div class="question">2. Positive behavior strategies
  <select name="q2"><option value="1">1</option><option value="2">2</option>
  <option value="3">3</option><option value="4">4</option><option value="5">5</option></select>
</div>

<div class="question">3. Organized and safe environment
  <select name="q3"><option value="1">1</option><option value="2">2</option>
  <option value="3">3</option><option value="4">4</option><option value="5">5</option></select>
</div>

<div class="question">4. Lesson planning & objectives
  <select name="q4"><option value="1">1</option><option value="2">2</option>
  <option value="3">3</option><option value="4">4</option><option value="5">5</option></select>
</div>

<div class="question">5. Adapt activities for all levels
  <select name="q5"><option value="1">1</option><option value="2">2</option>
  <option value="3">3</option><option value="4">4</option><option value="5">5</option></select>
</div>

<div class="question">6. Variety in teaching methods
  <select name="q6"><option value="1">1</option><option value="2">2</option>
  <option value="3">3</option><option value="4">4</option><option value="5">5</option></select>
</div>

<div class="question">7. Emotional & social support
  <select name="q7"><option value="1">1</option><option value="2">2</option>
  <option value="3">3</option><option value="4">4</option><option value="5">5</option></select>
</div>

<div class="question">8. Communication with children
  <select name="q8"><option value="1">1</option><option value="2">2</option>
  <option value="3">3</option><option value="4">4</option><option value="5">5</option></select>
</div>

<div class="question">9. Reflection on practice
  <select name="q9"><option value="1">1</option><option value="2">2</option>
  <option value="3">3</option><option value="4">4</option><option value="5">5</option></select>
</div>

<div class="question">10. Parent communication
  <select name="q10"><option value="1">1</option><option value="2">2</option>
  <option value="3">3</option><option value="4">4</option><option value="5">5</option></select>
</div>

<button type="button" onclick="calculatePriorities()">Submit</button>
</form>

<div id="result"></div>

<script>
const questions = [
  "Clear daily routines",
  "Positive behavior strategies",
  "Organized and safe environment",
  "Lesson planning & objectives",
  "Adapt activities for all levels",
  "Variety in teaching methods",
  "Emotional & social support",
  "Communication with children",
  "Reflection on practice",
  "Parent communication"
];

function calculatePriorities() {
  const form = document.getElementById('assessmentForm');
  let scores = [];
  for (let i = 1; i <= 10; i++) {
    scores.push({ q: questions[i-1], score: parseInt(form['q'+i].value) });
  }
  // Sort ascending to find lowest 3 scores
  scores.sort((a,b) => a.score - b.score);
  const priorities = scores.slice(0,3).map(s => s.q);
  document.getElementById('result').innerHTML = "<h3>Suggested Priority Areas:</h3><ul>" + priorities.map(p => "<li>" + p + "</li>").join("") + "</ul>";
}
</script>

</body>
</html>
