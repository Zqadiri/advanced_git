## Step 1 : Initialize the Repo

```bash
# Create a new sample project folder and navigate to it.
mkdir ex1
cd ex1

# git status command shows that the directory is not a git repository yet. 
git status
> fatal: not a git repository (or any parent up to mount point /Users)
Stopping at filesystem boundary (GIT_DISCOVERY_ACROSS_FILESYSTEM not set).

# Use git init to initialize it as a repository.
git  init 
> Initialized empty Git repository in /Users/zqadiri/Desktop/ex1/.git/
```

## Step 2 : First Commit

```bash
# Create a new document
echo 'New Document!' > doc.txt

# stage it for a commit
git add doc.txt

# commit it to your repository
git commit -m "Initial commit"
[master (root-commit) 4816da9] Initial commit
 1 file changed, 1 insertion(+)
 create mode 100644 doc.txt
```

## Step 3 : View the .git folder

add `tree` command  : `brew install tree`

```bash
tree .git
> 
.git
├── COMMIT_EDITMSG
├── HEAD
├── config
├── description
├── hooks
│   ├── applypatch-msg.sample
│   ├── commit-msg.sample
│   ├── fsmonitor-watchman.sample
│   ├── post-update.sample
│   ├── pre-applypatch.sample
│   ├── pre-commit.sample
│   ├── pre-push.sample
│   ├── pre-rebase.sample
│   ├── pre-receive.sample
│   ├── prepare-commit-msg.sample
│   └── update.sample
├── index
├── info
│   └── exclude
├── logs
│   ├── HEAD
│   └── refs
│       └── heads
│           └── master
├── objects
│   ├── 18
│   │   └── 29caca48f0d85fad71afa0133aa69859061c24
│   ├── 48
│   │   └── 16da99373f0dcdd037c8a3496b3009bd861134
│   ├── a9
│   │   └── 0412bd3b15c140a02512ec586b1e39664f03a7
│   ├── info
│   └── pack
└── refs
    ├── heads
    │   └── master
    └── tags
```

## Step 4 : inspect the objects

`git cat-file <option> <object>`

git-cat-file - Provide content or type and size information for repository objects

```bash
tree .git/objects
> 
.git/objects
├── 18
│   └── 29caca48f0d85fad71afa0133aa69859061c24
├── 48
│   └── 16da99373f0dcdd037c8a3496b3009bd861134
├── a9
│   └── 0412bd3b15c140a02512ec586b1e39664f03a7
├── info
└── pack

```

`git cat-file -p <hash>`

to read the content ( or blob ) of a git object

```bash
git cat-file -p  4816da
> 
tree a90412bd3b15c140a02512ec586b1e39664f03a7
author Zaineb Qadiri <zqadiri@student.1337.ma> 1615024192 +0100
committer Zaineb Qadiri <zqadiri@student.1337.ma> 1615024192 +0100

Initial commit
```

`git cat-file -t <hash>`

to read its type

```bash
git cat-file -t  4816da

> commit
```

## Step 5 : look at the references :