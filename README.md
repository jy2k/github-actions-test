# From Script to training pipeline
## What's in the repo:
Github action that triggers on push
The action sends a message to a pub/sub topic
The topic, Service account (in base 64), and project id are defined as secrets in the repo

## What's not in the repo:
The message in pub/sub should trigger a training pipeline
[Here](https://cloud.google.com/vertex-ai/docs/pipelines/trigger-pubsub) is how to write a cloud function that picks up on a pub/sub message
