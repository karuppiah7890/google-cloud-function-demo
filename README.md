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

LEVEL   NAME      EXECUTION_ID  TIME_UTC                 LOG
D       helloGET  gpaxvy76awgx  2018-09-28 07:36:03.508  Function execution started
D       helloGET  gpaxvy76awgx  2018-09-28 07:36:03.524  Function execution took 16 ms, finished with status code: 200
D       helloGET  gpaxv07k7vfz  2018-09-28 07:36:14.073  Function execution started
D       helloGET  gpaxv07k7vfz  2018-09-28 07:36:14.080  Function execution took 31 ms, finished with status code: 304
D       helloGET  gpaxda7yzx9q  2018-09-28 07:36:15.524  Function execution started
D       helloGET  gpaxda7yzx9q  2018-09-28 07:36:15.529  Function execution took 6 ms, finished with status code: 304
D       helloGET  gpaxdo4fyz75  2018-09-28 07:36:17.133  Function execution started
D       helloGET  gpaxdo4fyz75  2018-09-28 07:36:17.137  Function execution took 4 ms, finished with status code: 304
D       helloGET  gpaxnfr5oqc5  2018-09-28 07:49:36.739  Function execution started
D       helloGET  gpaxnfr5oqc5  2018-09-28 07:49:36.877  Function execution took 138 ms, finished with status code: 200
NOTICE  helloGET                2018-09-28 07:50:31.413
NOTICE  helloGET                2018-09-28 07:50:36.391
NOTICE  helloGET                2018-09-28 07:56:25.588
NOTICE  helloGET                2018-09-28 07:56:51.528
D       helloGET  5kkt83q80a5r  2018-09-28 07:57:01.332  Function execution started
D       helloGET  5kkt83q80a5r  2018-09-28 07:57:01.373  Function execution took 42 ms, finished with status code: 200
D       helloGET  5vn7k7x65ie0  2018-09-28 09:27:19.409  Function execution started
D       helloGET  5vn7k7x65ie0  2018-09-28 09:27:19.445  Function execution took 37 ms, finished with status code: 200
NOTICE  helloGET                2018-09-28 09:28:44.852
NOTICE  helloGET                2018-09-28 09:29:11.501
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

### Getting a list of the functions deployed

```
$ gcloud functions list

NAME      STATUS  TRIGGER       REGION
helloGET  ACTIVE  HTTP Trigger  us-central1
```