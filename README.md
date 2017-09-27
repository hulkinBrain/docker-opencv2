# Docker image for opencv2, python, numpy, matplotlib and other libraries

**The docker image contains:**

- OpenCV 2.4.13.3
- Python 2.7
- Numpy
- Matplotlib
- Pillow
- Virtualenv

_Please check the requirements.txt for other libraries which get installed while running the Dockerfile and make changes to install more libraries_

This ```Dockerfile``` is based on the official docker [Python image](https://hub.docker.com/_/python/) and contains the bash script commands to install OpenCV which have been taken from [here](https://github.com/milq/milq/blob/master/scripts/bash/install-opencv.sh). The commands have been altered a little to install the above mentioned libraries. 

### Instructions to install any library using ```Dockerfile```

To install any library, search the linux bash installation method for that library. Just paste the commands which you'd execute sequentially on a linux bash shell for installation, inside the Dockerfile. Check out the Dockerfile in this repository to see how to paste the bash commands.

**To test the docker image run the following command:**

    docker run -it hulkinbrain/docker-opencv2 bash
    
**And to test the installed libraries, run the following commands after running the above command:**<br>
_OpenCV installation is being checked by the following commands_

    # python
    >>> import cv2
    >>> print cv2.__version__
    2.4.13.3


### Extra information for those looking to deploy Docker images for their heroku webapps
For example if you want to deploy a Django based webapp using this Docker image, follow the below instructions:

- **Clone this repository to your local environment**
- **Copy your project folder into the cloned repository**
- **Change the following lines of the Dockerfile:**

    ```
    ADD ./yourProjectFolder /opt/yourProjectFolder/
    WORKDIR /opt/yourProjectFolder

    # Assuming yourProjectFolder contains manage.py run the following command to start the server

    CMD python manage.py runserver 0.0.0.0:$PORT
    ```
- **Push the updated repository to github**
- **Go to your docker account and create an automatic build by linking your github account and selecting your repository to Docker. Docker will build an image after 2-3 mintues on its own, it the building doesnt start make a small change in the readme.md file. This will trigger the building.**
- **After the image gets created, Run the following commands in the CLI to deploy your webapp along with the Dockerimage:**
    ```
    heroku container:login
    
    heroku create yourAppName
    
    heroku container:push web
    
    heroku open
    ```
Now your webapp will open on your browser
