## Starting a Notebook Instance from the Command Line

In this section, we’ll examine how the command line is used to launch and shut down a pre-configured deep learning VM integrated with JupyterLab.

Create a Datalab instance: To create a Notebook instance, execute the code

```
export IMAGE_FAMILY="tf-latest-cpu-experimental"
export ZONE="us-west1-b"
export INSTANCE_NAME="my-instance"
gcloud compute instances create $INSTANCE_NAME \
  --zone=$ZONE \
  --image-family=$IMAGE_FAMILY \
  --image-project=deeplearning-platform-release
```

where

--image-family can be any of the available images supported by Google Deep Learning VM; "tf-latest-cpu-experimental" launches an image with TensorFlow 2.0 pre-configured.

--image-project must be set to deeplearning-platform-release

### Connect to the instance: To connect to JupyterLab running on the instance, run the command

```
export INSTANCE_NAME="my-instance"
gcloud compute ssh $INSTANCE_NAME -- -L 8080:localhost:8080
```

#### Output:

```
/opt/deeplearning/binaries/tensorflow/
If you need to install a different version of Tensorflow manually, use the common Deep Learning image with the
right version of CUDA

Linux ml-instance 4.9.0-11-amd64 #1 SMP Debian 4.9.189-3+deb9u1 (2019-09-20) x86_64

The programs included with the Debian GNU/Linux system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.
```

### Stop the instance: To stop the instance, run the following command from your local terminal (not on the instance):

gcloud compute instances stop $INSTANCE_NAME
Stopping instance(s) my-instance...done.

Updated [https://www.googleapis.com/compute/v1/projects/ekabasandbox/zones/us-west1-b/instances/my-instance].