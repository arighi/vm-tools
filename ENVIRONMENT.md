# git config (`~/.gitconfig`)

```
[user]
	email = <YOUR EMAIL>
	name = <YOUR NAME>
[color]
	diff = auto
	status = auto
	branch = auto
	interactive = auto
[http]
	sslVerify = 0
[color "diff"]
	whitespace = red reverse
[gc]
	auto = 0
[help]
	autocorrect = -1
[alias]
	l = log --oneline
	lg = log --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit --date=relative
	lp = log -p
	log-author = log --oneline --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset'
	latr = branch --sort=committerdate
	format-commit = "!sh -c 'git log --pretty=format:\"%h (\\\"%s\\\")\" $0~1..$0'"
	last-changes = "!f() { git log --oneline $@ $(git reflog --oneline | head -2 | cut -d\" \" -f1 | tac | tr \"\\n\" \" \" | sed \"s/ /../\"); }; f"
	dc = describe --contains
	fp = format-patch -N -M
	b = branch -v
	summary = diff -C --dirstat=5 --cumulative
	contains = tag --contains
	push = !git-pull --rebase && git-push
	who = !git shortlog -s -n
	ours = "!f() { git checkout --ours -- \"${@:-.}\"; git add -u \"${@:-.}\"; }; f"
	theirs = "!f() { git checkout --theirs -- \"${@:-.}\"; git add -u \"${@:-.}\"; }; f"
	tagdate = tag --sort=creatordate
	lasttag = !sh -c 'git tag --sort=creatordate | tail -1'
	stable = log --oneline --grep="stable@"
	merge-find = "!sh -c 'commit=$0 && branch=${1:-HEAD} && (git rev-list $commit..$branch --ancestry-path | cat -n; git rev-list $commit..$branch --first-parent | cat -n) | sort -k2 -s | uniq -f1 -d | sort -n | tail -1 | cut -f2'"
	merge-show = "!sh -c 'merge=$(git merge-find $0 $1) && [ -n \"$merge\" ] && git show $merge'"
	merge-log-short = "!f() { git log --pretty=oneline \"$1^..$1\"; }; f"
	merge-log = "!f() { git log \"$1^..$1\"; }; f"
	bisect-fixed = bisect bad
	bisect-unfixed = bisect good
	distclean = "!f() { git clean -xdf && git submodule foreach --recursive git clean -xdf; }; f"
[push]
	default = current
[merge]
	tool = vimdiff
[branch]
	autosetuprebase = always
[commit]
	gpgsign = false
[pretty]
	fixes = Fixes: %h (\"%s\")
[url "git+ssh://arighi@git.launchpad.net/"]
        pushinsteadof = lp:
	pushinsteadof = git://git.launchpad.net/
        insteadof = lps:
[url "git://git.launchpad.net/"]
        insteadof = lp:
[url "git+ssh://arighi@git.launchpad.net/~fips-cc-stig"]
        insteadof = lp:~fips-cc-stig
        insteadof = git://git.launchpad.net/~fips-cc-stig
```

# bash prompt (`~/.bashrc`)

```
export DEBFULLNAME='<YOUR NAME>'
export DEBEMAIL='<YOUR EMAIL>'

# some more ls aliases
alias ll='ls -l'
alias la='ls -A'
alias l='ls -CF'

export QUILT_DIFF_OPTS="-p"
export QUILT_DIFF_ARGS="--color=auto"
export QUILT_PATCHES=debian/patches

alias fdr="fakeroot debian/rules"
alias dr="debian/rules"
```
