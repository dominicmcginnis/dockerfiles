FROM nodesource/fedora22:5.5.0

MAINTAINER Dominic McGinnis, dominic_mcginnis@yahoo.com

ENV 	DISPLAY :99.0
ENV 	CHROME_BIN /opt/google/chrome/google-chrome

# Setup Xvfb and chrome driver
RUN dnf install -y xorg-x11-server-Xvfb

# Install chrome
ADD google-chrome.repo /etc/yum.repos.d/.
RUN dnf install -y google-chrome-stable
RUN dnf install -y libexif-gtk2.x86_64
RUN dnf install -y sudo

# Remove unwanted packages to reduce image size
RUN dnf remove -y man

# Cleanup dnf cache to reduce image size
RUN dnf clean all

# Setup dbus correctly
RUN dbus-uuidgen > /etc/machine-id

RUN export DISPLAY=:99.0
