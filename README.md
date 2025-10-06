This repo contains some metadata from World of Warships. This repo will hopefully be updated each patch so that each commit represents a game update.

### Comparing Builds

The way that I tend to compare builds a bit easier with tools like [WinMerge](https://winmerge.org/) is to use [jujutsu](https://jj-vcs.github.io) for manging the repo and using its [workspace feature](https://jj-vcs.github.io/jj/latest/cli-reference/#jj-workspace-add) to add another workspace on the earlier commit.

```sh
jj git clone https://github.com/landaire/wows_diff.git
cd wows_diff

# -r @- in the following command is shorthand for --revision <PREVIOUS>.
# use `jj log` to grab a different change ID
jj workspace add ..\wows_diff_prev_patch -r @-
```

After running the above there will be two directories: `wows_diff` and `wows_diff_prev_patch`, both part of the same "repo" but with different versions in different directories.

### Updating

[`wowsunpack`](https://github.com/landaire/wowsunpack) is used for generating data:

```sh
wowsunpack diff-dump --game-dir C:\Path\To\Game .\wows_diff
```
