FROM docker.io/fedora:23

MAINTAINER Dominic McGinnis, dominic_mcginnis@yahoo.com

ENV JAVA_VER 1.8.0_72
ENV JAVA_DWL_VER 8u72
ENV JAVA_DWL_BVER b15

ENV JAVA_HOME /usr/java64/current
ENV JDK_HOME ${JAVA_HOME}
ENV PATH ${JAVA_HOME}/bin:${PATH}

ENV		JMETER_VERSION	2.13
ENV		JMETER_HOME	/opt/jmeter
ENV		JMETER_DOWNLOAD_URL  http://apache-mirror.rbc.ru/pub/apache/jmeter/binaries/apache-jmeter-${JMETER_VERSION}.tgz

# Install utilities
RUN dnf update -y && dnf install -y unzip wget tar

# Install Java
RUN mkdir /usr/java64 ; cd /usr/java64/ ; \
     wget --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/${JAVA_DWL_VER}-${JAVA_DWL_BVER}/jdk-${JAVA_DWL_VER}-linux-x64.tar.gz && \
     cd /usr/java64/ && tar -xzf jdk-${JAVA_DWL_VER}-linux-x64.tar.gz && rm jdk-${JAVA_DWL_VER}-linux-x64.tar.gz && \
     cd /usr/java64/ && ln -s jdk${JAVA_VER} current && \
     chown -R root:root /usr/java64 && \
     chmod -R a+rwX /usr/java64

# download and extract jmeter 
RUN		mkdir -p ${JMETER_HOME} && \
		mkdir -p ${JMETER_HOME}/tests && \
		mkdir -p ${JMETER_HOME}/results && \
		curl -L --silent ${JMETER_DOWNLOAD_URL} | tar -xz --strip=1 -C ${JMETER_HOME} && \
		curl -L --silent http://jmeter-plugins.org/downloads/file/JMeterPlugins-Standard-1.3.1.zip -o /tmp/jmeter-plugins-standard.zip && \
		unzip -o -d /opt/jmeter/ /tmp/jmeter-plugins-standard.zip && \
		rm /tmp/jmeter-plugins-standard.zip && \
		curl -L --silent http://jmeter-plugins.org/downloads/file/JMeterPlugins-ExtrasLibs-1.3.1.zip -o /tmp/jmeter-plugins-ExtrasLibs.zip && \
		unzip -o -d /opt/jmeter/ /tmp/jmeter-plugins-ExtrasLibs.zip && \
		rm /tmp/jmeter-plugins-ExtrasLibs.zip && \
		chmod -R 777 ${JMETER_HOME} 

WORKDIR		${JMETER_HOME}
