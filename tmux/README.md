# `tmux` Scripts

The scripts in this group are mainly geared towards automating `tmux` management in a particular way.

All scripts in this directory depend on having `tmux` installed on the host.

## `fzfw`

**Dependencies**: `fd, fzf`

`fzfw` allows users to fuzzy-find and open the directories that are related with their tmux sessions in separate tmux windows.

This functionality also helps users organize their directories by their contents.

It's easier to explain with pseudocode.
Here is an example scenario:

```bash
# "work" and "personal" directories are defined to store work and personal related subdirectories (e.g. Git repositories).
work_projects_path="$HOME/work"
personal_projects_path="$HOME/personal"

# The subdirectories.
mkdir -p "$work_projects_path"/project{1..4}
mkdir -p "$personal_projects_path"/project{1..4}

# The corresponding tmux sessions.
tmux new -s work
tmux new -s personal

# User attaches to the session "work" to deal with work projects.
tmux attach -t work

# Using fzfw in the work session allows the user to search any directory that belongs "to $HOME/work".
# Notice how the project directories created under "$HOME/personal" are not shown in the list.
fzfw
# "$HOME/work/project1"
# "$HOME/work/project2"
# "$HOME/work/project3"
# "$HOME/work/project4"

# Selecting project4 from the list provided by fzfw above.
selected_dir="$HOME/work/project4"

# fzfw opens project4 in a new window, titled "project4".
tmux list-windows
# 0: bash
# 1: project4
```

If the directory structure is designed similar to the given example above, then `fzfw` makes it really a great experience to create tmux windows and switch between projects.

The _automation_ aspect of the script can be felt better when the user is located in a deeply nested directory and wants to open up a new tmux window in a completely different place.
