<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Preschool Teacher Self-Assessment</title>
<style>
  body { font-family: Arial; max-width: 800px; margin: auto; padding: 20px; }
  h1, h2 { text-align: center; }
  .area { margin-top: 20px; border-top: 1px solid #ccc; padding-top: 10px; }
  .question { margin-bottom: 10px; }
  select { margin-left: 10px; }
  #result { margin-top: 20px; padding: 10px; border: 1px solid #ccc; background: #f9f9f9; }
</style>
</head>
<body>

<h1>Preschool Teacher Self-Assessment</h1>
<p>Rate each statement from 1 (Strongly Disagree) to 5 (Strongly Agree)</p>

<form id="assessmentForm">

<!-- Area 1: Classroom Routines -->
<div class="area">
<h2>1. Classroom Routines</h2>
<div class="question">1. I have clear daily routines that children understand.</div>
<select name="q1"><option value="1">1</option><option value="2">2</option>
<option value="3">3</option><option value="4">4</option><option value="5">5</option></select>

<div class="question">2. I can maintain routines even when unexpected events occur.</div>
<select name="q2"><option value="1">1</option><option value="2">2</option>
<option value="3">3</option><option value="4">4</option><option value="5">5</option></select>

<div class="question">3. I adjust routines to fit individual children without disrupting the class.</div>
<select name="q3"><option value="1">1</option><option value="2">2</option>
<option value="3">3</option><option value="4">4</option><option value="5">5</option></select>
</div>

<!-- Repeat similar blocks for all 10 areas, 3 questions each (total 30 questions) -->
<!-- For brevity, only Area 1 is shown here. We can add the rest in the final version. -->

<button type="button" onclick="calculatePriorities()">Submit</button>
</form>

<div id="result"></div>

<script>
const areas = [
  {name: "Classroom Routines", qs:[1,2,3]},
  // Add the other 9 areas here with their question numbers
];

function calculatePriorities() {
  const form = document.getElementById('assessmentForm');
  // For simplicity, calculate averages per area
  let areaScores = [];
  for (let area of areas) {
    let sum = 0;
    for (let q of area.qs) {
      sum += parseInt(form['q'+q].value);
    }
    let avg = sum / area.qs.length;
    areaScores.push({name: area.name, avg: avg});
  }
  // Sort ascending → lowest averages = priority areas
  areaScores.sort((a,b) => a.avg - b.avg);
  const priorities = areaScores.slice(0,3);
  document.getElementById('result').innerHTML = "<h3>Suggested Priority Areas:</h3><ul>" + priorities.map(p => "<li>" + p.name + " (average score: " + p.avg.toFixed(2) + ")</li>").join("") + "</ul>";
}
</script>

</body>
</html>
