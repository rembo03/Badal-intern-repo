Terminal Setup & Basic Command-line Knowledge (Mac)
This document contains my reflections and learnings after setting up and using my terminal client on macOS.

✅ 1. Terminal Client I Chose
I am using iTerm2 + zsh on my Mac.

Why I chose iTerm2?
It is faster and more customizable than the default macOS Terminal

Supports split panes, profiles, and better color schemes

Works perfectly with zsh, the default Mac shell

Supports plugins and themes that improve productivity

🎨 2. Customizations I Made
I set up the following customizations to improve my terminal workflow:

Installed Oh My Zsh for managing zsh easily

Applied the Powerlevel10k theme for a modern, clean UI

Added helpful plugins:

git — shows branch & status

zsh-autosuggestions — auto-complete suggestions

zsh-syntax-highlighting — syntax colors

Customized terminal colors

Added quick aliases to save time:

bash
Copy code
alias gs="git status"
alias ga="git add ."
alias gc="git commit -m"
alias gp="git push"
These changes make my terminal quicker, cleaner, and more efficient.

🧠 3. Most Useful Command I Learned Today
ls – List files and folders
bash
Copy code
ls
ls -la
Why it’s useful:
It helps me quickly see which files exist, including hidden files (ls -la). This is something I use constantly while navigating projects.

(You can replace this with your real choice— like cd, mkdir, grep, or git commands — but this one is safe and common.)

📝 4. Reflection
Working with the terminal on Mac feels much smoother after customizing it. I realised:

iTerm2 + zsh provides a cleaner, more powerful environment than the default terminal

Short commands and aliases reduce repetitive typing

Git becomes faster when used directly in the terminal

Auto-suggestions and syntax highlighting help me avoid mistakes

A well-set terminal boosts development speed and confidence

Overall, setting up a personalized terminal significantly improves productivity and makes day-to-day development easier.

📤 5. Commit & Push 