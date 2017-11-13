FROM groonga/groonga:latest

# Add the patch fix
COPY stack-fix.c /lib/

# Prepare the libraries packages
RUN set -ex \
    && apk add --no-cache  --virtual .build-deps build-base \
    && gcc  -shared -fPIC /lib/stack-fix.c -o /lib/stack-fix.so \
    && apk del .build-deps

# export the environment variable of LD_PRELOAD
ENV LD_PRELOAD /lib/stack-fix.so

RUN mkdir -p /app/groonga/db
WORKDIR /app/groonga

EXPOSE 10041

CMD ["--protocol", "http", "-s", "-n", "./db/groonga.db"]
