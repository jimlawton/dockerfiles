FROM jlawton/python-dev
MAINTAINER Jim Lawton

RUN apt-get -y update

RUN apt-get -y install libgtk2.0-dev
RUN apt-get -y install libavcodec-dev
RUN apt-get -y install libavformat-dev
RUN apt-get -y install libswscale-dev
RUN apt-get -y install libtbb2
RUN apt-get -y install libtbb-dev
RUN apt-get -y install libjpeg-dev
RUN apt-get -y install libpng-dev
RUN apt-get -y install libtiff-dev
RUN apt-get -y install libjasper-dev
RUN apt-get -y install libdc1394-22-dev

# Install OpenCV.
RUN git clone https://github.com/opencv/opencv.git 
RUN git clone https://github.com/opencv/opencv_contrib.git 
RUN cd /opencv && git checkout 3.1.0
RUN cd /opencv_contrib && git checkout 3.1.0
#RUN mkdir /opencv
#COPY ./opencv /opencv
#RUN mkdir /opencv_contrib
#COPY ./opencv_contrib /opencv_contrib
RUN cd /opencv && mkdir build && cd build && cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local -D INSTALL_C_EXAMPLES=OFF -D INSTALL_PYTHON_EXAMPLES=ON -D OPENCV_EXTRA_MODULES_PATH=../../opencv_contrib/modules -D BUILD_EXAMPLES=ON .. && make -j4 && make install && ldconfig

# Install Tesseract.
RUN apt-get -y install tesseract-ocr

# Install PythonMagick.
RUN apt-get -y install python-pythonmagick

RUN pip install PyPDF2
RUN pip install numpy
RUN pip install Pillow
RUN pip install scipy
RUN pip install pytesseract
RUN pip install mime

# Install doc2text.
RUN git clone https://github.com/jlsutherland/doc2text.git
#RUN mkdir /doc2text
#COPY . /doc2text
RUN cd /doc2text && python setup.py install
