# From Script to training pipeline
## What's in the repo:
1. Github action that triggers on push
2. The action sends a message to a pub/sub topic
3. The topic, Service account (in base 64), and project id are defined as secrets in the repo

## What's not in the repo:
The message in pub/sub should trigger a training pipeline
[Here](https://cloud.google.com/vertex-ai/docs/pipelines/trigger-pubsub) is how to write a cloud function that picks up on a pub/sub message

Potentially you could start any piece of code in the cloud function - for example [here](https://github.com/jy2k/Kubeflow-v2-end-to-end) is an end-to-end pipeline.

The example for architecture in mind:
![Screenshot](CI_CD_CT.png)
