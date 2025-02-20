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
  -

- get output of job
  - job runner logs to file on disk
  - http api reads from the log file on disk

- trigger job
  - trigger externally
  - trigger via git push

http api

- /buildy/job/[job name]
  - POST: Create job
  - DELETE: Delete Job
  -
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
  - containers
    - create container
    - run command in container
    - copy result out of container
