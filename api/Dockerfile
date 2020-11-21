FROM alpine:3.11 as fetch-src
RUN apk add --update --no-cache git
RUN git clone --depth 1 https://github.com/oldboyxx/jira_clone.git

FROM node:12-alpine
COPY --from=fetch-src /jira_clone/api/package* /api/
WORKDIR /api
RUN npm ci
RUN npm i -g pm2
COPY --from=fetch-src /jira_clone/api /api
RUN npm run build
EXPOSE 3000
CMD ["pm2-runtime", "start", "--name", "'jira_api'", "node", "--", "-r", "./tsconfig-paths.js", "build/index.js"]