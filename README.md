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

Deploying function (may take a while - up to 2 minutes)...done.
availableMemoryMb: 256
entryPoint: helloGET
httpsTrigger:
  url: https://us-central1-cloud-functions-demo-217305.cloudfunctions.net/helloGET
labels:
  deployment-tool: cli-gcloud
name: projects/cloud-functions-demo-217305/locations/us-central1/functions/helloGET
runtime: nodejs8
serviceAccountEmail: cloud-functions-demo-217305@appspot.gserviceaccount.com
sourceUploadUrl: https://storage.googleapis.com/gcf-upload-us-central1-0068148b-0f87-4ab1-99dc-6d2008332018/fbadb755-9f22-4c62-81e6-7dbc0f5acf4a.zip?GoogleAccessId=service-661142553259@gcf-admin-robot.iam.gserviceaccount.com&Expires=1538128723&Signature=lhM4kWzqnYo0Fh4rPloqmdGZIHZ52YhHosoaV6nPh5xc5a%2B1JMqla%2FT8LaHfiEoZyF7Kyx8%2BIZKHs2McdQ14i%2BQ2rg%2FyXV9xnobdnHh5z8dIX5n8lQBtBVyeX2f1qctoB3Q2g8H2Sy9ld0w%2BcL%2FlV9CAuSsNr1WAokIFS3yqV5MpyZDAqw7poJFL5%2F6SbmckgEdSzFHSrVM02ba3seiXXo%2B%2FfYhSRzFh3m%2BkWyD%2Bff1CLS63bXdgQZarKothl9mblUAqdhe2%2FOLduAs7M%2BqdWVacNWWcg%2FZvgolzd8OpPfAq7g9bfh5B87RM44bNVlrV1xcovOp48lk05etmLDxp0A%3D%3D
status: ACTIVE
timeout: 60s
updateTime: '2018-09-28T09:29:11Z'
```

While deploying, it also created a `.gcloudignore` file

### Checking your logs is no tough stuff

```
$ gcloud functions logs read helloGET
```

### Invoking the function from CLI!

Instead of invoking the function using a HTTP request, you can invoke it from the command line using 

```
$ gcloud functions call helloGET

executionId: 5vn7k7x65ie0
result: Hello World! :D
```

### Getting information about the function from CLI !

You can get information using this command :

```
$ gcloud functions describe helloGET

availableMemoryMb: 256
entryPoint: helloGET
httpsTrigger:
  url: https://us-central1-cloud-functions-demo-217305.cloudfunctions.net/helloGET
labels:
  deployment-tool: cli-gcloud
name: projects/cloud-functions-demo-217305/locations/us-central1/functions/helloGET
runtime: nodejs8
serviceAccountEmail: cloud-functions-demo-217305@appspot.gserviceaccount.com
sourceUploadUrl: https://storage.googleapis.com/gcf-upload-us-central1-0068148b-0f87-4ab1-99dc-6d2008332018/fbadb755-9f22-4c62-81e6-7dbc0f5acf4a.zip?GoogleAccessId=service-661142553259@gcf-admin-robot.iam.gserviceaccount.com&Expires=1538128723&Signature=lhM4kWzqnYo0Fh4rPloqmdGZIHZ52YhHosoaV6nPh5xc5a%2B1JMqla%2FT8LaHfiEoZyF7Kyx8%2BIZKHs2McdQ14i%2BQ2rg%2FyXV9xnobdnHh5z8dIX5n8lQBtBVyeX2f1qctoB3Q2g8H2Sy9ld0w%2BcL%2FlV9CAuSsNr1WAokIFS3yqV5MpyZDAqw7poJFL5%2F6SbmckgEdSzFHSrVM02ba3seiXXo%2B%2FfYhSRzFh3m%2BkWyD%2Bff1CLS63bXdgQZarKothl9mblUAqdhe2%2FOLduAs7M%2BqdWVacNWWcg%2FZvgolzd8OpPfAq7g9bfh5B87RM44bNVlrV1xcovOp48lk05etmLDxp0A%3D%3D
status: ACTIVE
timeout: 60s
updateTime: '2018-09-28T09:29:11Z'
versionId: '2'
```