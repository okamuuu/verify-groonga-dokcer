FROM groonga/groonga:latest

RUN mkdir -p /app/groonga/db
WORKDIR /app/groonga

EXPOSE 10041

CMD ["--protocol", "http", "-s", "-n", "./db/groonga.db"]
