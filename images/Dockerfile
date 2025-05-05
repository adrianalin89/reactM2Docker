FROM node:18


WORKDIR /app

RUN corepack enable && \
    corepack prepare yarn@4.1.1 --activate && \
    yarn config set --home enableTelemetry 0

#RUN yarn install
#RUN yarn build

EXPOSE 3000
USER node
#CMD ["yarn", "start"]
CMD ["tail", "-f", "/dev/null"]