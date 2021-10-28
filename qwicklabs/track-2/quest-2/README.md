<img src="/Resources/images/Perform-Foundational-Data-ML-and-AI-Tasks-in-Google-Cloud-Challenge-Lab.png" width="100%">
<br>
<br>
<h1 align="center">Task 1: Run a simple Dataflow job</h1>

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
<h4>16. Now go to DATAPREP from the dashboard and allow everything and Accept condition and login to DATAPREP </h4>
<br>
<h4>17. In the Dataprep click on GCS then fill the path shown in the image below and click on go !! </h4>
<br>
<img src="/Resources/images/dataprep1.png" width="100%">
<h4>Now after sometime you'll see an continue button in right bottom side of your screen click on that. </h4>






