# act_demo

This repo contains a use case of [Nektos/Act](https://github.com/nektos/act) that showcase the functionality of Nektos Act runner to replicate the work Github Actions does.

## Installation

```bash
brew install act
```

## Usage

### TL;DR

```bash
act push -s GITHUB_TOKEN="$(gh auth token)" -P ubuntu-latest=-self-hosted
```

**Hint**: `-P ubuntu-latest=nektos/act-environments-ubuntu:18.04` creates a container with the specified image and runs the workflow in it. This is useful when you want to test your workflow in a specific environment instead of the local machine. Surely, [docker](https://docs.docker.com/get-docker/) must be installed to use it.

### Detailed

```bash
Run GitHub actions locally by specifying the event name (e.g. `push`) or an action name directly.

Usage:
  act [event name to run] [flags]

If no event name passed, will default to "on: push"
If actions handles only one event it will be used as default instead of "on: push"

Flags:
      --action-cache-path string                          Defines the path where the actions get cached and host workspaces created. (default "/Users/edizemektas/.cache/act")
  -a, --actor string                                      user that triggered the event (default "nektos/act")
      --artifact-server-addr string                       Defines the address to which the artifact server binds. (default "192.168.2.3")
      --artifact-server-path string                       Defines the path where the artifact server stores uploads and retrieves downloads from. If not specified the artifact server will not start.
      --artifact-server-port string                       Defines the port where the artifact server listens. (default "34567")
  -b, --bind                                              bind working directory to container, rather than copy
      --bug-report                                        Display system information for bug report
      --cache-server-addr string                          Defines the address to which the cache server binds. (default "192.168.2.3")
      --cache-server-path string                          Defines the path where the cache server stores caches. (default "/Users/edizemektas/.cache/actcache")
      --cache-server-port uint16                          Defines the port where the artifact server listens. 0 means a randomly available port.
      --container-architecture string                     Architecture which should be used to run containers, e.g.: linux/amd64. If not specified, will use host default architecture. Requires Docker server API Version 1.41+. Ignored on earlier Docker server platforms.
      --container-cap-add stringArray                     kernel capabilities to add to the workflow containers (e.g. --container-cap-add SYS_PTRACE)
      --container-cap-drop stringArray                    kernel capabilities to remove from the workflow containers (e.g. --container-cap-drop SYS_PTRACE)
      --container-daemon-socket string                    URI to Docker Engine socket (e.g.: unix://~/.docker/run/docker.sock or - to disable bind mounting the socket)
      --container-options string                          Custom docker container options for the job container without an options property in the job definition
      --defaultbranch string                              the name of the main branch
      --detect-event                                      Use first event type from workflow as event that triggered the workflow
  -C, --directory string                                  working directory (default ".")
  -n, --dryrun                                            dryrun mode
      --env stringArray                                   env to make available to actions with optional value (e.g. --env myenv=foo or --env myenv)
      --env-file string                                   environment file to read and use as env in the containers (default ".env")
  -e, --eventpath string                                  path to event JSON file
      --github-instance string                            GitHub instance to use. Dont use this if you are not using GitHub Enterprise Server. (default "github.com")
  -g, --graph                                             draw workflows
  -h, --help                                              help for act
      --input stringArray                                 action input to make available to actions (e.g. --input myinput=foo)
      --input-file string                                 input file to read and use as action input (default ".input")
      --insecure-secrets                                  NOT RECOMMENDED! Doesnt hide secrets while printing logs.
  -j, --job string                                        run a specific job ID
      --json                                              Output logs in json format
  -l, --list                                              list workflows
      --log-prefix-job-id                                 Output the job id within non-json logs instead of the entire name
      --matrix stringArray                                specify which matrix configuration to include (e.g. --matrix java:13
      --no-cache-server                                   Disable cache server
      --no-recurse                                        Flag to disable running workflows from subdirectories of specified path in --workflows/-W flag
      --no-skip-checkout                                  Do not skip actions/checkout
  -P, --platform stringArray                              custom image to use per platform (e.g. -P ubuntu-18.04=nektos/act-environments-ubuntu:18.04)
      --privileged                                        use privileged mode
  -p, --pull                                              pull docker image(s) even if already present (default true)
  -q, --quiet                                             disable logging of output from steps
      --rebuild                                           rebuild local action docker image(s) even if already present (default true)
      --remote-name string                                git remote name that will be used to retrieve url of git repo (default "origin")
      --replace-ghe-action-token-with-github-com string   If you are using replace-ghe-action-with-github-com  and you want to use private actions on GitHub, you have to set personal access token
      --replace-ghe-action-with-github-com stringArray    If you are using GitHub Enterprise Server and allow specified actions from GitHub (github.com), you can set actions on this. (e.g. --replace-ghe-action-with-github-com =github/super-linter)
  -r, --reuse                                             dont remove container(s) on successfully completed workflow(s) to maintain state between runs
      --rm                                                automatically remove container(s)/volume(s) after a workflow(s) failure
  -s, --secret stringArray                                secret to make available to actions with optional value (e.g. -s mysecret=foo or -s mysecret)
      --secret-file string                                file with list of secrets to read from (e.g. --secret-file .secrets) (default ".secrets")
      --use-gitignore                                     Controls whether paths specified in .gitignore should be copied into container (default true)
      --userns string                                     user namespace to use
      --var stringArray                                   variable to make available to actions with optional value (e.g. --var myvar=foo or --var myvar)
      --var-file string                                   file with list of vars to read from (e.g. --var-file .vars) (default ".vars")
  -v, --verbose                                           verbose output
      --version                                           version for act
  -w, --watch                                             watch the contents of the local repo and run when files change
  -W, --workflows string                                  path to workflow file(s) (default "./.github/workflows/")
```