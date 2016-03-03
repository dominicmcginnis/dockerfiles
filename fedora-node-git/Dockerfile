FROM nodesource/fedora22:5.5.0

MAINTAINER Dominic McGinnis, dominic_mcginnis@yahoo.com

# Add git and prep for SSH keys
RUN dnf install -y git

# Make ssh dir
RUN mkdir /root/.ssh/

# Create known_hosts
RUN touch /root/.ssh/known_hosts
