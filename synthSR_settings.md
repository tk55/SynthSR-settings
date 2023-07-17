## Freesurfer download

SynyhSR is included in Freesurfer7.3.0 or later. Download the version appropriate for your OS.

[freesurfer Download and Install](https://surfer.nmr.mgh.harvard.edu/fswiki/DownloadAndInstall)

Note:If you also want to keep using older version, you may want to use tar.gz rather than deb, rpm,
or pkg. packages. See the next section for details.

## Check your directories and make a directory for new version

Check the directory structure. If you are already using freesurfer, your directory should look something like this

```
/usr/local
       └── freesurfer        
```

Installation from the command line would be, for example, the following command

```
cd /usr/local
$ sudo mv freesurfer freesurfer-*.*.*        # rename your old package
$ sudo mkdir freesurfer                      # make new freesurfer directory
$ sudo mv freesurfer-*.*.* freesurfer        # move old package under freesurfer dir.
```

The final directory structure will look like this

```
/usr/local
       └── freesurfer
              ├── freesurfer-*.*.*(old_version)
              └── freesurfer-*.*.*(new_version)
```

## Unpack the freesurfer-latest to /usr/local/freesurfer (e.g. freesurfer-linux-ubuntu22_amd64-7.4.0.tar.gz)

```
sudo tar xvzf ~/Downloads/freesurfer-linux-ubuntu22_amd64-7.4.0.tar.gz -C /usr/local/freesurfer/freesurfer7.4.0
```

If you have license.txt, copy it into freesurfer/freesurfer7.4.0 directory.

## Update .bashrc

Open .bashrc (or maybe .bash_profile, bash_aliases) and comment out your old settings.

```
#FreeSurfer_old_version
#export SUBJECTS_DIR=/usr/local/freesurfer/freesurfer_old/subjects
#export FREESURFER_HOME=/usr/local/freesurfer/freesurfer_old
#export FS_LICENSE=/usr/local/freesurfer/freesurfer_old/license.txt
#source $FREESURFER_HOME/SetUpFreeSurfer.sh
```

Then write your new settings for new version.

```
#FreeSurfer *.*.*
export SUBJECTS_DIR=/usr/local/freesurfer/freesurfer*.*.*/subjects
export FREESURFER_HOME=/usr/local/freesurfer/freesurfer*.*.*
export FS_LICENSE=/usr/local/freesurfer/freesurfer*.*.*/license.txt
source $FREESURFER_HOME/SetUpFreeSurfer.sh
```

Note that you can switch between old version and dev version by switching comment outed lines of .bashrc file.

## 📌About Conflict with FSL 📌

If you use FSL 6.0.6 or later, some troubles may arrise. So you may want to modify FreeSurferEnv.sh.
Check following site for details.

[Dealing with Issues when Installing FreeSurfer and FSL 6.0.6 or Later](https://www.nemotos.net/?p=5388)

## 📌About the warning of synthSR 📌

For those who obtained the dev version immediately after the release, the following error message is displayed when mri_synthsr is executed.

```
get_data() is deprecated in favor of get_fdata(), which has a more predictable return type. To obtain get_data() behavior going forward, use numpy.asanyarray(img.dataobj).

* deprecated from version: 3.0
* Raises <class 'nibabel.deprecator.ExpiredDeprecationError'> as of version: 5.0
resuming program execution
```

You can leave this message alone, but a patch file is available at freesurfer's website (<https://surfer.nmr.mgh.harvard.edu/pub/dist/freesurfer/7.3.2-patch/synthsr/>). Please download this file and replace the file according to the README.txt.

## How to use synthSR ?

See freesurfer [wiki page.](https://surfer.nmr.mgh.harvard.edu/fswiki/SynthSR)

- If you get error with GPU version(default), you can use CPU version by setting "--cpu" flag. If you use
"--threads" flag (eg. --threads 4 or more, according to your resource) together, it will not take so longer time.

- If you get error like

```
what():  std::bad_alloc
```

You can check your memory rsource.
If you are using --threads option, by removing it things may go better.

- Related to the above, note using CT as input  might need more abundant memory.

Good luck! :smiley::wave:
