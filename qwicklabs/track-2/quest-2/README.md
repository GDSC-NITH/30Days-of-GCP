<img src="/Resources/images/Perform-Foundational-Data-ML-and-AI-Tasks-in-Google-Cloud-Challenge-Lab.png" width="100%">
<br>
<br>
<h1 align="center">Task 1 and Task 2 : </h1>
  <h2 align="center">"Run a simple Dataflow job" and "Run a simple Dataproc job." </h2>

<h4>1. Create a bucket with a unique name.</h4>
<img src="/Resources/images/create-a-bucket.png" width="100%">

<h4>2. Run a simple Dataflow job :-</h4>

```bash
bq mk lab

gsutil cp gs://cloud-training/gsp323/lab.csv .

cat lab.csv

gsutil cp gs://cloud-training/gsp323/lab.schema .

cat lab.schema
```

<h4>3. After running the above commands copy the following as shown in the image below:-</h4>
<br>
<img src="/Resources/images/terminal1.png" width="100%">
<br>
<h4>4. Now go to the BigQuery section from Dashboard. Their you'll be able to see lab under your QwikLab project id then click on the three dots in front of lab and select open as shown in the image below.</h4>
<img src="/Resources/images/bigquery1.png" width="100%">
<br>
<h4>5. Now create the table with the following details shown in the images below.</h4>
<br>
<img src="/Resources/images/table1.png" width="100%">
<br>
<h4>6. Now select "edit as text" and paste the text which you have copied previosly from the console as shown in the image below.</h4>
<br>
<img src="/Resources/images/table2.png" width="100%">
<br>
<h4>7. Now click on create table.</h4>
<br>
<h4>8. Now go to Dataproc section from dashboard and "Create Cluster" with pre-defined values.</h4>
<img src="/Resources/images/cluster1.png" width="100%">
<br>
<h4>8. Now go to Dataflow section from dashboard and click on "Create Job From Template" and create job from template with the details shown in the image below.</h4>
<h4>9. You can copy all the commands from the Challenge lab page itself just don't forget to replace "YOUR_PROJECT" with your project id.</h4>
<img src="/Resources/images/job4.png" width="100%">
<img src="/Resources/images/job1.png" width="100%">
<img src="/Resources/images/job2.png" width="100%">
<img src="/Resources/images/job3.png" width="100%">
<br>
<h4>10. Click on Run job.</h4>
<br>
<h4>11. Now go to DATAPROC and click on the cluster.</h4>
<br>
<img src="/Resources/images/cluster2.png" width="100%">
<br>
<h4>12. Then click on VM INSTANCES and click on SSH.</h4>
<br>
<img src="/Resources/images/cluster3.png" width="100%">
<br>
<h4>13. In the SSH run the following command</h4>

```
hdfs dfs -cp gs://cloud-training/gsp323/data.txt /data.txt
```
<br>
<h4>14. Now go to job section and click on submit a job. </h4>
<br>
<img src="/Resources/images/job5.png" width="100%">
<br>
<h4>15. Now create a job with the specifications given below. </h4>
<br>
<img src="/Resources/images/job6.png" width="100%">
<br>

<h2 align="center"> Task 3: Run a simple Dataprep job</h2>

* Go to **Dataprep** > Accept the terms > Login with the same account

* Import Data > Select GCS > Edit > Enter the path as this: `gs://cloud-training/gsp323/runs.csv` > Import and Wrangle

* Modify the table as specified in the lab instructions.
<br>
<img src="/Resources/images/dataprep1.png" width="100%">
<br>
<h2 align="center">Task 4: AI</h4>

**<u>PART 1</u>**

Use the following commands:

```yaml
gcloud iam service-accounts create my-natlang-sa \
  --display-name "my natural language service account"

gcloud iam service-accounts keys create ~/key.json \
  --iam-account my-natlang-sa@${GOOGLE_CLOUD_PROJECT}.iam.gserviceaccount.com

export GOOGLE_APPLICATION_CREDENTIALS="/home/$USER/key.json"

gcloud auth activate-service-account my-natlang-sa@${GOOGLE_CLOUD_PROJECT}.iam.gserviceaccount.com --key-file=$GOOGLE_APPLICATION_CREDENTIALS

gcloud ml language analyze-entities --content="Old Norse texts portray Odin as one-eyed and long-bearded, frequently wielding a spear named Gungnir and wearing a cloak and a broad hat." > result.json

gcloud auth login 
(Copy the token from the link provided)

gsutil cp result.json gs://YOUR_PROJECT-marking/task4-cnl.result
```

**<u>PART 2</u>**

* Create an API Key by going to IAM > Credentials, and export it as `API_KEY` variable in the Cloud Shell. 

* Create the following JSON file:

```yaml
nano request.json

{
  "config": {
      "encoding":"FLAC",
      "languageCode": "en-US"
  },
  "audio": {
      "uri":"gs://cloud-training/gsp323/task4.flac"
  }
}
```

* Run the following:

  > Replace `YOUR_PROJECT` with your GCP Project ID.

```yaml
curl -s -X POST -H "Content-Type: application/json" --data-binary @request.json \
"https://speech.googleapis.com/v1/speech:recognize?key=${API_KEY}" > result.json

gsutil cp result.json gs://YOUR_PROJECT-marking/task4-gcs.result
```

**<u>PART 3</u>**

* Run the following:

```yaml
gcloud iam service-accounts create quickstart

gcloud iam service-accounts keys create key.json --iam-account quickstart@${GOOGLE_CLOUD_PROJECT}.iam.gserviceaccount.com

gcloud auth activate-service-account --key-file key.json

export ACCESS_TOKEN=$(gcloud auth print-access-token)
```

* Modify the previous JSON file:

```yaml
nano request.json

{
   "inputUri":"gs://spls/gsp154/video/chicago.mp4",
   "features": [
       "TEXT_DETECTION"
   ]
}
```

* Run the following:

> Replace `YOUR_PROJECT` with your GCP Project ID.

```yaml
curl -s -H 'Content-Type: application/json' \
    -H "Authorization: Bearer $ACCESS_TOKEN" \
    'https://videointelligence.googleapis.com/v1/videos:annotate' \
    -d @request.json



curl -s -H 'Content-Type: application/json' -H "Authorization: Bearer $ACCESS_TOKEN" 'https://videointelligence.googleapis.com/v1/operations/OPERATION_FROM_PREVIOUS_REQUEST' > result1.json


gsutil cp result1.json gs://YOUR_PROJECT-marking/task4-gvi.result
```









