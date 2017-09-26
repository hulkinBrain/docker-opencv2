# Docker container for opencv2 and python

The docker image contains:

- OpenCV 2.4.13.3
- Python 2.7
- Numpy
- Matplotlib
- Pillow
- Virtualenv

If you want to add more dependencies, you can make changes to the requirements file

To test the docker image run the following command:

    docker run -it hulkinbrain/docker-opencv2 bash
    
And to test the installed libraries, run the following commands after running the above command:
_OpenCV installation is being checked by the following commands_

    # python
    >>> import cv2
    >>> print cv2.__version__
    2.4.13.3
