# Docker container for opencv2 and python

The docker image contains:

- OpenCV 2.4.13.3
- Python 2.7
- Numpy
- Matplotlib
- Pillow
- Virtualenv

_Please check the requirements.txt for other libraries which get installed while running the Dockerfile and make changes to install more libraries_

**To test the docker image run the following command:**

    docker run -it hulkinbrain/docker-opencv2 bash
    
**And to test the installed libraries, run the following commands after running the above command:**<br>
_OpenCV installation is being checked by the following commands_

    # python
    >>> import cv2
    >>> print cv2.__version__
    2.4.13.3
