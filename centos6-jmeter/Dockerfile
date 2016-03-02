FROM sergeyzh/centos6-java:jdk8

MAINTAINER Dominic McGinnis, dominic_mcginnis@yahoo.com

ENV		JMETER_VERSION	2.13
ENV		JMETER_HOME	/opt/jmeter
ENV		JMETER_DOWNLOAD_URL  http://apache-mirror.rbc.ru/pub/apache/jmeter/binaries/apache-jmeter-${JMETER_VERSION}.tgz
ENV 	DISPLAY :1.5

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
