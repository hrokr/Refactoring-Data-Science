# Lesson 0 - Visual Studio Code

In truth, this could be Lesson 1 with Lesson 0 being something like "Learn To Type", "The Command Line Interface and You", or any of a number of math topics. But we have to assume some sort of familiarity or competency _somewhere_ so this is as good of a spot as any.

For now, Visual Studio Code (or VS Code) is a pretty popular choice for a text editor. It's lightweight, extensible and does most of you might need, plus a lot of what you might not need but could come to. It's used in industry -- Facebook announced [this week](https://www.techspot.com/news/82862-facebook-moving-microsoft-visual-studio-code-internal-development.html) they were switching to VS Code instead of Nuclide (whatever that is) and Emacs(!?!).

Importantly, VS Code has some additional python goodness. So, let's focus on that first. 

- Python (the one from Microsoft)
- Anaconda Extension Pack
- Code Runner

Others that aren't python specific but damn useful

- Markdown lint
- Markdown+Math
- Rainbow CSV

## Let's talk about all that lint(ing)
Linting is getting your code to have a unified style. Because python has came about with both the  [pep-8](https://www.python.org/dev/peps/pep-0008/) and [pep-20 (aka the zen of python)](https://www.python.org/dev/peps/pep-0020/) early on (they're in the 500's now) python has had a fairly clear vision of what good code should look like. So, linters usually follow pep-8 some even give you options in the event you work for a company that doesn't _quite_ follow pep-8.

An interesting thing or two about linters:

- People _really_ don't like it when their code is corrected for style by a human but they're fine if the corrections come from a program. So use a linter (or don't fight using one) and enjoy a bit less friction.

- If you aren't a control freak, [Black](https://github.com/psf/black) kicks ass. It's by the Python Software Foundation, so think of it as being from the font of python. What Black does is format your code without asking you to say yes to everything you'd end up saying yes to anyway. It's very opinionated. Here is how you do it:
    * to install: ```pip install black```
    * to use it on a file: ```black {name of file}```
    * when it's done it will look something like:

        ```python
        reformatted sentdex1.py
        All done! ✨ 🍰 ✨
        1 file reformatted.
        ```

