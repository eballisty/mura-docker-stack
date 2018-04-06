# can pin this to a specific version
# (for example, blueriver/mura:7.1.190)
FROM blueriver/mura:latest

ARG admin_hspw=
ARG web_hspw=

RUN sed -i "s/hspw=\"\"/hspw=\"$admin_hspw\"/" /opt/lucee/server/lucee-server/context/lucee-server.xml \
	&& sed -i "s/hspw=\"\"/hspw=\"$web_hspw\"/" /opt/lucee/web/lucee-web.xml.cfm

# Copy Mura files
COPY . /var/www

# Add healthcheck
HEALTHCHECK --start-period=3m CMD curl --fail http://localhost:8888/?healthcheck || exit 1
