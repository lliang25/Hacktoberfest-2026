# Hacktoberfest-2026
DataTrap — Question the Data, Not Just the Answers
Most AI tools help you analyze data. DataTrap helps you question the analysis.

DataTrap is a hackathon prototype that helps people spot data-quality issues and potentially misleading statistical interpretations in CSV datasets. Upload data, inspect evidence-backed warnings, and explore how outliers or missing values may change your conclusions.

Status: 🚧 In development — Hacktoberfest 2026
The problem
Charts and correlations can look convincing even when the underlying data have missing values, extreme observations, or other limitations. DataTrap makes those limitations visible and understandable before users draw conclusions.
Our MVP
- CSV upload: Import a dataset and preview its columns and rows.
- Data-quality scan: Count missing values and flag potential outliers using the interquartile range (IQR) method.
- Correlation exploration: Calculate correlations between numeric columns when there is sufficient valid data, with a clear correlation ≠ causation reminder.
- Visual explanations: Show charts and compare analyses with and without flagged outliers as a sensitivity check (without claiming outliers must be removed).
- AI explanations (planned): Summarize computed findings in plain English, using only results the app actually calculates.
Important limitation: A CSV alone generally cannot establish selection bias, causal relationships, or whether an outlier is an error. DataTrap flags questions for further investigation rather than making definitive judgments.
Tech stack
Layer	Tool
Development	Cursor
Language	Python 3.10+
Web app	Streamlit
Data analysis	pandas
Visualization	Streamlit charts (optional: Plotly)
AI explanation	Optional; API/provider TBD by team
Collaboration	Git + GitHub


Suggested project structure
datatrap/
├── app.py                # Streamlit UI and CSV upload
├── analyzer.py           # Data-quality and statistics functions
├── ai_explainer.py       # Optional AI explanation integration
├── requirements.txt      # Python dependencies
├── .gitignore            # Files that should not be committed
├── .env.example          # Optional API configuration template (no secrets)
├── sample_data/          # Non-sensitive example CSV datasets
├── tests/                # Tests for analysis functions
└── README.md
The structure above is a plan, not a claim that all files already exist. Create them as features are implemented.
Getting started locally
1. Install the tools
Install Python 3.10+, Git, and Cursor.
2. Clone the shared repository
In Cursor, open a terminal and run:
git clone https://github.com/OWNER/REPO.git
cd REPO
Replace OWNER/REPO with your team's actual GitHub repository address. Or, in Cursor, use Clone Repository and paste the URL.
3. Create a virtual environment
macOS / Linux:
python3 -m venv .venv
source .venv/bin/activate
Windows (PowerShell):
py -m venv .venv
.venv\Scripts\Activate.ps1
If PowerShell blocks activation, open Command Prompt and use .venv\Scripts\activate.bat instead.
4. Install dependencies
Once requirements.txt exists:
python -m pip install -r requirements.txt
For an initial Streamlit/Pandas MVP, your requirements.txt can start with:
streamlit
pandas
5. Run DataTrap
Once app.py exists:
python -m streamlit run app.py
Open the local URL shown in the terminal (usually http://localhost:8501).
If the app files have not been created yet: Start with the Cursor prompt in the team chat to generate a basic app.py and analyzer.py, then commit those files. A README alone does not launch a web app.

Four-person team plan
Role	Ownership	Suggested files
A — Data analysis	Missing values, IQR outliers, correlations, validation	analyzer.py, tests/
B — UI / frontend	CSV uploader, dashboard, plots, visual comparison	app.py
C — AI explanations	Optional AI integration, prompt safeguards, plain-English summaries	ai_explainer.py, .env.example
D — Integration + demo	Repository setup, QA, sample CSVs, docs, pitch	README.md, sample_data/, tests/


Decide together who owns integration and the final submission. Avoid editing the same file simultaneously when possible.
GitHub collaboration workflow
One-time setup (repo owner)
1. Create a GitHub repository, e.g. datatrap.
2. Upload or commit the starter files to its main branch.
3. In Settings → Collaborators, invite teammates. They must accept the invitations.
4. Share the exact repository URL with everyone.
For each teammate (each feature)
Start with an updated main:
git switch main
git pull origin main
Create your own feature branch:
git switch -c feature/data-analysis
Use a different branch name per task, e.g. feature/dashboard, feature/ai-explanations, or docs/demo.

After editing your assigned files:
git status
git add <files-you-changed>
git commit -m "Add initial data analysis"
git push -u origin feature/data-analysis
Replace <files-you-changed> with actual file paths (for example, analyzer.py tests/). Review git status before staging, especially when API keys are involved.

Open a Pull Request (PR): On GitHub, click Compare & pull request, describe what you changed and how you tested it, and request a teammate's review. Merge into main after checking that the app runs.

After the PR is merged, update main before creating your next branch:
git switch main
git pull origin main
Team rule: No direct pushes to main unless the team explicitly agrees during a deadline emergency. Avoid force-pushing shared branches.
Definition of done — first demo
- [ ] App starts using python -m streamlit run app.py.
- [ ] A user can upload a CSV and preview the data.
- [ ] Missing values are correctly counted.
- [ ] IQR outlier findings show the columns and thresholds involved.
- [ ] Correlations use appropriate numeric data and avoid causal claims.
- [ ] At least one chart changes when the selected data changes.
- [ ] Example data are included for a reproducible demo.
- [ ] README accurately reflects what has actually shipped.
- [ ] No .env, API keys, private datasets, or virtual environments are committed.
Demo outline (approximately 2 minutes)
1. Problem (20 sec): A persuasive chart can hide important limitations.
2. Upload (20 sec): Load a small CSV with missing values and an extreme observation.
3. Detect (40 sec): Show the flagged issues and how DataTrap computed them.
4. Compare (25 sec): Illustrate how conclusions may shift when exploring outlier sensitivity.
5. Explain (15 sec): Summarize why these warnings matter; show AI explanations only if working.
Security and responsible analysis
- Keep credentials in a local .env file, never in source code or GitHub.
- Commit an .env.example with variable names only, if the app needs API keys.
- Use public or synthetic sample datasets; do not upload private student or customer information.
- Do not present AI-generated commentary as independently verified statistical evidence.
- Validate calculations with a small dataset before relying on the AI explanation layer.
Next steps
1. Assign roles and invite all teammates to GitHub.
2. Create a minimal Streamlit app with a CSV uploader.
3. Implement and test the data-quality checks.
4. Add charts and the outlier sensitivity comparison.
5. Add optional AI explanations if time and API access permit.
6. Rehearse the demo and submit according to the hackathon's official instructions.
Built by the DataTrap team at Hacktoberfest 2026.
