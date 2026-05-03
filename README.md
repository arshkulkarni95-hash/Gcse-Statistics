<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>GCSE Statistics Mastery - Grade 9</title>
<style>
* {margin:0;padding:0;box-sizing:border-box}
body {font-family:-apple-system,BlinkMacSystemFont,'Segoe UI',sans-serif;background:linear-gradient(135deg,#667eea 0%,#764ba2 100%);min-height:100vh;padding:20px}
.container {max-width:950px;margin:0 auto}
.header {text-align:center;color:white;margin-bottom:40px}
.header h1 {font-size:2.5em;margin-bottom:10px}
.header p {font-size:1.1em;opacity:0.9}
.grade-badge {display:inline-block;background:rgba(255,255,255,0.2);padding:8px 20px;border-radius:20px;margin-top:10px;font-weight:600}
.mode-selector {display:flex;gap:10px;justify-content:center;flex-wrap:wrap;margin-bottom:30px}
.mode-btn {background:white;border:none;padding:15px 25px;border-radius:12px;font-size:1em;font-weight:600;cursor:pointer;transition:all 0.3s;box-shadow:0 4px 6px rgba(0,0,0,0.1)}
.mode-btn:hover {transform:translateY(-2px);box-shadow:0 6px 12px rgba(0,0,0,0.15)}
.mode-btn.active {background:#667eea;color:white}
.content-area {background:white;border-radius:20px;padding:40px;box-shadow:0 10px 30px rgba(0,0,0,0.2);min-height:400px}
.flashcard-container {perspective:1000px;height:380px;margin-bottom:20px}
.flashcard {width:100%;height:100%;position:relative;transform-style:preserve-3d;transition:transform 0.6s;cursor:pointer}
.flashcard.flipped {transform:rotateY(180deg)}
.flashcard-front,.flashcard-back {position:absolute;width:100%;height:100%;backface-visibility:hidden;border-radius:15px;display:flex;flex-direction:column;align-items:center;justify-content:center;padding:30px;text-align:center}
.flashcard-front {background:linear-gradient(135deg,#667eea 0%,#764ba2 100%);color:white}
.flashcard-back {background:linear-gradient(135deg,#f093fb 0%,#f5576c 100%);color:white;transform:rotateY(180deg)}
.flashcard-content {font-size:1.25em;line-height:1.6}
.difficulty-badge {position:absolute;top:20px;right:20px;padding:6px 14px;border-radius:12px;font-size:0.85em;font-weight:600;background:rgba(255,255,255,0.25)}
.flashcard-controls {display:flex;justify-content:space-between;align-items:center;margin-top:20px;flex-wrap:wrap;gap:10px}
.card-counter {font-size:1.1em;color:#666}
.nav-buttons {display:flex;gap:10px;flex-wrap:wrap}
.nav-btn {background:#667eea;color:white;border:none;padding:10px 20px;border-radius:8px;cursor:pointer;font-size:1em;transition:all 0.3s}
.nav-btn:hover:not(:disabled) {background:#5568d3;transform:translateY(-1px)}
.nav-btn:disabled {background:#ccc;cursor:not-allowed;transform:none;opacity:0.6}
.shuffle-btn {background:#28a745;color:white;border:none;padding:10px 20px;border-radius:8px;cursor:pointer;font-size:0.95em;transition:all 0.3s}
.shuffle-btn:hover {background:#218838;transform:translateY(-1px)}
.question-container {margin-bottom:30px}
.question-header {display:flex;justify-content:space-between;align-items:center;margin-bottom:15px;flex-wrap:wrap;gap:10px}
.question-type-badge {background:#667eea;color:white;padding:6px 14px;border-radius:12px;font-size:0.9em;font-weight:600}
.marks-badge {background:#f0f2ff;color:#667eea;padding:6px 14px;border-radius:12px;font-size:0.9em;font-weight:600}
.question-text {font-size:1.35em;color:#333;margin-bottom:25px;line-height:1.6}
.options {display:flex;flex-direction:column;gap:12px}
.option {background:#f8f9fa;border:2px solid #e9ecef;padding:18px 20px;border-radius:12px;cursor:pointer;transition:all 0.3s;font-size:1.1em}
.option:hover:not(.correct):not(.incorrect) {border-color:#667eea;background:#f0f2ff}
.option.selected {border-color:#667eea;background:#667eea;color:white}
.option.correct {border-color:#28a745;background:#28a745;color:white}
.option.incorrect {border-color:#dc3545;background:#dc3545;color:white}
.option.disabled {cursor:not-allowed}
.written-answer-box {width:100%;min-height:120px;padding:15px;border:2px solid #e9ecef;border-radius:12px;font-size:1.05em;font-family:inherit;resize:vertical;transition:all 0.3s}
.written-answer-box:focus {outline:none;border-color:#667eea;background:#f0f2ff}
.written-answer-box:disabled {background:#f8f9fa;cursor:not-allowed}
.char-counter {text-align:right;color:#999;font-size:0.9em;margin-top:5px}
.submit-btn {background:#667eea;color:white;border:none;padding:15px 40px;border-radius:12px;font-size:1.1em;font-weight:600;cursor:pointer;margin-top:20px;transition:all 0.3s}
.submit-btn:hover:not(:disabled) {background:#5568d3;transform:translateY(-2px)}
.submit-btn:disabled {background:#ccc;cursor:not-allowed;transform:none}
.feedback {margin-top:25px;padding:25px;border-radius:12px;font-size:1.05em;line-height:1.7}
.feedback.correct {background:#d4edda;border:2px solid #28a745;color:#155724}
.feedback.partial {background:#fff3cd;border:2px solid #ffc107;color:#856404}
.feedback.incorrect {background:#f8d7da;border:2px solid #dc3545;color:#721c24}
.feedback-title {font-weight:700;margin-bottom:12px;font-size:1.25em;display:flex;align-items:center;gap:8px}
.feedback-section {margin:15px 0;padding:15px;background:rgba(255,255,255,0.5);border-radius:8px}
.feedback-section h4 {margin-bottom:8px;color:#333}
.mark-scheme {background:#f0f2ff;padding:15px;border-radius:8px;margin-top:12px;border-left:4px solid #667eea}
.exam-tip {background:#e7f3ff;border-left:4px solid #2196F3;padding:12px 15px;margin-top:12px;border-radius:4px}
.next-question-btn {background:#28a745;color:white;border:none;padding:12px 30px;border-radius:8px;cursor:pointer;margin-top:15px;font-size:1em;font-weight:600;transition:all 0.3s}
.next-question-btn:hover {background:#218838;transform:translateY(-1px)}
.progress-bar {background:#e9ecef;height:10px;border-radius:5px;margin-bottom:20px;overflow:hidden}
.progress-fill {background:linear-gradient(90deg,#667eea 0%,#764ba2 100%);height:100%;transition:width 0.3s}
.stats {display:flex;justify-content:space-around;margin-top:20px;padding:20px;background:#f8f9fa;border-radius:12px;flex-wrap:wrap;gap:15px}
.stat-item {text-align:center;min-width:100px}
.stat-value {font-size:2em;font-weight:700;color:#667eea}
.stat-label {color:#666;margin-top:5px;font-size:0.9em}
.topic-selector {margin-bottom:25px}
.topic-selector label {display:block;margin-bottom:10px;font-weight:600;color:#333}
.topic-selector select {width:100%;padding:12px;border-radius:8px;border:2px solid #e9ecef;font-size:1em;cursor:pointer;background:white}
.topic-selector select:focus {outline:none;border-color:#667eea}
.difficulty-filter {display:flex;gap:10px;margin-bottom:20px;flex-wrap:wrap}
.difficulty-chip {padding:8px 16px;border-radius:20px;border:2px solid #e9ecef;background:white;cursor:pointer;transition:all 0.3s;font-size:0.95em}
.difficulty-chip:hover {border-color:#667eea}
.difficulty-chip.active {background:#667eea;color:white;border-color:#667eea}
.hidden {display:none}
.completion-screen {text-align:center;padding:40px 20px}
.grade-display {font-size:4em;font-weight:700;color:#28a745;margin:20px 0}
.performance-breakdown {display:grid;grid-template-columns:repeat(auto-fit,minmax(200px,1fr));gap:15px;margin:30px 0}
.performance-card {background:#f8f9fa;padding:20px;border-radius:12px;border:2px solid #e9ecef}
.performance-card h3 {color:#667eea;margin-bottom:10px;text-transform:capitalize}
.performance-card p {color:#666;margin:5px 0}
#exam-timer {padding:10px 15px;background:#111827;color:white;border-radius:10px;font-weight:700;margin-bottom:15px;text-align:center;font-size:1.1em}
#exam-timer.warning {background:#dc3545;animation:pulse 1s infinite}
@keyframes pulse {0%,100%{opacity:1}50%{opacity:0.7}}
@media (max-width:768px) {
  .header h1{font-size:2em}
  .content-area{padding:25px}
  .flashcard-content{font-size:1.1em}
  .question-text{font-size:1.2em}
  .mode-selector{gap:8px}
  .mode-btn{padding:12px 20px;font-size:0.95em}
}
</style>
</head>
<body>
<div class="container">
<div class="header">
<h1>📊 GCSE Statistics Mastery</h1>
<p>AQA Specification - Grade 9 Focused</p>
<div class="grade-badge">🎯 Target Grade: 9</div>
</div>

<div class="mode-selector" id="mode-selector">
<button class="mode-btn" data-mode="flashcards">📚 Flashcards</button>
<button class="mode-btn" data-mode="practice">✍️ Practice Questions</button>
<button class="mode-btn" data-mode="hard">🔥 Hard Mode</button>
<button class="mode-btn" data-mode="review">🧠 Review Mistakes</button>
<button class="mode-btn" data-mode="timed">⏱️ Timed Mode (10m)</button>
<button class="mode-btn" data-mode="refresh">♻️ New Questions</button>
<button class="mode-btn hidden" data-mode="stop">⏹️ Stop Timer</button>
</div>

<div class="content-area">
<div id="flashcard-mode">
<div class="topic-selector">
<label for="flashcard-topic">Select Topic:</label>
<select id="flashcard-topic">
<option value="all">All Topics (112 cards)</option>
<option value="sampling">1. Sampling Methods (18 cards)</option>
<option value="charts">2. Charts & Graphs (20 cards)</option>
<option value="averages">3. Averages & Spread (19 cards)</option>
<option value="probability">4. Probability (19 cards)</option>
<option value="correlation">5. Correlation (18 cards)</option>
<option value="timeseries">6. Time Series (18 cards)</option>
</select>
</div>

<div class="difficulty-filter" id="flashcard-difficulty">
<div class="difficulty-chip active" data-difficulty="all">All Levels</div>
<div class="difficulty-chip" data-difficulty="foundation">Foundation</div>
<div class="difficulty-chip" data-difficulty="higher">Higher</div>
<div class="difficulty-chip" data-difficulty="grade9">Grade 9</div>
</div>

<div class="flashcard-container">
<div class="flashcard" id="flashcard">
<div class="flashcard-front">
<div class="difficulty-badge" id="front-difficulty"></div>
<div class="flashcard-content" id="question-side"></div>
</div>
<div class="flashcard-back">
<div class="difficulty-badge" id="back-difficulty"></div>
<div class="flashcard-content" id="answer-side"></div>
</div>
</div>
</div>

<div class="flashcard-controls">
<span class="card-counter" id="card-counter"></span>
<div class="nav-buttons">
<button class="shuffle-btn" id="shuffle-btn">🔀 Shuffle</button>
<button class="nav-btn" id="prev-btn">← Previous</button>
<button class="nav-btn" id="next-btn">Next →</button>
</div>
</div>
</div>

<div id="practice-mode" class="hidden">
<div class="topic-selector">
<label for="practice-topic">Select Topic:</label>
<select id="practice-topic">
<option value="all">All Topics (Mixed)</option>
<option value="sampling">1. Sampling Methods</option>
<option value="charts">2. Charts & Graphs</option>
<option value="averages">3. Averages & Spread</option>
<option value="probability">4. Probability</option>
<option value="correlation">5. Correlation</option>
<option value="timeseries">6. Time Series</option>
</select>
</div>

<div id="exam-timer" class="hidden"></div>
<div class="progress-bar"><div class="progress-fill" id="progress-fill"></div></div>
<div id="question-area"></div>

<div class="stats">
<div class="stat-item"><div class="stat-value" id="correct-count">0</div><div class="stat-label">Correct</div></div>
<div class="stat-item"><div class="stat-value" id="total-count">0</div><div class="stat-label">Attempted</div></div>
<div class="stat-item"><div class="stat-value" id="accuracy">0%</div><div class="stat-label">Accuracy</div></div>
<div class="stat-item"><div class="stat-value" id="total-marks">0/0</div><div class="stat-label">Marks</div></div>
</div>
</div>
</div>
</div>

<script>
// ============================================================================
// DATA STRUCTURES
// ============================================================================

const FLASHCARDS = {
  sampling: [
    {q:"What is a population in statistics?",a:"The entire group you want to study or collect data from.",difficulty:"foundation"},
    {q:"What is a sample?",a:"A smaller group selected from the population.",difficulty:"foundation"},
    {q:"What is random sampling?",a:"Every member has equal chance of selection.",difficulty:"foundation"},
    {q:"What is systematic sampling?",a:"Select every nth member from a list.",difficulty:"higher"},
    {q:"What is stratified sampling?",a:"Sample proportionally from each subgroup to ensure representation.",difficulty:"higher"},
    {q:"What is a census?",a:"Collecting data from every member of the population.",difficulty:"foundation"},
    {q:"What is quota sampling?",a:"Fixed numbers from each group, non-random selection.",difficulty:"higher"},
    {q:"What is sampling bias?",a:"When the sample doesn't accurately represent the population.",difficulty:"higher"},
    {q:"What is cluster sampling?",a:"Select whole clusters (groups) randomly, then survey all members.",difficulty:"grade9"},
    {q:"Why use stratified sampling?",a:"Ensures each subgroup is proportionally represented.",difficulty:"higher"},
    {q:"What is convenience sampling?",a:"Selecting the easiest accessible people (often biased).",difficulty:"higher"},
    {q:"What is a sampling frame?",a:"A complete list of all population members.",difficulty:"grade9"},
    {q:"Advantage of random sampling?",a:"Unbiased selection, every member has equal chance.",difficulty:"higher"},
    {q:"Disadvantage of random sampling?",a:"Needs complete population list (sampling frame).",difficulty:"higher"},
    {q:"When to use systematic sampling?",a:"When population has an ordered list available.",difficulty:"grade9"},
    {q:"Stratified sample size formula?",a:"(Stratum size ÷ Population size) × Sample size.",difficulty:"grade9"},
    {q:"What is non-response bias?",a:"When non-responders differ systematically from responders.",difficulty:"grade9"},
    {q:"What makes a good sample?",a:"Large enough, representative, and randomly selected.",difficulty:"higher"}
  ],
  
  charts: [
    {q:"What does a histogram show?",a:"Continuous data where area represents frequency.",difficulty:"foundation"},
    {q:"Frequency density formula?",a:"Frequency ÷ Class width.",difficulty:"higher"},
    {q:"What is a cumulative frequency graph?",a:"Shows running total of frequencies.",difficulty:"higher"},
    {q:"What does a box plot show?",a:"Minimum, Q1, median, Q3, and maximum values.",difficulty:"higher"},
    {q:"What is interquartile range?",a:"Q3 - Q1 (middle 50% of data).",difficulty:"higher"},
    {q:"What is a scatter diagram for?",a:"Showing relationship between two variables.",difficulty:"foundation"},
    {q:"Histogram vs bar chart difference?",a:"Histogram has continuous data with no gaps; bar chart has categories.",difficulty:"higher"},
    {q:"How to estimate frequency from histogram?",a:"Frequency density × Class width.",difficulty:"grade9"},
    {q:"What is a back-to-back stem-and-leaf?",a:"Compares two datasets side by side.",difficulty:"higher"},
    {q:"What is a frequency polygon?",a:"Line graph joining midpoints of histogram bars.",difficulty:"higher"},
    {q:"Where to plot cumulative frequency?",a:"At upper class boundaries.",difficulty:"grade9"},
    {q:"What does box plot width show?",a:"Interquartile range (spread of middle 50%).",difficulty:"higher"},
    {q:"How to find median from cumulative frequency?",a:"Find n/2 on y-axis, read across to curve, down to x-axis.",difficulty:"grade9"},
    {q:"What is skewness?",a:"When data is not symmetrical around the median.",difficulty:"grade9"},
    {q:"Positive skew means?",a:"Tail on right side, mean > median.",difficulty:"grade9"},
    {q:"Negative skew means?",a:"Tail on left side, mean < median.",difficulty:"grade9"},
    {q:"What are outliers?",a:"Values significantly different from other data.",difficulty:"higher"},
    {q:"Outlier boundary formula?",a:"Q1 - 1.5×IQR or Q3 + 1.5×IQR.",difficulty:"grade9"},
    {q:"Why use two-way tables?",a:"Show relationship between two categorical variables.",difficulty:"higher"},
    {q:"What is class width?",a:"Upper boundary - Lower boundary.",difficulty:"foundation"}
  ],
  
  averages: [
    {q:"What is the mean?",a:"Sum of all values ÷ Number of values.",difficulty:"foundation"},
    {q:"What is the median?",a:"Middle value when data is ordered.",difficulty:"foundation"},
    {q:"What is the mode?",a:"Most frequently occurring value.",difficulty:"foundation"},
    {q:"What is the range?",a:"Maximum value - Minimum value.",difficulty:"foundation"},
    {q:"Mean for grouped data formula?",a:"Σ(frequency × midpoint) ÷ Σfrequency.",difficulty:"higher"},
    {q:"What is standard deviation?",a:"Measure of spread from the mean.",difficulty:"grade9"},
    {q:"When is median better than mean?",a:"When data is skewed or has outliers.",difficulty:"higher"},
    {q:"What is modal class?",a:"Class interval with highest frequency.",difficulty:"higher"},
    {q:"How to find class midpoint?",a:"(Lower boundary + Upper boundary) ÷ 2.",difficulty:"higher"},
    {q:"What does large range indicate?",a:"Wide spread of data values.",difficulty:"higher"},
    {q:"What is variance?",a:"(Standard deviation)² - average of squared deviations.",difficulty:"grade9"},
    {q:"How to compare two datasets?",a:"Compare measure of center (mean/median) AND spread (range/IQR).",difficulty:"grade9"},
    {q:"What is the median position?",a:"(n + 1) ÷ 2.",difficulty:"higher"},
    {q:"What is Q1?",a:"Lower quartile - 25th percentile.",difficulty:"higher"},
    {q:"What is Q3?",a:"Upper quartile - 75th percentile.",difficulty:"higher"},
    {q:"Why is mean affected by outliers?",a:"Every value contributes equally to the calculation.",difficulty:"higher"},
    {q:"When to use the mode?",a:"For categorical data or to find most common value.",difficulty:"foundation"},
    {q:"What is the effect of adding 5 to all values?",a:"Mean and median increase by 5, range stays same.",difficulty:"grade9"},
    {q:"What is the effect of multiplying all values by 2?",a:"Mean, median, and range all double.",difficulty:"grade9"}
  ],
  
  probability: [
    {q:"Basic probability formula?",a:"Number of favorable outcomes ÷ Total number of outcomes.",difficulty:"foundation"},
    {q:"What does P(A') mean?",a:"Probability that event A does NOT happen.",difficulty:"higher"},
    {q:"What are mutually exclusive events?",a:"Events that cannot happen at the same time.",difficulty:"higher"},
    {q:"What are independent events?",a:"One event does not affect the probability of the other.",difficulty:"higher"},
    {q:"What is conditional probability?",a:"Probability of an event given another event has occurred.",difficulty:"grade9"},
    {q:"Expected frequency formula?",a:"Probability × Number of trials.",difficulty:"higher"},
    {q:"What is a tree diagram used for?",a:"Showing combined probabilities of multiple events.",difficulty:"higher"},
    {q:"P(A or B) for mutually exclusive?",a:"P(A) + P(B).",difficulty:"grade9"},
    {q:"P(A and B) for independent events?",a:"P(A) × P(B).",difficulty:"grade9"},
    {q:"What are exhaustive events?",a:"Events that cover all possible outcomes.",difficulty:"higher"},
    {q:"What is relative frequency?",a:"Experimental probability from trials.",difficulty:"foundation"},
    {q:"What is expected value?",a:"Long-run average outcome.",difficulty:"grade9"},
    {q:"What does P(A) + P(A') equal?",a:"1 (certainty).",difficulty:"higher"},
    {q:"Sample space definition?",a:"Set of all possible outcomes.",difficulty:"foundation"},
    {q:"What is theoretical probability?",a:"Based on equally likely outcomes.",difficulty:"foundation"},
    {q:"Probability range?",a:"Between 0 and 1 (or 0% to 100%).",difficulty:"foundation"},
    {q:"Venn diagram use in probability?",a:"Show relationships between events and calculate combined probabilities.",difficulty:"higher"},
    {q:"What is the addition rule?",a:"P(A or B) = P(A) + P(B) - P(A and B).",difficulty:"grade9"},
    {q:"When to multiply probabilities?",a:"For independent events happening together (AND).",difficulty:"higher"}
  ],
  
  correlation: [
    {q:"What is positive correlation?",a:"As one variable increases, the other also increases.",difficulty:"foundation"},
    {q:"What is negative correlation?",a:"As one variable increases, the other decreases.",difficulty:"foundation"},
    {q:"What is no correlation?",a:"No clear relationship pattern between variables.",difficulty:"foundation"},
    {q:"What is line of best fit?",a:"Line that shows the overall trend in scatter diagram.",difficulty:"higher"},
    {q:"What is interpolation?",a:"Predicting values within the data range.",difficulty:"higher"},
    {q:"What is extrapolation?",a:"Predicting values outside the data range (less reliable).",difficulty:"higher"},
    {q:"Does correlation prove causation?",a:"No - correlation does NOT prove causation.",difficulty:"higher"},
    {q:"What is strong correlation?",a:"Points lie close to the line of best fit.",difficulty:"higher"},
    {q:"What is weak correlation?",a:"Points are scattered far from the line of best fit.",difficulty:"higher"},
    {q:"What is the mean point?",a:"Point at (mean of x values, mean of y values).",difficulty:"grade9"},
    {q:"What is a confounding variable?",a:"A third variable that affects both variables being studied.",difficulty:"grade9"},
    {q:"Correlation coefficient range?",a:"-1 to +1.",difficulty:"grade9"},
    {q:"What does correlation coefficient of 0 mean?",a:"No linear correlation.",difficulty:"grade9"},
    {q:"What does correlation coefficient of +1 mean?",a:"Perfect positive correlation.",difficulty:"grade9"},
    {q:"What does correlation coefficient of -1 mean?",a:"Perfect negative correlation.",difficulty:"grade9"},
    {q:"Line of best fit property?",a:"Passes through (mean x, mean y) and balances points.",difficulty:"grade9"},
    {q:"Why is extrapolation unreliable?",a:"Relationship may change outside observed data range.",difficulty:"higher"},
    {q:"Example of correlation without causation?",a:"Ice cream sales and drownings (both caused by hot weather).",difficulty:"higher"}
  ],
  
  timeseries: [
    {q:"What is a time series?",a:"Data recorded at regular time intervals.",difficulty:"foundation"},
    {q:"What is a trend?",a:"Long-term general direction of the data.",difficulty:"foundation"},
    {q:"What are seasonal variations?",a:"Regular, repeating patterns in data.",difficulty:"higher"},
    {q:"What is a moving average?",a:"Average that smooths data to show the trend.",difficulty:"higher"},
    {q:"How to calculate 4-point moving average?",a:"Sum of 4 consecutive values ÷ 4.",difficulty:"higher"},
    {q:"Why use moving averages?",a:"Remove short-term fluctuations to reveal trend.",difficulty:"higher"},
    {q:"What are random variations?",a:"Unpredictable, irregular changes in data.",difficulty:"higher"},
    {q:"How to calculate 3-point moving average?",a:"Sum of 3 consecutive values ÷ 3.",difficulty:"higher"},
    {q:"What is an increasing trend?",a:"Values generally rising over time.",difficulty:"foundation"},
    {q:"What is a decreasing trend?",a:"Values generally falling over time.",difficulty:"foundation"},
    {q:"What is seasonal effect?",a:"Actual value - Trend value.",difficulty:"grade9"},
    {q:"What is cyclical variation?",a:"Long-term irregular repeating patterns.",difficulty:"grade9"},
    {q:"Where to plot moving averages?",a:"At the middle time period of the values used.",difficulty:"grade9"},
    {q:"4-point MA plotting position?",a:"Halfway between 2nd and 3rd values.",difficulty:"grade9"},
    {q:"3-point MA plotting position?",a:"At the middle (2nd) value.",difficulty:"grade9"},
    {q:"Purpose of time series analysis?",a:"Identify trends and make predictions.",difficulty:"higher"},
    {q:"What is deseasonalization?",a:"Removing seasonal effects to see underlying trend.",difficulty:"grade9"},
    {q:"How to predict future values?",a:"Extend the trend line and add seasonal effect.",difficulty:"grade9"}
  ]
};

// ============================================================================
// STATE MANAGEMENT
// ============================================================================

const state = {
  flashcards: {
    currentTopic: 'all',
    currentDifficulty: 'all',
    currentIndex: 0,
    cards: [],
    isFlipped: false
  },
  practice: {
    currentTopic: 'all',
    currentIndex: 0,
    questions: [],
    selectedAnswer: null,
    submitted: false,
    correctCount: 0,
    totalCount: 0,
    marksEarned: 0,
    marksPossible: 0
  },
  timer: {
    active: false,
    interval: null,
    secondsLeft: 0
  },
  progress: {
    totalAttempts: 0,
    totalCorrect: 0,
    topicStats: {},
    wrongQuestions: [],
    streak: 0,
    lastStudyDate: null
  }
};

// ============================================================================
// UTILITY FUNCTIONS
// ============================================================================

function rand(min, max) {
  return Math.floor(Math.random() * (max - min + 1)) + min;
}

function choice(arr) {
  return arr[rand(0, arr.length - 1)];
}

function shuffle(arr) {
  const result = [...arr];
  for (let i = result.length - 1; i > 0; i--) {
    const j = rand(0, i);
    [result[i], result[j]] = [result[j], result[i]];
  }
  return result;
}

function normalizeText(text) {
  return (text || '').toLowerCase()
    .replace(/[^a-z0-9\s]/g, ' ')
    .replace(/\s+/g, ' ')
    .trim();
}

// ============================================================================
// QUESTION GENERATION
// ============================================================================

function generateQuestions() {
  const bank = {
    sampling: [],
    charts: [],
    averages: [],
    probability: [],
    correlation: [],
    timeseries: []
  };

  // SAMPLING QUESTIONS
  for (let i = 0; i < 35; i++) {
    const pop = rand(200, 2000);
    const sample = rand(30, 200);
    const strata = rand(2, 5);
    
    bank.sampling.push({
      type: 'mcq',
      q: `A researcher has a population of ${pop} people. Which sampling method ensures every person has an equal chance of selection?`,
      options: ['Random sampling', 'Convenience sampling', 'Quota sampling', 'Judgement sampling'],
      correct: 0,
      marks: 1,
      explanation: 'Random sampling gives every member an equal probability of selection, making it unbiased.',
      examTip: 'Random = equal chance for all members.'
    });

    bank.sampling.push({
      type: 'written',
      q: `Describe how to obtain a stratified sample of ${sample} students from a school with ${rand(3, 6)} year groups.`,
      modelAnswer: `Calculate the proportion of students in each year group. Multiply each proportion by ${sample} to find how many to select from each group. Then randomly select that number from each year group.`,
      marks: 3,
      keywords: ['stratified', 'proportion', 'random', 'each group'],
      markScheme: ['Calculate proportions (1 mark)', 'Multiply by sample size (1 mark)', 'Random selection from each group (1 mark)'],
      examTip: 'Always mention: proportions, calculation, and random selection within strata.'
    });

    bank.sampling.push({
      type: 'mcq',
      q: `What is the main disadvantage of systematic sampling?`,
      options: ['Too expensive', 'Needs ordered list', 'Pattern in list can cause bias', 'Takes too long'],
      correct: 2,
      marks: 1,
      explanation: 'If there\'s a hidden pattern in the list (e.g., every 10th person is a manager), systematic sampling can introduce bias.',
      examTip: 'Systematic = watch for hidden patterns in the list.'
    });
  }

  // CHARTS & GRAPHS QUESTIONS
  for (let i = 0; i < 35; i++) {
    const freq = rand(20, 80);
    const width = rand(5, 20);
    
    bank.charts.push({
      type: 'mcq',
      q: `In a histogram, what does the area of each bar represent?`,
      options: ['Class width', 'Frequency', 'Frequency density', 'Mean'],
      correct: 1,
      marks: 1,
      explanation: 'In histograms, area = frequency. This is why we calculate frequency density = frequency ÷ class width.',
      examTip: 'AREA = FREQUENCY in all histograms.'
    });

    bank.charts.push({
      type: 'written',
      q: `A histogram bar has frequency ${freq} and class width ${width}. Calculate the frequency density.`,
      modelAnswer: `Frequency density = ${freq} ÷ ${width} = ${(freq/width).toFixed(2)}`,
      marks: 2,
      keywords: ['frequency density', 'divide', width.toString()],
      markScheme: ['Correct formula used (1 mark)', 'Correct answer (1 mark)'],
      examTip: 'Frequency density = Frequency ÷ Class width (always divide).'
    });

    const q1 = rand(10, 30);
    const q3 = rand(40, 70);
    
    bank.charts.push({
      type: 'mcq',
      q: `A box plot shows Q1 = ${q1} and Q3 = ${q3}. What is the interquartile range?`,
      options: [`${q1 + q3}`, `${q3 - q1}`, `${q3}`, `${(q1 + q3) / 2}`],
      correct: 1,
      marks: 1,
      explanation: `IQR = Q3 - Q1 = ${q3} - ${q1} = ${q3 - q1}`,
      examTip: 'IQR = Q3 - Q1 (measures spread of middle 50%).'
    });
  }

  // AVERAGES & SPREAD QUESTIONS
  for (let i = 0; i < 35; i++) {
    const vals = Array.from({length: rand(5, 9)}, () => rand(10, 100));
    const mean = (vals.reduce((a, b) => a + b, 0) / vals.length).toFixed(1);
    
    bank.averages.push({
      type: 'mcq',
      q: `When is the median a better measure than the mean?`,
      options: ['Always', 'When data is skewed', 'When calculating totals', 'When data is exact'],
      correct: 1,
      marks: 1,
      explanation: 'Median is better for skewed data because it is not affected by extreme values (outliers).',
      examTip: 'Skewed data or outliers → use median.'
    });

    bank.averages.push({
      type: 'written',
      q: `Explain why the mean might not be representative of data with outliers.`,
      modelAnswer: `Outliers are extreme values that pull the mean away from the typical values. The mean includes all values equally, so one very large or small value significantly affects the result.`,
      marks: 2,
      keywords: ['outliers', 'extreme', 'pull', 'mean', 'affect'],
      markScheme: ['Mentions outliers (1 mark)', 'Explains effect on mean (1 mark)'],
      examTip: 'Mean is sensitive to outliers - use median instead.'
    });

    bank.averages.push({
      type: 'mcq',
      q: `What happens to the range if you add 10 to every value in a dataset?`,
      options: ['Increases by 10', 'Decreases by 10', 'Stays the same', 'Doubles'],
      correct: 2,
      marks: 1,
      explanation: 'Range = max - min. Adding 10 to all values adds 10 to both max and min, so the difference stays the same.',
      examTip: 'Adding/subtracting constant → range unchanged.'
    });
  }

  // PROBABILITY QUESTIONS
  for (let i = 0; i < 35; i++) {
    const total = rand(20, 50);
    const favorable = rand(5, total - 5);
    const prob = (favorable / total).toFixed(3);
    
    bank.probability.push({
      type: 'mcq',
      q: `What is the probability of an impossible event?`,
      options: ['0', '0.5', '1', 'Cannot be calculated'],
      correct: 0,
      marks: 1,
      explanation: 'Impossible events have probability 0. Certain events have probability 1.',
      examTip: 'Probability scale: 0 (impossible) to 1 (certain).'
    });

    bank.probability.push({
      type: 'written',
      q: `A bag has ${total} balls. ${favorable} are red. What is the probability of picking a red ball?`,
      modelAnswer: `P(red) = ${favorable}/${total} = ${prob}`,
      marks: 2,
      keywords: ['probability', favorable.toString(), total.toString()],
      markScheme: ['Correct fraction (1 mark)', 'Correct decimal (1 mark)'],
      examTip: 'Probability = favorable outcomes ÷ total outcomes.'
    });

    const pA = (rand(2, 8) / 10).toFixed(1);
    
    bank.probability.push({
      type: 'mcq',
      q: `If P(A) = ${pA}, what is P(A')?`,
      options: [`${(1 - pA).toFixed(1)}`, pA, '1', '0'],
      correct: 0,
      marks: 1,
      explanation: `P(A') = 1 - P(A) = 1 - ${pA} = ${(1 - pA).toFixed(1)}`,
      examTip: 'P(A) + P(A\') = 1 always.'
    });

    const trials = rand(50, 200);
    const p = (rand(1, 4) / 10).toFixed(2);
    
    bank.probability.push({
      type: 'written',
      q: `A coin has P(heads) = ${p}. In ${trials} flips, how many heads are expected?`,
      modelAnswer: `Expected frequency = ${p} × ${trials} = ${(p * trials).toFixed(1)}`,
      marks: 2,
      keywords: ['expected', 'probability', trials.toString()],
      markScheme: ['Correct formula (1 mark)', 'Correct answer (1 mark)'],
      examTip: 'Expected frequency = probability × number of trials.'
    });
  }

  // CORRELATION QUESTIONS
  for (let i = 0; i < 35; i++) {
    bank.correlation.push({
      type: 'mcq',
      q: `What type of correlation shows both variables increasing together?`,
      options: ['Positive', 'Negative', 'None', 'Zero'],
      correct: 0,
      marks: 1,
      explanation: 'Positive correlation: as one variable increases, the other also increases.',
      examTip: 'Upward slope = positive correlation.'
    });

    bank.correlation.push({
      type: 'written',
      q: `Explain why correlation does not prove causation.`,
      modelAnswer: `Correlation shows a relationship between variables but doesn't prove one causes the other. There could be a third confounding variable affecting both, or the relationship could be coincidental.`,
      marks: 3,
      keywords: ['correlation', 'causation', 'confounding', 'third variable'],
      markScheme: ['States correlation ≠ causation (1 mark)', 'Mentions confounding variable (1 mark)', 'Example or explanation (1 mark)'],
      examTip: 'Always state: correlation does NOT prove causation.'
    });

    bank.correlation.push({
      type: 'mcq',
      q: `What is interpolation?`,
      options: ['Predicting outside data range', 'Predicting within data range', 'Finding the mean', 'Drawing best fit line'],
      correct: 1,
      marks: 1,
      explanation: 'Interpolation = prediction within the data range (more reliable). Extrapolation = outside range (less reliable).',
      examTip: 'Inter = inside; Extra = outside.'
    });

    bank.correlation.push({
      type: 'written',
      q: `Why is extrapolation less reliable than interpolation?`,
      modelAnswer: `Extrapolation predicts outside the observed data range where the relationship pattern may change or break down. We have no evidence the trend continues beyond the data.`,
      marks: 2,
      keywords: ['extrapolation', 'outside', 'range', 'unreliable', 'trend'],
      markScheme: ['States outside data range (1 mark)', 'Explains why unreliable (1 mark)'],
      examTip: 'Extrapolation assumes trend continues - often wrong.'
    });
  }

  // TIME SERIES QUESTIONS
  for (let i = 0; i < 35; i++) {
    const values = Array.from({length: 4}, () => rand(20, 80));
    const ma = (values.reduce((a, b) => a + b, 0) / 4).toFixed(1);
    
    bank.timeseries.push({
      type: 'mcq',
      q: `What does a moving average show in time series?`,
      options: ['Exact values', 'The trend', 'Random variation', 'Seasonal effects'],
      correct: 1,
      marks: 1,
      explanation: 'Moving averages smooth out short-term fluctuations to reveal the underlying trend.',
      examTip: 'Moving average = smoothed trend.'
    });

    bank.timeseries.push({
      type: 'written',
      q: `Calculate the 4-point moving average for: ${values.join(', ')}`,
      modelAnswer: `(${values.join(' + ')}) ÷ 4 = ${ma}`,
      marks: 2,
      keywords: ['moving average', '4', ma],
      markScheme: ['Correct sum (1 mark)', 'Divide by 4 (1 mark)'],
      examTip: 'n-point MA = sum of n values ÷ n.'
    });

    bank.timeseries.push({
      type: 'mcq',
      q: `What are seasonal variations?`,
      options: ['Random changes', 'Long-term trend', 'Regular repeating patterns', 'One-time events'],
      correct: 2,
      marks: 1,
      explanation: 'Seasonal variations are regular patterns that repeat at fixed intervals (e.g., ice cream sales higher in summer).',
      examTip: 'Seasonal = regular repeating pattern.'
    });

    bank.timeseries.push({
      type: 'written',
      q: `Explain why moving averages are useful in time series analysis.`,
      modelAnswer: `Moving averages remove short-term fluctuations and random variations, making it easier to see the underlying long-term trend in the data.`,
      marks: 2,
      keywords: ['moving average', 'fluctuations', 'trend', 'smooth'],
      markScheme: ['Removes fluctuations (1 mark)', 'Shows trend (1 mark)'],
      examTip: 'MAs smooth data to reveal trends.'
    });
  }

  // Shuffle all question banks
  Object.keys(bank).forEach(topic => {
    bank[topic] = shuffle(bank[topic]);
  });

  return bank;
}

let QUESTION_BANK = generateQuestions();

// ============================================================================
// PROGRESS TRACKING
// ============================================================================

function loadProgress() {
  try {
    const saved = localStorage.getItem('statsProgress');
    if (saved) {
      const data = JSON.parse(saved);
      state.progress = { ...state.progress, ...data };
    }
  } catch (e) {
    console.error('Failed to load progress:', e);
  }
}

function saveProgress() {
  try {
    localStorage.setItem('statsProgress', JSON.stringify(state.progress));
  } catch (e) {
    console.error('Failed to save progress:', e);
  }
}

function updateStreak() {
  const today = new Date().toDateString();
  if (state.progress.lastStudyDate !== today) {
    const yesterday = new Date();
    yesterday.setDate(yesterday.getDate() - 1);
    const wasYesterday = state.progress.lastStudyDate === yesterday.toDateString();
    
    state.progress.streak = wasYesterday ? state.progress.streak + 1 : 1;
    state.progress.lastStudyDate = today;
    saveProgress();
  }
}

function recordQuestionResult(topic, question, correct, marksEarned = 0) {
  if (!state.progress.topicStats[topic]) {
    state.progress.topicStats[topic] = { correct: 0, attempted: 0 };
  }
  
  state.progress.totalAttempts++;
  state.progress.topicStats[topic].attempted++;
  
  if (correct) {
    state.progress.totalCorrect++;
    state.progress.topicStats[topic].correct++;
  } else {
    state.progress.wrongQuestions.push({
      topic,
      question: question.q,
      answer: question.modelAnswer || question.explanation || '',
      type: question.type
    });
  }
  
  saveProgress();
}

// ============================================================================
// WRITTEN ANSWER SCORING
// ============================================================================

function scoreWrittenAnswer(userAnswer, question) {
  const answer = normalizeText(userAnswer);
  const model = normalizeText(question.modelAnswer || '');
  
  if (answer.length < 10) return 0;
  
  const keywords = question.keywords || [];
  const modelWords = model.split(' ').filter(w => w.length > 4);
  const allTerms = [...new Set([...keywords, ...modelWords])].slice(0, 20);
  
  let keywordMatches = 0;
  for (const term of allTerms) {
    if (answer.includes(normalizeText(term))) {
      keywordMatches++;
    }
  }
  
  const lengthBonus = answer.length > 30 ? 1 : 0;
  const structureBonus = (answer.includes('because') || answer.includes('therefore') || answer.includes('so')) ? 1 : 0;
  
  const score = Math.min(
    question.marks,
    Math.round((keywordMatches + lengthBonus + structureBonus) / Math.max(3, allTerms.length / 3) * question.marks)
  );
  
  return Math.max(0, score);
}

// ============================================================================
// FLASHCARD FUNCTIONS
// ============================================================================

function getAllFlashcards() {
  const topic = state.flashcards.currentTopic;
  return topic === 'all' 
    ? Object.values(FLASHCARDS).flat() 
    : FLASHCARDS[topic] || [];
}

function getFilteredFlashcards() {
  let cards = getAllFlashcards();
  const difficulty = state.flashcards.currentDifficulty;
  
  if (difficulty !== 'all') {
    cards = cards.filter(c => c.difficulty === difficulty);
  }
  
  return cards;
}

function loadFlashcards() {
  state.flashcards.currentTopic = document.getElementById('flashcard-topic').value;
  state.flashcards.cards = shuffle(getFilteredFlashcards());
  state.flashcards.currentIndex = 0;
  state.flashcards.isFlipped = false;
  renderFlashcard();
}

function renderFlashcard() {
  const cards = state.flashcards.cards;
  const index = state.flashcards.currentIndex;
  
  if (cards.length === 0) {
    document.getElementById('question-side').textContent = 'No cards found.';
    document.getElementById('answer-side').textContent = 'Try a different filter.';
    document.getElementById('front-difficulty').textContent = '';
    document.getElementById('back-difficulty').textContent = '';
    document.getElementById('card-counter').textContent = '0/0';
    document.getElementById('prev-btn').disabled = true;
    document.getElementById('next-btn').disabled = true;
    return;
  }
  
  const card = cards[index];
  const flashcardEl = document.getElementById('flashcard');
  
  if (state.flashcards.isFlipped) {
    flashcardEl.classList.remove('flipped');
    state.flashcards.isFlipped = false;
  }
  
  document.getElementById('question-side').textContent = card.q;
  document.getElementById('answer-side').textContent = card.a;
  document.getElementById('front-difficulty').textContent = card.difficulty.toUpperCase();
  document.getElementById('back-difficulty').textContent = card.difficulty.toUpperCase();
  document.getElementById('card-counter').textContent = `${index + 1}/${cards.length}`;
  
  document.getElementById('prev-btn').disabled = index === 0;
  document.getElementById('next-btn').disabled = index === cards.length - 1;
}

function flipCard() {
  const flashcardEl = document.getElementById('flashcard');
  flashcardEl.classList.toggle('flipped');
  state.flashcards.isFlipped = !state.flashcards.isFlipped;
}

function nextCard() {
  if (state.flashcards.currentIndex < state.flashcards.cards.length - 1) {
    state.flashcards.currentIndex++;
    state.flashcards.isFlipped = false;
    renderFlashcard();
  }
}

function previousCard() {
  if (state.flashcards.currentIndex > 0) {
    state.flashcards.currentIndex--;
    state.flashcards.isFlipped = false;
    renderFlashcard();
  }
}

function shuffleFlashcards() {
  state.flashcards.cards = shuffle(getFilteredFlashcards());
  state.flashcards.currentIndex = 0;
  state.flashcards.isFlipped = false;
  renderFlashcard();
}

function filterFlashcards(difficulty) {
  state.flashcards.currentDifficulty = difficulty;
  
  document.querySelectorAll('#flashcard-difficulty .difficulty-chip').forEach(chip => {
    chip.classList.toggle('active', chip.dataset.difficulty === difficulty);
  });
  
  loadFlashcards();
}

// ============================================================================
// PRACTICE QUESTION FUNCTIONS
// ============================================================================

function loadPracticeQuestions() {
  const topic = document.getElementById('practice-topic').value;
  state.practice.currentTopic = topic;
  
  let questions;
  if (topic === 'all') {
    questions = Object.values(QUESTION_BANK).flat();
  } else {
    questions = QUESTION_BANK[topic] || [];
  }
  
  state.practice.questions = shuffle(questions).slice(0, 20); // Limit to 20 questions
  state.practice.currentIndex = 0;
  state.practice.selectedAnswer = null;
  state.practice.submitted = false;
  state.practice.correctCount = 0;
  state.practice.totalCount = 0;
  state.practice.marksEarned = 0;
  state.practice.marksPossible = 0;
  
  updateStats();
  renderQuestion();
}

function renderQuestion() {
  const questions = state.practice.questions;
  const index = state.practice.currentIndex;
  
  if (index >= questions.length) {
    renderCompletionScreen();
    return;
  }
  
  const q = questions[index];
  state.practice.selectedAnswer = null;
  state.practice.submitted = false;
  
  let html = `
    <div class="question-container">
      <div class="question-header">
        <div class="question-type-badge">${q.type === 'mcq' ? 'Multiple Choice' : 'Written Answer'}</div>
        <div class="marks-badge">${q.marks} mark${q.marks > 1 ? 's' : ''}</div>
      </div>
      <div class="question-text">${q.q}</div>
  `;
  
  if (q.type === 'mcq') {
    html += '<div class="options">';
    q.options.forEach((opt, i) => {
      html += `<div class="option" data-index="${i}">${String.fromCharCode(65 + i)}. ${opt}</div>`;
    });
    html += '</div>';
    html += '<button class="submit-btn" id="submit-btn" disabled>Submit Answer</button>';
  } else {
    html += `
      <textarea class="written-answer-box" id="written-answer" placeholder="Type your answer here..." maxlength="1000"></textarea>
      <div class="char-counter" id="char-counter">0 / 1000 chars</div>
      <button class="submit-btn" id="submit-btn">Submit Answer</button>
    `;
  }
  
  html += '</div>';
  
  document.getElementById('question-area').innerHTML = html;
  
  // Update progress bar
  const progress = (index / questions.length) * 100;
  document.getElementById('progress-fill').style.width = `${progress}%`;
  
  // Add event listeners
  if (q.type === 'mcq') {
    document.querySelectorAll('.option').forEach(opt => {
      opt.addEventListener('click', handleOptionClick);
    });
  } else {
    const textarea = document.getElementById('written-answer');
    if (textarea) {
      textarea.addEventListener('input', updateCharCount);
    }
  }
  
  const submitBtn = document.getElementById('submit-btn');
  if (submitBtn) {
    submitBtn.addEventListener('click', submitAnswer);
  }
}

function handleOptionClick(e) {
  if (state.practice.submitted) return;
  
  const index = parseInt(e.currentTarget.dataset.index);
  state.practice.selectedAnswer = index;
  
  document.querySelectorAll('.option').forEach(opt => {
    opt.classList.remove('selected');
  });
  
  e.currentTarget.classList.add('selected');
  
  const submitBtn = document.getElementById('submit-btn');
  if (submitBtn) {
    submitBtn.disabled = false;
  }
}

function updateCharCount() {
  const textarea = document.getElementById('written-answer');
  const counter = document.getElementById('char-counter');
  
  if (textarea && counter) {
    counter.textContent = `${textarea.value.length} / 1000 chars`;
  }
}

function submitAnswer() {
  if (state.practice.submitted) return;
  
  const q = state.practice.questions[state.practice.currentIndex];
  let isCorrect = false;
  let marksEarned = 0;
  let feedbackClass = 'incorrect';
  let feedbackTitle = '❌ Incorrect';
  
  state.practice.totalCount++;
  state.practice.marksPossible += q.marks;
  
  if (q.type === 'mcq') {
    if (state.practice.selectedAnswer === null) {
      return;
    }
    
    isCorrect = state.practice.selectedAnswer === q.correct;
    marksEarned = isCorrect ? q.marks : 0;
    
    // Update option styling
    document.querySelectorAll('.option').forEach((opt, i) => {
      opt.classList.add('disabled');
      if (i === q.correct) {
        opt.classList.add('correct');
      }
      if (i === state.practice.selectedAnswer && i !== q.correct) {
        opt.classList.add('incorrect');
      }
    });
    
    if (isCorrect) {
      state.practice.correctCount++;
      feedbackClass = 'correct';
      feedbackTitle = '✅ Correct!';
    }
  } else {
    const textarea = document.getElementById('written-answer');
    if (!textarea) return;
    
    const answer = textarea.value.trim();
    if (answer.length < 5) {
      alert('Please write a more detailed answer.');
      return;
    }
    
    marksEarned = scoreWrittenAnswer(answer, q);
    isCorrect = marksEarned === q.marks;
    
    if (isCorrect) {
      feedbackClass = 'correct';
      feedbackTitle = '✅ Excellent!';
      state.practice.correctCount++;
    } else if (marksEarned > 0) {
      feedbackClass = 'partial';
      feedbackTitle = `🟡 Partial Credit (${marksEarned}/${q.marks} marks)`;
    }
    
    textarea.disabled = true;
  }
  
  state.practice.marksEarned += marksEarned;
  state.practice.submitted = true;
  
  // Record result
  recordQuestionResult(state.practice.currentTopic, q, isCorrect, marksEarned);
  
  // Update stats
  updateStats();
  
  // Show feedback
  const feedback = document.createElement('div');
  feedback.className = `feedback ${feedbackClass}`;
  
  let feedbackHTML = `
    <div class="feedback-title">${feedbackTitle}</div>
    <div class="feedback-section">
      <h4>${q.type === 'mcq' ? 'Explanation' : 'Model Answer'}</h4>
      <div>${q.explanation || q.modelAnswer || 'Well done!'}</div>
    </div>
  `;
  
  if (q.markScheme && q.markScheme.length > 0) {
    feedbackHTML += `
      <div class="mark-scheme">
        <strong>Mark Scheme:</strong>
        <ul style="margin:10px 0 0 20px">
          ${q.markScheme.map(point => `<li>${point}</li>`).join('')}
        </ul>
      </div>
    `;
  }
  
  feedbackHTML += `
    <div class="exam-tip">
      <strong>💡 Exam Tip:</strong> ${q.examTip}
    </div>
  `;
  
  feedback.innerHTML = feedbackHTML;
  
  // Add next button
  const nextBtn = document.createElement('button');
  nextBtn.className = 'next-question-btn';
  nextBtn.textContent = state.practice.currentIndex < state.practice.questions.length - 1 
    ? 'Next Question →' 
    : 'See Results';
  nextBtn.addEventListener('click', () => {
    state.practice.currentIndex++;
    renderQuestion();
  });
  
  feedback.appendChild(nextBtn);
  
  document.getElementById('question-area').appendChild(feedback);
  
  // Disable submit button
  const submitBtn = document.getElementById('submit-btn');
  if (submitBtn) {
    submitBtn.disabled = true;
  }
}

function updateStats() {
  document.getElementById('correct-count').textContent = state.practice.correctCount;
  document.getElementById('total-count').textContent = state.practice.totalCount;
  
  const accuracy = state.practice.totalCount > 0 
    ? Math.round((state.practice.correctCount / state.practice.totalCount) * 100)
    : 0;
  document.getElementById('accuracy').textContent = `${accuracy}%`;
  
  document.getElementById('total-marks').textContent = 
    `${state.practice.marksEarned}/${state.practice.marksPossible}`;
}

function renderCompletionScreen() {
  const marksPercent = state.practice.marksPossible > 0
    ? Math.round((state.practice.marksEarned / state.practice.marksPossible) * 100)
    : 0;
  
  let grade = 'U';
  if (marksPercent >= 90) grade = '9';
  else if (marksPercent >= 80) grade = '8';
  else if (marksPercent >= 70) grade = '7';
  else if (marksPercent >= 60) grade = '6';
  else if (marksPercent >= 50) grade = '5';
  else if (marksPercent >= 40) grade = '4';
  else if (marksPercent >= 30) grade = '3';
  
  let html = `
    <div class="completion-screen">
      <h2>🎉 Quiz Complete!</h2>
      <div class="grade-display">Grade ${grade}</div>
      <p><strong>${state.practice.marksEarned}/${state.practice.marksPossible}</strong> marks (${marksPercent}%)</p>
      <p>Questions correct: <strong>${state.practice.correctCount}/${state.practice.totalCount}</strong></p>
      <p>Study streak: <strong>${state.progress.streak} day${state.progress.streak !== 1 ? 's' : ''}</strong> 🔥</p>
      
      ${renderProgressBreakdown()}
      
      <div style="margin-top:30px;display:flex;gap:10px;justify-content:center;flex-wrap:wrap">
        <button class="submit-btn" id="retry-btn">Try Again</button>
        <button class="submit-btn" id="review-mistakes-btn" style="background:#f59e0b">Review Mistakes</button>
        <button class="submit-btn" id="new-topic-btn" style="background:#8b5cf6">New Topic</button>
      </div>
    </div>
  `;
  
  document.getElementById('question-area').innerHTML = html;
  document.getElementById('progress-fill').style.width = '100%';
  
  // Add event listeners
  document.getElementById('retry-btn')?.addEventListener('click', loadPracticeQuestions);
  document.getElementById('review-mistakes-btn')?.addEventListener('click', loadWrongQuestions);
  document.getElementById('new-topic-btn')?.addEventListener('click', () => {
    switchMode('practice');
  });
}

function renderProgressBreakdown() {
  const topics = Object.keys(FLASHCARDS);
  
  let html = '<div class="performance-breakdown">';
  
  topics.forEach(topic => {
    const stats = state.progress.topicStats[topic] || { correct: 0, attempted: 0 };
    const accuracy = stats.attempted > 0 
      ? Math.round((stats.correct / stats.attempted) * 100)
      : 0;
    
    html += `
      <div class="performance-card">
        <h3>${topic.charAt(0).toUpperCase() + topic.slice(1)}</h3>
        <p>Attempted: ${stats.attempted}</p>
        <p>Accuracy: ${accuracy}%</p>
      </div>
    `;
  });
  
  html += '</div>';
  
  return html;
}

// ============================================================================
// SPECIAL MODES
// ============================================================================

function loadHardQuestions() {
  const hardCards = Object.values(FLASHCARDS)
    .flat()
    .filter(c => c.difficulty === 'grade9' || c.difficulty === 'higher');
  
  state.flashcards.cards = shuffle(hardCards);
  state.flashcards.currentIndex = 0;
  state.flashcards.isFlipped = false;
  
  switchMode('flashcards');
  renderFlashcard();
}

function loadWrongQuestions() {
  if (state.progress.wrongQuestions.length === 0) {
    alert('No mistakes recorded yet! Keep practicing.');
    return;
  }
  
  const wrongQs = state.progress.wrongQuestions.map(w => ({
    type: w.type || 'written',
    q: w.question,
    modelAnswer: w.answer,
    marks: 2,
    keywords: [],
    markScheme: ['Review the concept carefully.'],
    examTip: 'Master this topic!',
    explanation: w.answer
  }));
  
  state.practice.questions = shuffle(wrongQs).slice(0, 15);
  state.practice.currentIndex = 0;
  state.practice.selectedAnswer = null;
  state.practice.submitted = false;
  state.practice.correctCount = 0;
  state.practice.totalCount = 0;
  state.practice.marksEarned = 0;
  state.practice.marksPossible = 0;
  
  switchMode('practice');
  updateStats();
  renderQuestion();
}

function refreshQuestionBank() {
  if (confirm('Generate new practice questions? Current progress will be saved.')) {
    QUESTION_BANK = generateQuestions();
    loadPracticeQuestions();
    alert('✨ New questions generated!');
  }
}

// ============================================================================
// TIMER FUNCTIONS
// ============================================================================

function startTimedMode(minutes = 10) {
  state.timer.secondsLeft = minutes * 60;
  state.timer.active = true;
  
  const timerEl = document.getElementById('exam-timer');
  timerEl.classList.remove('hidden');
  
  document.querySelector('[data-mode="stop"]')?.classList.remove('hidden');
  
  updateTimerDisplay();
  
  if (state.timer.interval) {
    clearInterval(state.timer.interval);
  }
  
  state.timer.interval = setInterval(() => {
    state.timer.secondsLeft--;
    updateTimerDisplay();
    
    if (state.timer.secondsLeft <= 0) {
      stopTimedMode();
      alert('⏰ Time\'s up!');
      renderCompletionScreen();
    } else if (state.timer.secondsLeft <= 60) {
      timerEl.classList.add('warning');
    }
  }, 1000);
  
  loadPracticeQuestions();
}

function stopTimedMode() {
  state.timer.active = false;
  
  if (state.timer.interval) {
    clearInterval(state.timer.interval);
    state.timer.interval = null;
  }
  
  const timerEl = document.getElementById('exam-timer');
  timerEl.classList.add('hidden');
  timerEl.classList.remove('warning');
  
  document.querySelector('[data-mode="stop"]')?.classList.add('hidden');
}

function updateTimerDisplay() {
  const timerEl = document.getElementById('exam-timer');
  if (!timerEl) return;
  
  const minutes = Math.floor(state.timer.secondsLeft / 60);
  const seconds = state.timer.secondsLeft % 60;
  
  timerEl.textContent = `⏱️ Time: ${minutes}:${seconds.toString().padStart(2, '0')}`;
}

// ============================================================================
// MODE SWITCHING
// ============================================================================

function switchMode(mode) {
  const flashcardMode = document.getElementById('flashcard-mode');
  const practiceMode = document.getElementById('practice-mode');
  
  flashcardMode.classList.add('hidden');
  practiceMode.classList.add('hidden');
  
  document.querySelectorAll('.mode-btn').forEach(btn => {
    btn.classList.remove('active');
  });
  
  if (mode === 'flashcards') {
    flashcardMode.classList.remove('hidden');
    document.querySelector('[data-mode="flashcards"]')?.classList.add('active');
  } else if (mode === 'practice') {
    practiceMode.classList.remove('hidden');
    document.querySelector('[data-mode="practice"]')?.classList.add('active');
  }
}

// ============================================================================
// INITIALIZATION
// ============================================================================

function init() {
  // Load saved progress
  loadProgress();
  updateStreak();
  
  // Set up mode buttons
  document.querySelectorAll('.mode-btn').forEach(btn => {
    btn.addEventListener('click', (e) => {
      const mode = e.currentTarget.dataset.mode;
      
      switch(mode) {
        case 'flashcards':
          switchMode('flashcards');
          break;
        case 'practice':
          switchMode('practice');
          loadPracticeQuestions();
          break;
        case 'hard':
          loadHardQuestions();
          break;
        case 'review':
          loadWrongQuestions();
          break;
        case 'timed':
          startTimedMode(10);
          break;
        case 'refresh':
          refreshQuestionBank();
          break;
        case 'stop':
          stopTimedMode();
          break;
      }
    });
  });
  
  // Set up flashcard controls
  document.getElementById('flashcard-topic')?.addEventListener('change', loadFlashcards);
  document.getElementById('flashcard')?.addEventListener('click', flipCard);
  document.getElementById('prev-btn')?.addEventListener('click', previousCard);
  document.getElementById('next-btn')?.addEventListener('click', nextCard);
  document.getElementById('shuffle-btn')?.addEventListener('click', shuffleFlashcards);
  
  // Set up difficulty filter
  document.querySelectorAll('#flashcard-difficulty .difficulty-chip').forEach(chip => {
    chip.addEventListener('click', (e) => {
      const difficulty = e.currentTarget.dataset.difficulty;
      filterFlashcards(difficulty);
    });
  });
  
  // Set up practice topic selector
  document.getElementById('practice-topic')?.addEventListener('change', loadPracticeQuestions);
  
  // Initialize flashcards
  loadFlashcards();
  switchMode('flashcards');
  
  console.log('✅ GCSE Statistics Mastery initialized');
  console.log(`📊 ${Object.values(QUESTION_BANK).flat().length} practice questions available`);
  console.log(`🎯 Streak: ${state.progress.streak} days`);
}

// Start the app when DOM is ready
if (document.readyState === 'loading') {
  document.addEventListener('DOMContentLoaded', init);
} else {
  init();
}
</script>
</body>
</html>
