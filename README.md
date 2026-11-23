# CPU Scheduling Visualizer

An interactive web application that shows how an operating system schedules processes on the CPU. Enter your own processes, choose an algorithm, and watch the CPU, ready queue and Gantt chart update tick by tick.

**Live demo:** `https://<your-username>.github.io/<repo-name>/`

---

## Features

- Six scheduling algorithms: FCFS, SJF, SRTF, Priority (preemptive and non-preemptive), and Round Robin with an adjustable time quantum
- Editable process table (arrival time, burst time, priority) with add, remove, random and sample sets
- Animated simulation with Play, Pause, Step, Reset and a speed slider
- Live CPU box, ready queue and Gantt chart
- Per-process metrics: completion, turnaround, waiting and response time
- Summary metrics: average waiting, turnaround and response time, CPU utilization, throughput and context switches
- Comparison table that runs all algorithms on the same processes and highlights the lowest average waiting time
- Responsive layout with automatic light and dark theme

---

## Technologies Used

This project uses only standard web technologies. There are no frameworks, libraries or backend, so the whole app is a single file.

| Technology | Where it lives | What it is used for |
|---|---|---|
| **HTML5** | `<body>` | Page structure: process table, input fields, buttons, CPU box, ready queue, Gantt chart container and results tables |
| **CSS3** | `<style>` | Styling and layout |
| &nbsp;&nbsp;Flexbox | | Aligns the controls, CPU box, ready queue and Gantt cells |
| &nbsp;&nbsp;CSS variables | | Colour tokens that allow theming |
| &nbsp;&nbsp;Media queries (`prefers-color-scheme`) | | Automatic light and dark mode |
| &nbsp;&nbsp;`overflow-x: auto` | | Lets wide tables and long Gantt charts scroll on small screens |
| **JavaScript (ES6)** | `<script>` | All application logic |

### How the JavaScript is organised

| Part | Purpose |
|---|---|
| `simulate()` | The scheduling engine. It runs the chosen algorithm one time unit at a time and records which process ran and which were waiting. |
| `draw()` | Renders the Gantt chart, time ruler, CPU box and ready queue for the current moment. |
| `results()` | Fills the per-process results table and the summary statistics. |
| `compare()` | Runs all six algorithms on the same processes and fills the comparison table. |
| `setInterval` | Drives the animation. The speed slider changes the delay between ticks. |
| DOM manipulation and event listeners | Reads user input, updates the page, and handles button clicks. |

### Tools and hosting

| Tool | Purpose |
|---|---|
| **Git and GitHub** | Version control and source hosting |
| **GitHub Pages** | Free static hosting, so anyone can open the app from a link |

---

## Algorithms Implemented

| Algorithm | Type | Rule for picking the next process |
|---|---|---|
| FCFS | Non-preemptive | Earliest arrival first |
| SJF | Non-preemptive | Shortest burst time first |
| SRTF | Preemptive | Shortest remaining time first, checked every tick |
| Priority (NP) | Non-preemptive | Lowest priority number first |
| Priority (P) | Preemptive | Lowest priority number first, checked every tick |
| Round Robin | Preemptive | Each process runs for at most one time quantum, then goes to the back of the queue |

Ties are broken by arrival time, then by process number.

---

## Metrics Explained

| Metric | Formula |
|---|---|
| Turnaround time | Completion time − Arrival time |
| Waiting time | Turnaround time − Burst time |
| Response time | First CPU time − Arrival time |
| CPU utilization | Busy time units ÷ Total time units × 100 |
| Throughput | Number of processes ÷ Total time units |
| Context switches | Number of times the CPU moves from one process directly to a different one |

---

## How to Run

**Locally**
1. Download `index.html`.
2. Double-click it, or right-click and choose **Open with** your browser.

No installation, build step or internet connection is needed.

**On GitHub Pages**
1. Upload `index.html` to a public repository.
2. Go to **Settings → Pages**, set the source to **Deploy from a branch**, choose **main** and **/ (root)**, then save.
3. Open the link shown on that page.

---

## How to Use

1. Choose an algorithm from the dropdown. For Round Robin, set the time quantum.
2. Edit the process table, or click **Random set** or **Sample set**.
3. Press **Play** to animate, or **Step** to advance one time unit at a time.
4. Read the metrics when the run finishes, and use the comparison table to see how the algorithms differ.

---

## Project Structure

```
.
├── index.html   # the complete app: HTML, CSS and JavaScript
└── README.md
```

---

## Possible Improvements

- Multilevel feedback queue and HRRN algorithms
- I/O bursts and blocked states
- Export results as CSV or an image of the Gantt chart
- Step-back (rewind) control

---

## License

Free to use for learning and academic projects.
