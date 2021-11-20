# From Script to training pipeline
## What's in the repo:
A Github Workflow located at [.github/workflows/github-actions-demo.yml](https://github.com/jy2k/github-actions-test/tree/main/.github/workflows).
The Workflow:
1. Once a push is made to the repo the workflow triggers
2. The workflow sends a message to a pub/sub topic

## What's not in the repo:
The message in pub/sub should trigger a training pipeline
[Here](https://cloud.google.com/vertex-ai/docs/pipelines/trigger-pubsub) is how to write a cloud function that picks up on a pub/sub message

Potentially you could start any piece of code in the cloud function - for example [here](https://github.com/jy2k/Kubeflow-v2-end-to-end) is an end-to-end pipeline.

The example for architecture in mind:
![Screenshot](CI_CD_CT.png)

### Misc
#### Secrets
The pub/sub topic, Service account (in base 64), and project id are defined as secrets in the repo
[Here](https://damienaicheh.github.io/github/actions/2021/04/15/environment-variables-secrets-github-actions-en.html) is how to create secrets in Github (also shows how to create convert key.json to base64)
[Here](https://medium.com/firebase-developers/create-automatic-firestore-backups-with-github-actions-abb12eef86a0) is how to save the service account JSON key in base64

#### Service account
[Create a Service account](https://cloud.google.com/iam/docs/creating-managing-service-accounts#creating) in your Google Project and download a JSON key. Encode it as base65 and save it to the Repos secrets.
The minimum role that the service account needs is ["Pub/Sub Publisher"](https://cloud.google.com/iam/docs/understanding-roles#pub-sub-roles).

Generally based the Github actions workflow on [this](https://github.com/google-github-actions/setup-gcloud) gcloud setup
