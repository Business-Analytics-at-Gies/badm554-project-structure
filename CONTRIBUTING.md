# Changing shared files

`members/<your-netid>/` is yours alone. Everything else (the project folders, this file, the README) is shared, so
two people can collide. Change shared files this way:

1. **Pull first.** In VS Code, Sync; or `git pull`.
2. **Make a branch** named for the change: `git switch -c reorganize-folders`.
3. **Make the change and commit it** on the branch. Keep one change per branch.
4. **Push and open a pull request** on GitHub: `git push -u origin reorganize-folders`, then *Compare & pull request*.
   Say in one or two sentences what changed and why.
5. **A teammate reviews and merges it.** Then everyone pulls.

If two people changed the same lines, GitHub shows a conflict on the pull request. Decide together which version
stays; the course page [Submitting with a GitHub Repo](https://canvas.illinois.edu/courses/70435/pages/submitting-with-a-github-repo)
has the Fresh Clone Rule if git gets into a state you do not understand.
