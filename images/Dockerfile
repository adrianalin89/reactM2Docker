FROM node:18 AS builder
WORKDIR /app
COPY package.json yarn.lock ./
RUN yarn install
COPY . .
RUN yarn build

FROM node:16
ARG USER_ID
ARG GROUP_ID
RUN groupadd -g ${GROUP_ID} appuser
RUN useradd -u ${USER_ID} -g appuser -m /app appuser
COPY --from=builder /app/.next /app/.next
COPY --from=builder /app/node_modules /app/node_modules
COPY --from=builder /app/package.json /app/package.json
RUN chown -R appuser:appuser /app
WORKDIR /app
EXPOSE 3000
USER appuser
CMD ["yarn", "start"]