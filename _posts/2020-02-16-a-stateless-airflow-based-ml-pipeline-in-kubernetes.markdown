---
layout: post
title:  "A Stateless Airflow Based Machine Learning Pipeline in Kubernetes"
date:   2020-02-16
categories: jekyll update
---


## Background

[Airflow](https://airflow.apache.org/) is a popular open source project for workflow management written in Python. It automates the task depedency management, error alerting and also provides built-in support for retry. In its core, a complete workflow with potentially many tasks is represented as a Directed Asyclic Graph (DAG).

In a modern development team, it is often desireable to have a Continuous Integration (CI) infrastructure to provide a fast feedback loop to all changes. Such CI framework is often integrated with a Git repo (such as BitBucket, Github etc) and some tests will be triggered based on certain events such as pull request being created. Machine Learning (ML) applications differs from conventional applications in that
1. It requires a lot of data
2. If data changes, the model will change
3. If the model training logic changes, the model will also change

Therefore, it is very important to have some kind of end-to-end integration tests to make sure that the code changes didn't introduce significant differences in terms of model's performance. So, let's assume that integration test will basically trigger the DAG under test and verify the model metrics in the end

## The Challenges

Even with a relative small team size (say 3 to 5 persons), it is still very common that people will work on the same DAG or modify the same task being used in the DAG for different feature implementations. This means that we will need Airflow to be able to run the same DAG with difference version of the code. On the other hand, if Airflow is configured to run tasks in local executors, it will need to either
1. git checkout that version of the code, if Python environment is configured to load the git source
2. install the version of code into the Python environment

Either way, it can only have __ONE__ version at any time. This means that DAG runs will interfere with each other

To solve this issue, we need to use other type of executors and in this post, we will focus on using Kubernetes Executor to build a stateless CI framework


## The Solution
To be continued...
