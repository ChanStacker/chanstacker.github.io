---
layout: default
title:  "Creating continuous dependent jobs control-m"
date:   2022-01-26 07:00:00 +0100
categories: techarticle
---

The idea is to create a job JOB_A that runs on a recurrent schedule and on successful run, will kick off another job JOB_B.
A recurrent schedule is achieved by making a job cyclic in Control M.  This is done through the "Rerun settings" located in the "Schedule" tab under the job's properties.

1. Create a variable on JOB_A, say pre_req_job_a and add to it's Prerequisites tab.
2. On the Action tab under Out conditions, "Remove" varianle pre_req_job_a.  This is to prevent JOB_A from running again before JOB_B has kicked off and run. For JOB_B to kick off, add another variable say "pre_req_job_b" and mark it as "Add".  
3. On JOB_B prerequisites, make variable "pre_req_job_b" as a prerequisite.
4. On JOB_B Action tab under Out conditions, "Remove" varianle pre_req_job_b.  This is to prevent JOB_B from running again before JOB_A has ran again. To signal JOB_A to rerun, add another variable say "pre_req_job_a" and mark it as "Add". 
5. To kick off the above loop, add a dummy job say "INITIALISATION_JOB" that will run only once.  Do not make this job cyclic as it is supposed to run only once.  Specify a time on it's schedule when it should run, normally at the beginning on the next Control M chart.  In it's Action tab, add variable "pre_req_job_a" and mark it as Add.
6. A characteristic of ControlM is that when a rest call is made it expects a status 200 in order to consider a call successful and mark the job green (goes back to grey if job is cyclic).  If endpoint returns void, ie 204, it will consider it as a failure and make impact the cyclic nature depending on what is configured in the Actions tab.  To handle 204 as success, in the "On-Do" actions, add an action "When OS completion status Equal to 204" then "Set to OK".  I don't have screenshots to provide but under the Actions > On-Do actions section, it is pretty explicit.

