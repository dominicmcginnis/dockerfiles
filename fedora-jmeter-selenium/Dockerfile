FROM dmcginnis/fedora-jmeter

MAINTAINER Dominic McGinnis, dominic_mcginnis@yahoo.com

ENV 	DISPLAY :99.0

# Setup Xvfb and chrome driver
RUN dnf install -y xorg-x11-server-Xvfb

# Install chrome
ADD google-chrome.repo /etc/yum.repos.d/.
RUN dnf install -y google-chrome-stable
RUN dnf install -y libexif-gtk2.x86_64

# Install chrome driver
RUN	curl -L --silent http://chromedriver.storage.googleapis.com/2.21/chromedriver_linux64.zip -o /tmp/chromedriver_linux64.zip && \
	unzip -o -d /opt/google/chrome /tmp/chromedriver_linux64.zip && \
	rm /tmp/chromedriver_linux64.zip

# Add JMeter Webdriver
RUN		curl -L --silent http://jmeter-plugins.org/downloads/file/JMeterPlugins-WebDriver-1.3.1.zip -o /tmp/jmeter-plugins-WebDriver.zip && \
		unzip -o -d /opt/jmeter/ /tmp/jmeter-plugins-WebDriver.zip && \
		rm /tmp/jmeter-plugins-WebDriver.zip && \
		rm ${JMETER_HOME}/lib/httpcore-4.2.5.jar && \
		rm ${JMETER_HOME}/lib/httpclient-4.2.6.jar && \
		rm ${JMETER_HOME}/lib/httpmime-4.2.6.jar

# Setup dbus correctly
RUN dbus-uuidgen > /etc/machine-id

# Install python selenium for stand-alone selenium testing (non-jmeter)
RUN pip install selenium

RUN export DISPLAY=:99.0

WORKDIR ~

# Reset root user password
RUN echo 'root:bobafett' | chpasswd

# CMD to run the virtual screen
CMD Xvfb :99 -screen 0 1024x768x16 &> xvfb.log &

