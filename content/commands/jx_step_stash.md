---
date: 2019-01-22T21:36:41Z
title: "jx step stash"
slug: jx_step_stash
url: /commands/jx_step_stash/
---
## jx step stash

Stashes local files generated as part of a pipeline into long term storage

### Synopsis

This pipeline step stashes the specified files from the build into some stable storage location.
  
Currently Jenkins X supports storing files into a branch of a git repository or in cloud blob storage like S3, GCS, Azure blobs etc. 

When using Cloud Storage we use URLs like 's3://nameOfBucket' on AWS, 'gs://anotherBucket' on GCP or on Azure 'azblob://thatBucket' 

See Also: 

  * jx step unstash : https://jenkins-x.io/commands/jx_step_unstash  
  * jx edit storage : https://jenkins-x.io/commands/jx_edit_storage

```
jx step stash [flags]
```

### Examples

```
  # lets collect some files to the team's default storage location (which if not configured uses the current git repository's gh-pages branch)
  jx step stash -c tests -p "target/test-reports/*"
  
  # lets collect some files to a specific Git URL for a repository
  jx step stash -c tests -p "target/test-reports/*" --git-url https://github.com/myuser/myrepo.git
  
  # lets collect some files with the file names relative to the 'target/test-reports' folder and store in a Git URL
  jx step stash -c tests -p "target/test-reports/*" --basedir target/test-reports --git-url https://github.com/myuser/myrepo.git
  
  # lets collect some files to a specific AWS cloud storage bucket
  jx step stash -c coverage -p "build/coverage/*" --bucket-url s3://my-aws-bucket
  
  # lets collect some files to a specific cloud storage bucket
  jx step stash -c tests -p "target/test-reports/*" ---bucket-url gs://my-gcp-bucket
  
  # lets collect some files to a specific cloud storage bucket and specify the path to store them inside
  jx step stash -c tests -p "target/test-reports/*" ---bucket-url gs://my-gcp-bucket --to-path tests/mystuff
```

### Options

```
      --basedir string            The base directory to use to create relative output file names. e.g. if you specify '--pattern "target/*.xml" then you may want to supply '--basedir target' to strip the 'target/' prefix from all collected files
  -b, --batch-mode                In batch mode the command never prompts for user input
      --bucket-url string         Specify the cloud storage bucket URL to send each file to. e.g. use 's3://nameOfBucket' on AWS, gs://anotherBucket' on GCP or on Azure 'azblob://thatBucket'
  -c, --classifier string         A name which classifies this type of file. Example values: coverage, tests, logs
      --dir string                The source directory to try detect the current git repository or branch. Defaults to using the current directory
      --git-branch string         The branch to use to store files in the git repository (default "gh-pages")
      --git-url string            Specify the Git URL to of the repository to use for storage
      --headless                  Enable headless operation if using browser automation
  -h, --help                      help for stash
      --install-dependencies      Should any required dependencies be installed automatically
      --log-level string          Logging level. Possible values - panic, fatal, error, warning, info, debug. (default "info")
      --no-brew                   Disables the use of brew on macOS to install or upgrade command line dependencies
  -p, --pattern stringArray       Specify the pattern to use to look for files
      --project-branch string     The project git branch of the project to collect for. Used to default the branch folder in the storage. If not specified its discovered from the local '.git' folder
      --project-git-url string    The project git URL to collect for. Used to default the organisation and repository folders in the storage. If not specified its discovered from the local '.git' folder
      --pull-secrets string       The pull secrets the service account created should have (useful when deploying to your own private registry): provide multiple pull secrets by providing them in a singular block of quotes e.g. --pull-secrets "foo, bar, baz"
      --skip-auth-secrets-merge   Skips merging a local git auth yaml file with any pipeline secrets that are found
  -t, --to-path string            The path within the storage to store the files. If not specified it defaults to 'jenkins-x/$category/$owner/$repoName/$branch/$buildNumber'
      --verbose                   Enable verbose logging
```

### SEE ALSO

* [jx step](/commands/jx_step/)	 - pipeline steps

###### Auto generated by spf13/cobra on 22-Jan-2019