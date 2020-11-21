FROM alpine:3.11 as fetch-src
RUN apk add --update --no-cache git
RUN git clone --depth 1 https://github.com/oldboyxx/jira_clone.git

FROM node:12-alpine
COPY --from=fetch-src /jira_clone/client/package* /client/
WORKDIR /client
RUN npm ci
RUN npm i -g pm2
COPY --from=fetch-src /jira_clone/client /client
RUN npm run build
EXPOSE 8080
CMD ["pm2-runtime", "start", "--name", "'jira_client'", "server.js"]