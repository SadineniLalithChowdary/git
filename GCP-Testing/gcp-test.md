## Resize the Machine Type of a GCP VM Instance

shell
## Set Variables
$PROJECT_ID="windows-test-lalith"
$ZONE="us-central1-c"
$INSTANCE_NAME="lalith-test-01"
$MACHINE_TYPE="n2-standard-8"

## Pre-Change
shell
gcloud compute instances describe $INSTANCE_NAME --zone=$ZONE

## Paste the pre-change output below -

machineType:  https://www.googleapis.com/compute/v1/projects/windows-test-lalith/zones/us-central1-a/machineTypes/n2-standard-4


## Steps to resize an instance for a Standard Machine Type
shell
## Login and set Project
gcloud auth login
gcloud config set project $PROJECT_ID

## Stop the instance
gcloud compute instances stop $INSTANCE_NAME --zone=$ZONE

## Change the Machine Type
gcloud compute instances set-machine-type $INSTANCE_NAME --zone=$ZONE --machine-type=$MACHINE_TYPE

## Start the instance
gcloud compute instances start $INSTANCE_NAME --zone=$ZONE

## Post-Change
shell
gcloud compute instances describe $INSTANCE_NAME --zone=$ZONE

## Paste the post-change output below -
```
machineType:

[https://compute.googleapis.com/compute/v1/projects/windows-test-lalith/zones/us-central1-a/instances/lalith-test-01].