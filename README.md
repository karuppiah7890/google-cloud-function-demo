# Simple Hello World endpoint using Google Cloud Functions

Prerequisties : 
1. Google Cloud Platform (GCP) account
2. `gcloud` cli tool

## Things learned while trying out

### `gcloud` supports tab completion ! 🎉

It's so easy to press tab and see the sub commands and even the options! And the names of options and sub commands are mostly understandable without checking help

### Minimal code !

I just wrote a `index.js` file with a HTTP handler and *nothing* else! 

### Deploying is easy peasy !!

```
$ gcloud functions deploy helloGET --runtime nodejs8 --trigger-http
```

While deploying, it also created a `.gcloudignore` file

### Checking your logs is no tough stuff

```
$ gcloud functions logs read helloGET
```
