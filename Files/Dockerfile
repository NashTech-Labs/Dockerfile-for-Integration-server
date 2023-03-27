# Base image
FROM centos:7

# Update the packages
RUN yum -y update

# This step will install required packages
RUN yum -y install wget unzip

# This step will download and install Java
RUN wget --no-cookies --no-check-certificate \
    --header "Cookie: oraclelicense=accept-securebackup-cookie" \
    "https://download.oracle.com/otn-pub/java/jdk/8u211-b12/2787e4a523244c269598db4e85c51e0c/jdk-8u211-linux-x64.rpm" \
    -O /tmp/jdk-8u211-linux-x64.rpm \
    && yum -y localinstall /tmp/jdk-8u211-linux-x64.rpm \
    && rm -f /tmp/jdk-8u211-linux-x64.rpm

# Download and install webMethods Integration Server
RUN wget -O /tmp/SoftwareAGInstaller20191216_linuxamd64.sh "https://download2.softwareag.com/SoftwareAG/webmethods/10-5/SoftwareAGInstaller20191216_linuxamd64.sh" \
    && chmod +x /tmp/SoftwareAGInstaller20191216_linuxamd64.sh \
    && /tmp/SoftwareAGInstaller20191216_linuxamd64.sh -i silent -f /tmp/ISInstallResponseFile.txt \
    && rm -f /tmp/SoftwareAGInstaller20191216_linuxamd64.sh

# Expose port 5555 for IS administration console
EXPOSE 5555

# Set environment variables for IS
ENV SAG_HOME=/opt/softwareag
ENV IS_DIR=$SAG_HOME/IntegrationServer
ENV PATH=$PATH:$JAVA_HOME/bin:$IS_DIR/bin

# Start IS server
CMD ["sh", "-c", "cd $IS_DIR/bin && ./server.sh"]
