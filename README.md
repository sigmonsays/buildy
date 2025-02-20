# buildy

goal is to build a simple cicd daemon to define and run jobs


the core of a cicd daemon

- define job steps (job spec)
  - shell commands
  - steps in containers (to do later)

- execute jobspec
  - execute array of jobspec
  - capture output
  - extract values from output for next steps
  - job execution timeout
  - json output of jobspec is supported as an "output format"

- job runner
  - takes a jobspec and runs it
  - given a job name, returns the list of runs
  - given a job name, returns log file locations

- get output of job
  - job runner logs to file on disk
  - http api reads from the log file on disk

- trigger job
  - trigger externally
  - trigger on timer (to do later)
  - trigger via git push

configuration
- configuration reload
  - how does a job config get reloaded

on disk
 /etc/buildy/config.yaml
 - main daemons config
 - defines jobs dir, ie /srv/buildy/jobs

job /srv/buildy/jobs/[job id]/
    run/

http api
- /buildy/job/[job name]
  - POST: Create job
  - DELETE: Delete Job

- /buildy/job/[job name]/run
  - run a job
  - POST: Trigger job run

- /buildy/job/[job name id]/output/raw
  - GET
    - read job output
    - params
      last = 50 - number of lines to read

brainstorms
  - shell commands
    - env variables
    - current working directory
    - run as user
    - timeout
  - containers
    - create container
    - run command in container
    - copy result out of container
