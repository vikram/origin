#
# This is an openvswitch image meant to enable OpenShift OVS based SDN
#
# The standard name for this image is openshift/openvswitch
#
FROM openshift/node

COPY scripts/* /usr/local/bin/

RUN INSTALL_PKGS="openvswitch" && \
    rpm -V $INSTALL_PKGS

LABEL io.k8s.display-name="OpenShift Origin OpenVSwitch Daemon" \
      io.k8s.description="This is a component of OpenShift Origin and runs an OpenVSwitch daemon process."
VOLUME /etc/openswitch
ENV HOME /root

# files required to run as a system container
COPY system-container/system-container-wrapper.sh /usr/local/bin/
COPY system-container/config.json.template system-container/service.template /exports/

ENTRYPOINT ["/usr/local/bin/ovs-run.sh"]
