---
layout: classic-docs
title: "CircleCI 2.0 Configuration Formatting"
short-title: "Formatting"
categories: [configuring-circleci]
---

Custom configuration for CircleCI lives in `~/.circleci/config.yml`. This is where you tell us how to do our jobs.

Let’s walk through the sections and explain what they’re for.

## `<root>`

This is the top level of the YAML file. You’re only allowed to specify 2 keys here:

**version**

This is the version of CircleCI you’re using and should be 2.

As we roll out new features for CircleCI, we’ll be using this field to issue warnings about deprecations or breaking changes.

**jobs**

This is a list of “jobs”, which we’ll define in the next section because it’s that important.

## `jobs`

Each job is a map with a single key-value pair.

The key is the job’s type and should form a unique tuple with the project’s name. The value is a map with the following attributes:

**name**

The name the UI will show for this job. If unspecified, will default to `<job-name>` (the key for this map).

**docker**

Map representing options for the docker executor. Using this means you are _not_ using the `machine` key.

**machine**

Map representing options for the machine executor. Using this means you are _not_ using the `docker` key.

**steps**

A list of steps to be performed for this job. This is the only key required by a job.

**parallelism**

The number of parallel instances of this job. Defaults to 1.

**environment**

A map of environment variable names and values.

**working_directory**

A directory from which to run a job’s steps. The default depends on which executor you choose (docker vs. machine).