# Individual Project — LLMs & You

A starting point for your semester project. Clone it, rename it, and make it
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

**1. Make your own copy.** Use the green **Use this template** button on
GitHub — do not fork. A fork stays linked to this repository; a template copy
is yours.

**2. Clone it and set up an environment.**

```bash
git clone https://github.com/YOUR-USERNAME/YOUR-PROJECT.git
cd YOUR-PROJECT

python3 -m venv .venv
source .venv/bin/activate        # Windows: .venv\Scripts\activate
pip install -r requirements.txt
```

**3. Set your API key.** It goes in an environment variable, never in a file.

```bash
export ANTHROPIC_API_KEY='sk-ant-...'      # Windows PowerShell: $env:ANTHROPIC_API_KEY='sk-ant-...'
```

That export lasts until you close the terminal. To make it permanent, add the
line to `~/.zshrc` or `~/.bashrc`. If you get `AuthenticationError`, this is
what is wrong.

**4. Turn on the credential guard.** Once per clone:

```bash
git config core.hooksPath .githooks
```

This blocks a commit that contains something shaped like an API key. A key
pushed to GitHub is scraped within minutes, and deleting it in the next commit
does not help — it stays in the history.

**5. Check that it works.**

```bash
python -m project.main "Say hello in exactly five words."
```

---

## What is in here

| Path | What it is for |
|:---|:---|
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
plan to delete. See step 4.

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
