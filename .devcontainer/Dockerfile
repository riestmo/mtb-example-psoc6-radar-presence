ARG VARIANT="stable"
FROM riestere/modus-linux-30:${VARIANT}

USER root
RUN mkdir /home/vscode
WORKDIR /home/vscode

RUN groupadd -r vscode && \
    useradd --no-log-init -r -g vscode -s /bin/bash vscode && \
    chown -R vscode /home/vscode

USER vscode

RUN mkdir /home/vscode/mtb-workspace
RUN mkdir /home/vscode/mtb-workspace/mtb-example-psoc6-radar-presence
WORKDIR /home/vscode/mtb-workspace/mtb-example-psoc6-radar-presence

COPY --chown=vscode:vscode . .

ARG TARGET="CYSBSYSKIT-DEV-01"
RUN /opt/ModusToolbox/tools_3.0/library-manager/library-manager-cli -p . --add-bsp-name ${TARGET}