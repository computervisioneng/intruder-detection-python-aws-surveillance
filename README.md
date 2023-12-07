# intruder-detection-python-aws-surveillance

<p align="center">
<a href="https://www.youtube.com/watch?v=">
    <img width="100%" src="thumbnail.jpg" alt="Watch the video">
</a>
</p>

## pipeline

<p align="center">
    <img src="https://github.com/computervisioneng/intruder-detection-python-aws-surveillance/blob/main/pipeline.jpg" alt="Project pipeline">
</p>

## execution

### setting up producer

### setting up consumer #1: backup

- Go to S3 and create an S3 bucket.
- Go to EC2 and launch a t2.medium instance with 20GB storage size.
- Go to IAM and create an access role for the EC2 instance with the following policies: **AmazonKinesisVideoStreamsFullAccess** and **AmazonS3FullAccess**.
- Attach the IAM role to the EC2 instance.
- SSH into the EC2 instance.
- Execute the following commands in the EC2 instance:

      sudo apt update
  
      sudo apt install python3-virtualenv

      virtualenv venv --python=python3
  
      source venv/bin/activate
  
      git clone https://github.com/aws-samples/amazon-kinesis-video-streams-consumer-library-for-python.git

      cd amazon-kinesis-video-streams-consumer-library-for-python
  
      pip install -r requirements.txt

      sudo apt-get update && sudo apt-get install ffmpeg libsm6 libxext6  -y

      sudo apt-get install python3-tk

- Edit region name and stream name.
- Add backup funcionality.
- Execute the following commands:

      cd ~/amazon-kinesis-video-streams-consumer-library-for-python
      python kvs_consumer_library_example.py

### setting up consumer #2: intruder detection

- Go to S3 and create an S3 bucket.
- Go to DynamoDB and create a table.
- Go to SNS and create a new topic.
- Select the topic you created and create a new subscription.
- Go to EC2 and launch a t2.medium instance with 20GB storage size.
- Go to IAM and create an access role for the EC2 instance with the following policies: **AmazonKinesisVideoStreamsFullAccess**, **AmazonDynamoDBFullAccess**, **AmazonS3FullAccess** and **AmazonRekognitionFullAccess**.
- Attach the IAM role to the EC2 instance.
- SSH into the EC2 instance.
- Execute the following commands in the EC2 instance:

      sudo apt update
  
      sudo apt install python3-virtualenv

      virtualenv venv --python=python3
  
      source venv/bin/activate
  
      git clone https://github.com/aws-samples/amazon-kinesis-video-streams-consumer-library-for-python.git

      cd amazon-kinesis-video-streams-consumer-library-for-python
  
      pip install -r requirements.txt

      sudo apt-get update && sudo apt-get install ffmpeg libsm6 libxext6  -y

      sudo apt-get install python3-tk

- Edit region name and stream name.
- Add intruder detection funcionality.
- Execute the following commands:

      cd ~/amazon-kinesis-video-streams-consumer-library-for-python
      python kvs_consumer_library_example.py
