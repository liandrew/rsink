# rsink

rsink is a wrapper around the rsync program. It simplifies remote 
synchronization by providing functions to mange remote hosts.

# Getting Started

## Installing 

Check that `$HOME/bin` is in your path 

```bash 
echo $PATH
```

If not then add it to your path

```bash 
vi ~/.zshrc
```

Download rsink and move it to your `$HOME/bin` directory

```bash 
wget https://raw.githubusercontent.com/liandrew/rsink/master/rsink
chmod +x rsink
mkdir -p $HOME/bin; mv rsink $HOME/bin
```

## Initialize directory

Upon initializing, a `.rsink` file will be created. The file is used to store 
configuration information such as remote name and host. Once the `.rsink` file
is created `rsink` will recognize the directory it resides in as a `rsink` project.  

```bash 
rsink init 
```

## Add remote

Add a remote host.  Specifiy the name and remote host along with the 
destination directory you would like to syncrhonize with.

```bash 
rsink remote add <remote-name> <remote_host>:<destination_directory>
```

## Push to remote

The push command is used to copy files from the current `rsink` project 
directory to the remote host destination directory.  The remote host 
destination directory is specified in the `.rsink` file.

```bash
rsink push <remote-name> <options>
```

## Pull from remote

The pull command is used to copy files from the remote host specified in your
`.rsink` file over to your current `rsink` project directory.

```bash 
rsink pull <remote-name> <options>
```

# List your remotes

Method #1 

```bash 
rsink remote list
```

Method #2 

```bash 
rsink remote -v
```

# Remove a remote 

```bash
rsink remote remove <remote-name>
```

## Supported options 

* -a, --archive
* -r, --recursive
* -n, --dry-run
* -q, --quiet
* -v, --verbose
* -t, --times
*     --size-only
* -i, --itemize-changes
* -u, --update
*      --delete
* -h, --human-readable
*      --progress
* -z, --compress

If you are unsure, use --dry-run to test what gets transfered before doing an
actual transfer.

```bash 
rsink push <remote-name> <option-to-test> --dry-run
```

# Compatability

rsink was only tested on Mac OSx
