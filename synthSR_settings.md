## Freesurfer-dev package download

SynyhSR is included in dev versions.  Download the version appropriate for your OS.

[freesurfer dev](https://surfer.nmr.mgh.harvard.edu/pub/dist/freesurfer/dev/)

## Check your directories and make a directory for dev.

Check the directory structure. If you are already using freesurfer, your directory should look like this

```
/usr/local
       └── freesurfer        
```
Installation from the command line would be, for example, the following command

```
$ cd /usr/local
$ sudo mv freesurfer freesurfer-*.*.*        # rename your old package
$ sudo mkdir freesurfer                      # make new freesurfer directory
$ sudo mv freesurfer-*.*.* freesurfer        # move old package under freesurfer dir.
```
The final directory structure will look like this

```
/usr/local
       └── freesurfer
              ├── freesurfer-*.*.*
              └── dev
```


## Unpack the freesurfer-dev to /usr/local/freesurfer 

```
sudo tar xvzf ~/Downloads/freesurfer-linux-ubuntu20_x86_64-7-dev.tar.gz -C /usr/local/freesurfer/dev
```

If you have license.txt, copy it into freesurfer-dev.

## Update .bashrc
Open .bashrc (or maybe .bash_profile, bash_aliases) and comment out your old settings.

```
#FreeSurfer *.*.*
#export SUBJECTS_DIR=/usr/local/freesurfer/freesurfer*.*.*/subjects
#export FREESURFER_HOME=/usr/local/freesurfer/freesurfer*.*.*
#export FS_LICENSE=/usr/local/freesurfer/freesurfer*.*.*/license.txt
#source $FREESURFER_HOME/SetUpFreeSurfer.sh
```

Then write your new settings for dev version.
```
#FreeSurfer dev
export SUBJECTS_DIR=/usr/local/freesurfer/dev/subjects
export FREESURFER_HOME=/usr/local/freesurfer/dev
export FS_LICENSE=/usr/local/freesurfer/dev/license.txt
source $FREESURFER_HOME/SetUpFreeSurfer.sh
```

Note that you can switch between old version and dev version by switching comment outed lines of .bashrc file.

## How to use synthSR ?

See freesurfer [wiki page.](https://surfer.nmr.mgh.harvard.edu/fswiki/SynthSR)
Good luck!