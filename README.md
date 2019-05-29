# Scap

##Install oscap-docker
yum install openscap-utils


docker run --name "our-rhel7-container" -ti registry.access.redhat.com/rhel7 /bin/bash

docker run --name "our-openjdk-container" -ti registry.redhat.io/redhat-openjdk-18/openjdk18-openshift /bin/bash

oscap-docker container-cve our-rhel7-container

yum install scap-security-guide

oscap-docker container our-rhel7-container oval eval \
               --results oval-results.xml --report report.html \
               /usr/share/xml/scap/ssg/content/ssg-rhel7-oval.xml
			   
			   
oscap-docker image registry.access.redhat.com/rhel7 oval eval \
               --results oval-results.xml --report report.html \
               /usr/share/xml/scap/ssg/content/ssg-rhel7-oval.xml 
			   
oscap-docker image registry.redhat.io/redhat-openjdk-18/openjdk18-openshift oval eval --results oval-results.xml --report report-openjdk.html /usr/share/xml/scap/ssg/content/ssg-rhel7-oval.xml 
