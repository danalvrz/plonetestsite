ARG PLONE_VERSION=6.0.0rc2
FROM plone/plone-backend:${PLONE_VERSION}

LABEL maintainer="Plone Foundation <collective@plone.org>" \
      org.label-schema.name="plonetestsite-backend" \
      org.label-schema.description="PloneTestSite backend image." \
      org.label-schema.vendor="Plone Foundation"

# Add local code
COPY . .

# Install local requirements and fix permissions
RUN ./bin/pip install mxdev \
    && mv requirements-docker.txt requirements.txt \
    && ./bin/mxdev -c mx.ini \
    && ./bin/pip install -r requirements-mxdev.txt \
    && chown -R plone: /app
