# Individual Project — LLMs & You

A starting point for your semester project. Copy it, rename it, and make it
yours.

This template is deliberately **empty of content and opinionated about
process.** It does not contain a project. It contains the structure that the
projects which go well in this course all turn out to have, and the three
practices that separate them from the ones that do not:

1. **Your prompts are source code.** They live in `prompts/`, they are edited
   deliberately, and their history is readable. See [`PROMPTING.md`](PROMPTING.md).
2. **Your decisions are written as you make them.** Why you chose something goes
   in `docs/adr/`; what actually changed goes in [`CHANGELOG.md`](CHANGELOG.md).
   Both are graded — see the
   [ADR guide](https://Nalaquq.github.io/llms-and-you/guides/writing-adrs/).
3. **Your claims are measured.** A change that "seems better" is a guess until
   `evals/` says otherwise.

---

## Getting started

**You need a browser and a GitHub account. Nothing is installed.** That is the
supported path for everything this course grades. Running the code on your own
machine is [optional, and further down](#running-it-on-your-own-machine-optional).

**1. Make your own copy.** At the top of
[this repository's page](https://github.com/Nalaquq/llms-and-you-project), press
**Use this template**, then **Create a new repository**. If you cannot find the
button, [this link](https://github.com/Nalaquq/llms-and-you-project/generate)
opens the same form. Name it what you like and set it **Public**.

Do not fork. A fork stays linked to this repository; a template copy is yours,
with a clean history that starts at your first commit.

**2. Make your first commit, in the browser.** Open [`TODO.txt`](TODO.txt) in
your copy, press the **pencil icon** at the top right of the file, delete the
examples and type something of your own. Scroll down, write a real sentence in
the commit message box, and press **Commit changes**.

That button does exactly what `git commit` does. Every file in this repository
can be edited the same way, and that is all the Git this course requires.
`TODO.txt` is the running list of what the next version of your prompt has to
do. An hour after you have the thought, you no longer have the thought.

**3. Write decisions down as you make them.** Copy
[`docs/adr/template.md`](docs/adr/template.md) into a new file in `docs/adr/`
for each one, using **Add file → Create new file**, and add a line to
[`CHANGELOG.md`](CHANGELOG.md) when something changes. Both are graded; the
[ADR guide](https://Nalaquq.github.io/llms-and-you/guides/writing-adrs/) says
what a good one contains.

**4. Keep your prompts in `prompts/`,** one file per prompt, each with the
header [`prompts/example-classify.md`](prompts/example-classify.md) shows. A
prompt you tried in a chat window and liked is not saved until it is a file here.

**5. Put your evaluation set in `evals/`.** The Week 7 lab notebook ends by
downloading a file called `cases.jsonl`. Open the `evals/` folder in your copy,
choose **Add file → Upload files**, and upload it. It replaces the five example
cases that ship with the template, which is what you want. Add a case every time
you find a new failure; [`evals/README.md`](evals/README.md) says why.

The course's [setup guide](https://Nalaquq.github.io/llms-and-you/guides/setup/)
walks through steps 1 and 2 with more explanation.

---

## Running it on your own machine — optional

Skip this section and you will not miss a single graded thing. It is here for
when you want `evals/run_eval.py` to run your whole test set against a model
from a terminal. That takes Python, Git, and an Anthropic API key of your own.

Every command below is given twice, once for each platform, including where the
two are identical. Use the half that matches your machine and ignore the other;
mixing them is the most common way this goes wrong.

**1. Get your copy onto your machine.** Clone the repository you made above:

**macOS / Linux**

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-PROJECT.git
cd YOUR-PROJECT
```

**Windows (PowerShell)**

```powershell
git clone https://github.com/YOUR-USERNAME/YOUR-PROJECT.git
cd YOUR-PROJECT
```

Do not clone *this* repository directly; that points at one you cannot push to.

**2. Set up an environment.** This is the step that genuinely differs by platform.

**macOS / Linux**

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

**Windows (PowerShell)**

```powershell
python -m venv .venv
.venv\Scripts\Activate.ps1
pip install -r requirements.txt
```

If PowerShell says `running scripts is disabled on this system`, run this once
in the same window and then activate again:

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

Your prompt starts with `(.venv)` when it is active. Activate again every time
you open a new terminal.

**3. Set your API key.** It goes in an environment variable, never in a file.

**macOS / Linux**

```bash
export ANTHROPIC_API_KEY='sk-ant-...'
```

Lasts until you close the terminal. To make it permanent, add that line to
`~/.zshrc` or `~/.bashrc` and open a new one.

**Windows (PowerShell)**

```powershell
$env:ANTHROPIC_API_KEY = 'sk-ant-...'
```

Lasts until you close the window. To make it permanent:

```powershell
[Environment]::SetEnvironmentVariable('ANTHROPIC_API_KEY', 'sk-ant-...', 'User')
```

Then open a new terminal — the one you typed it in will not see it.

If you get `AuthenticationError`, this is what is wrong. Check the key is set in
*this* terminal: `echo $ANTHROPIC_API_KEY` on macOS and Linux,
`echo $env:ANTHROPIC_API_KEY` on Windows.

**4. Turn on the credential guard.** Once per clone.

**macOS / Linux**

```bash
git config core.hooksPath .githooks
```

**Windows (PowerShell)**

```powershell
git config core.hooksPath .githooks
```

This blocks a commit that contains something shaped like an API key. A key
pushed to GitHub is scraped within minutes, and deleting it in the next commit
does not help — it stays in the history.

**5. Check that it works,** with the virtual environment active.

**macOS / Linux**

```bash
python -m project.main "Say hello in exactly five words."
```

**Windows (PowerShell)**

```powershell
python -m project.main "Say hello in exactly five words."
```

---

## What is in here

| Path | What it is for |
|:---|:---|
| `TODO.txt` | What the next version of your prompt needs to do. Start using it in week one. |
| `PROMPTING.md` | The practices this course grades. Read this first. |
| `prompts/` | Your prompts, as versioned files. One per prompt, not one per project. |
| `src/project/` | Your code. `client.py` is written for you; the rest is yours. |
| `evals/` | Your test set. Start it in week one, not the week before it is due. |
| `docs/adr/` | Your decision log — why you chose things. Graded. |
| `CHANGELOG.md` | What changed and when. Graded alongside the ADRs. |
| `tests/` | Ordinary tests, for the parts that are ordinary code. |

Rename `src/project/` to something that describes your project, and update the
`name` in `pyproject.toml` to match.

---

## The rules that are not obvious

**Do not put a key in your code.** Not even temporarily, not even in a file you
plan to delete. If you work in a terminal, turn on the credential guard in
the optional section above.

**Do not commit model output as if it were a result.** An output is evidence of
one run. A result is what `evals/` reports across your whole test set.

**Do not adjust `temperature`.** Nearly every prompt engineering tutorial online
tells you to. On current frontier models that parameter has been removed and
sending it returns an error. Use `effort` instead — see `PROMPTING.md`. When
sources contradict, [the API reference](https://docs.claude.com/en/api/overview)
wins.

**Cite AI use.** The course policy applies to your project exactly as it applies
to everything else, and the two ways to fail it are in
[the syllabus](https://Nalaquq.github.io/llms-and-you/syllabus/#using-ai).
