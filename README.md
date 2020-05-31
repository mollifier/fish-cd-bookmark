# fish-cd-bookmark

## Synopsis
Command to bookmark directories for fish shell

Port of [cd-bookmark](https://github.com/mollifier/cd-bookmark) for the fish shell.

## How to set up

### Installing using fisher
We recommend using [fisher](https://github.com/jorgebucaran/fisher) to install fish-cd-gitroot.

```
fisher add mollifier/fish-cd-bookmark
```

## How to set up

### Manually install

Put cd-bookmark and _cd-bookmark files somewhere in your $fpath and add the following line to your .zshrc:

```
autoload -Uz cd-bookmark
```

## Usage

### Add a directory to bookmark

```
cd-bookmark add [BOOKMARK_NAME] [BOOKMARK_DIRECTORY_PATH]
```

Add BOOKMARK\_DIRECTORY\_PATH directory to bookmark with BOOKMARK\_NAME.
If BOOKMARK\_DIRECTORY\_PATH is not specified, add current directory.
If BOOKMARK\_NAME is not specified, the directory basename is used.

BOOKMARK\_NAME is used as a key in bookmark.

### Change directory

```
cd-bookmark cd BOOKMARK_NAME
```

Change current directory to the directory associated with BOOKMARK_NAME.
In this form, you can add relative path from bookmark real path at the end of BOOKMARK\_NAME (see example below).

### List directories

```
cd-bookmark list
```

List all bookmarks.

### Print bookmark directory path

```
cd-bookmark print BOOKMARK_NAME
```

Prints the directory path associated with BOOKMARK_NAME.

### Delete bookmark

```
cd-bookmark delete BOOKMARK_NAME
```

Delete the bookmark.


## Options
\--help, -h    display help and exit

## Variables

Bookmarks are stored in `~/.fish_cd_bookmark` file. This file path can be changed by `FISH_CD_BOOKMARK_PATH` variable.

For example

```
set -g FISH_CD_BOOKMARK_PATH ~/.config/fish/bookmark_file
```


## Examples

```
# Current directory is '/home/mollifier/work'.
> pwd
/home/mollifier/work

# Add current directory to bookmark. It's bookmark name is 'work'.
> cd-bookmark add

# cd somewhere.
> cd

# Back to 'work' directory.
> cd-bookmark cd work
> pwd
/home/mollifier/work

# Add another directory to bookmark.
# In this case, it's bookmark name is 't'.
> cd /home/mollifier/tmp
> cd-bookmark add t

# List current bookmarks.
> cd-bookmark list
work|/home/mollifier/work
t|/home/mollifier/tmp

# You can add relative path from bookmark real path at the end of BOOKMARK_NAME.
> cd-bookmark work/project/data
> pwd
/home/mollifier/work/project/name
```

