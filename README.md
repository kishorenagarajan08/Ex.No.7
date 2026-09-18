# Ex.No.7 – Development of a Prompt-Based Application for Personal Needs Using Large Language Models

## Name :Kishore N
## Register No.: 212223230106

# Aim:

To develop a prompt-based application using ChatGPT that assists users in organizing academic and personal activities, demonstrates the progression from basic to advanced prompt design, and uses large language models for practical problem-solving.

# AI Tools Required:

* ChatGPT
* Google Gemini
* Claude

# Explanation:

Prompt-based applications use Large Language Models (LLMs) to understand natural-language instructions and generate useful responses based on user requirements.

In this experiment, a **Student Study Planner and Productivity Assistant** is developed. The application helps a student organize subjects, create study schedules, prioritize assignments, generate revision plans, suggest study breaks, and answer academic productivity-related queries.

The application demonstrates how a simple prompt can gradually be enhanced with user context, constraints, priorities, and output-format requirements to produce more useful responses.

# Selected Application:

## AI-Based Student Study Planner

The assistant is designed to help students with:

* Daily study planning
* Assignment prioritization
* Examination preparation
* Break scheduling
* Productivity suggestions
* Personalized study recommendations
* General academic queries

# PROMPT DESIGN AND EXECUTION

## Stage 1: Basic Prompt

### Prompt:

**"Act as a student productivity assistant. Create a simple study plan for today containing study sessions, breaks, and revision time."**

### Example LLM Response:

**Today's Study Plan**

| Time                | Activity                  |
| ------------------- | ------------------------- |
| 9:00 AM – 10:00 AM  | Study Mathematics         |
| 10:00 AM – 10:15 AM | Short Break               |
| 10:15 AM – 11:15 AM | Study Programming         |
| 11:15 AM – 11:30 AM | Break                     |
| 11:30 AM – 12:00 PM | Revise Important Concepts |

This basic prompt gives a general study timetable without considering personal priorities.

---

# Stage 2: Context-Based Prompt

### Prompt:

**"Act as my personal study planner. I need to study Python programming, Digital Electronics, and Cloud Computing today. I have 4 hours available. Give higher priority to Python programming and include short breaks between sessions."**

### Example LLM Response:

| Duration | Task                | Priority |
| -------- | ------------------- | -------- |
| 90 min   | Python Programming  | High     |
| 10 min   | Break               | -        |
| 60 min   | Digital Electronics | Medium   |
| 10 min   | Break               | -        |
| 50 min   | Cloud Computing     | Medium   |
| 20 min   | Python Revision     | High     |

### Observation:

Adding subjects, available time, and priority information produced a more personalized and practical plan.

---

# Stage 3: Advanced Prompt

### Prompt:

**"Act as an intelligent academic productivity assistant. I have four hours available today. My tasks are Python coding practice, Digital Electronics revision, Cloud Computing notes, and assignment completion. Python coding and the assignment are high priority. Create an optimized timetable using focused study sessions of 45–60 minutes, include short breaks, place difficult tasks earlier, and provide one productivity suggestion at the end."**

### Example LLM Response:

| Time Block  | Activity                     | Priority |
| ----------- | ---------------------------- | -------- |
| 0–60 min    | Python Coding Practice       | High     |
| 60–70 min   | Break                        | -        |
| 70–125 min  | Assignment Completion        | High     |
| 125–135 min | Break                        | -        |
| 135–180 min | Digital Electronics Revision | Medium   |
| 180–190 min | Break                        | -        |
| 190–230 min | Cloud Computing Notes        | Medium   |
| 230–240 min | Quick Review                 | High     |

**Productivity Tip:**
Keep the phone away during high-priority sessions and complete one task before switching to another.

### Observation:

The advanced prompt produced a more structured response because it included:

* User role
* Available time
* Subject priorities
* Session duration
* Difficulty preference
* Output expectations

---

# Procedure:

1. Identify the personal problem to be solved using an LLM.
2. Select academic planning as the application area.
3. Define the main assistant features.
4. Create simple prompts for basic study planning.
5. Refine prompts by adding subjects, priorities, deadlines, and available study time.
6. Generate responses using ChatGPT or other LLM tools.
7. Develop a simple web-based interface to simulate interaction with the assistant.
8. Allow the user to enter tasks and priorities.
9. Generate a study plan based on the entered information.
10. Modify future recommendations according to user preferences.
11. Analyze how prompt refinement improves output quality.

# PROGRAM:

The following program demonstrates a simple browser-based Student Study Planner. It accepts study tasks, assigns priorities, and generates a structured schedule.

```html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">

<title>AI Student Study Planner</title>

<style>
body {
    font-family: Arial, sans-serif;
    background: #f3f6fb;
    margin: 0;
    padding: 30px;
}

.container {
    max-width: 850px;
    margin: auto;
    background: white;
    padding: 25px;
    border-radius: 12px;
    box-shadow: 0 4px 18px rgba(0,0,0,0.08);
}

h1 {
    text-align: center;
    color: #243b67;
}

.description {
    text-align: center;
    color: #666;
    margin-bottom: 25px;
}

.input-row {
    display: flex;
    gap: 10px;
    margin-bottom: 15px;
}

input, select {
    padding: 10px;
    border: 1px solid #ccc;
    border-radius: 6px;
}

input {
    flex: 1;
}

button {
    padding: 10px 16px;
    border: none;
    border-radius: 6px;
    background: #315efb;
    color: white;
    cursor: pointer;
}

button:hover {
    background: #2449cf;
}

.task {
    display: flex;
    justify-content: space-between;
    padding: 10px;
    margin: 6px 0;
    background: #f6f7fa;
    border-radius: 6px;
}

.high {
    border-left: 5px solid #e74c3c;
}

.medium {
    border-left: 5px solid #f39c12;
}

.low {
    border-left: 5px solid #2ecc71;
}

.plan {
    margin-top: 25px;
}

.plan-item {
    background: #eef3ff;
    padding: 12px;
    margin: 8px 0;
    border-radius: 6px;
}

.tip {
    margin-top: 20px;
    padding: 12px;
    background: #fff8df;
    border-radius: 6px;
}
</style>
</head>

<body>

<div class="container">

<h1>AI Student Study Planner</h1>

<p class="description">
Add your subjects or academic tasks and generate a personalized study plan.
</p>

<div class="input-row">

<input
type="text"
id="taskInput"
placeholder="Enter task, e.g. Python coding practice">

<select id="priority">

<option value="high">High Priority</option>
<option value="medium">Medium Priority</option>
<option value="low">Low Priority</option>

</select>

<button onclick="addTask()">Add Task</button>

</div>

<h3>My Tasks</h3>

<div id="taskList"></div>

<div style="margin-top:20px;">

<label>
Available Study Time:
</label>

<select id="hours">

<option value="2">2 Hours</option>
<option value="3">3 Hours</option>
<option value="4" selected>4 Hours</option>
<option value="5">5 Hours</option>
<option value="6">6 Hours</option>

</select>

<button onclick="generatePlan()">
Generate Study Plan
</button>

</div>

<div class="plan">

<h3>Generated Study Plan</h3>

<div id="studyPlan">
Add tasks and click "Generate Study Plan".
</div>

</div>

<div class="tip" id="tip">
Productivity Tip: Complete high-priority activities when your concentration level is highest.
</div>

</div>

<script>

let tasks = [];

function addTask() {

    const taskInput =
        document.getElementById("taskInput");

    const priority =
        document.getElementById("priority").value;

    const text =
        taskInput.value.trim();

    if (text === "") {
        alert("Please enter a study task.");
        return;
    }

    tasks.push({
        task: text,
        priority: priority
    });

    taskInput.value = "";

    displayTasks();
}

function displayTasks() {

    const taskList =
        document.getElementById("taskList");

    taskList.innerHTML = "";

    tasks.forEach((item, index) => {

        const taskDiv =
            document.createElement("div");

        taskDiv.className =
            "task " + item.priority;

        taskDiv.innerHTML = `
            <span>${item.task}</span>

            <span>
            ${item.priority.toUpperCase()}
            <button onclick="removeTask(${index})">
            Remove
            </button>
            </span>
        `;

        taskList.appendChild(taskDiv);
    });
}

function removeTask(index) {

    tasks.splice(index, 1);

    displayTasks();
}

function generatePlan() {

    if (tasks.length === 0) {

        alert("Please add at least one task.");

        return;
    }

    const totalHours =
        parseInt(
        document.getElementById("hours").value
        );

    const totalMinutes =
        totalHours * 60;

    const priorityValue = {
        high: 3,
        medium: 2,
        low: 1
    };

    tasks.sort(
        (a, b) =>
        priorityValue[b.priority]
        -
        priorityValue[a.priority]
    );

    let breakTime =
        (tasks.length - 1) * 10;

    let availableMinutes =
        totalMinutes - breakTime;

    let sessionLength =
        Math.floor(
        availableMinutes / tasks.length
        );

    const studyPlan =
        document.getElementById("studyPlan");

    studyPlan.innerHTML = "";

    tasks.forEach((item, index) => {

        const block =
            document.createElement("div");

        block.className =
            "plan-item";

        block.innerHTML =
        `<strong>Session ${index + 1}</strong><br>
        ${item.task}<br>
        Duration: ${sessionLength} minutes<br>
        Priority: ${item.priority}`;

        studyPlan.appendChild(block);

        if (index < tasks.length - 1) {

            const breakBlock =
                document.createElement("div");

            breakBlock.className =
                "plan-item";

            breakBlock.innerHTML =
                "<strong>Break:</strong> 10 minutes";

            studyPlan.appendChild(
                breakBlock
            );
        }

    });

    generateTip();
}

function generateTip() {

    const tips = [

        "Start with your most difficult task when your concentration is highest.",

        "Keep your phone away during focused study sessions.",

        "Review key concepts for five minutes after every major study session.",

        "Use short breaks to walk, stretch, or drink water.",

        "Break large assignments into smaller achievable tasks."

    ];

    const randomTip =
        tips[
        Math.floor(
        Math.random() * tips.length
        )
        ];

    document.getElementById("tip")
        .innerHTML =
        "<strong>AI Productivity Tip:</strong> "
        + randomTip;
}

</script>

</body>
</html>
```

# Sample Input:

Tasks entered by the user:

* Complete Python programming exercise – High Priority
* Prepare Digital Electronics notes – Medium Priority
* Complete laboratory record – High Priority
* Revise Cloud Computing concepts – Low Priority

Available study time:

**4 Hours**

# Expected Output:

<img width="1158" height="777" alt="image" src="https://github.com/user-attachments/assets/ad09f353-1e7a-4aa1-9991-9db8148a42ba" />


The application arranges high-priority tasks first and distributes the available study time between the selected activities.

Example:

| Session | Activity                             | Duration |
| ------- | ------------------------------------ | -------- |
| 1       | Complete Python Programming Exercise | 53 min   |
| Break   | Short Break                          | 10 min   |
| 2       | Complete Laboratory Record           | 53 min   |
| Break   | Short Break                          | 10 min   |
| 3       | Prepare Digital Electronics Notes    | 53 min   |
| Break   | Short Break                          | 10 min   |
| 4       | Revise Cloud Computing Concepts      | 53 min   |

**Suggested Productivity Tip:**
Keep your phone away during focused study sessions.

# Personalization and Preference Adaptation:

The assistant can be improved by remembering user preferences such as:

* Preferred study duration
* Frequently studied subjects
* Preferred break duration
* Most productive study time
* Difficult subjects
* Preferred learning method

For example, if the user repeatedly prefers 50-minute study sessions with 10-minute breaks, future prompts can automatically include this preference.

# PROMPT PROGRESSION ANALYSIS:

| Prompt Type     | Information Provided                              | Output Quality    |
| --------------- | ------------------------------------------------- | ----------------- |
| Simple Prompt   | General study request                             | Basic             |
| Context Prompt  | Subjects and available time                       | Personalized      |
| Priority Prompt | Tasks, priority and time                          | More practical    |
| Advanced Prompt | Priority, difficulty, session duration and format | Highly structured |

# Observations:

* Simple prompts produced general responses.
* Adding specific requirements improved the usefulness of the generated output.
* Giving priorities helped the LLM arrange important activities first.
* Defining available time prevented unrealistic schedules.
* Specifying the desired output format made the response easier to understand.
* Persona-based prompting helped the LLM behave like an academic productivity assistant.
* LLM-generated recommendations can be modified easily when user requirements change.

# Advantages:

* Reduces time spent manually creating study schedules.
* Allows interaction using natural language.
* Generates personalized plans.
* Can easily adapt to changing user requirements.
* Helps prioritize important academic activities.
* Demonstrates practical applications of prompt engineering.

# Limitations:

* LLM responses depend strongly on the clarity of the prompt.
* Generated schedules may require manual verification.
* Actual reminders require integration with calendar or notification services.
* User preference memory requires storage or database support.
* AI recommendations should not completely replace the user's own judgment.

# Conclusion:

The experiment demonstrated the development of a prompt-based Student Study Planner using Large Language Models. Different levels of prompt design were tested, starting from simple instructions and progressing toward contextual and constraint-based prompts. The results showed that detailed prompts containing priorities, available time, and clear output requirements generated more personalized and useful responses.

# Result:

A prompt-based Student Study Planner was successfully designed and implemented. The experiment demonstrated how Large Language Models can be used to organize academic tasks, generate personalized study schedules, provide productivity suggestions, and adapt responses according to user requirements.
