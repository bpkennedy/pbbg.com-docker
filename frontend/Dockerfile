FROM node:lts-alpine as build-stage
RUN mkdir -p /app
WORKDIR /app
ADD . /app
RUN yarn --silent && \
    yarn run build && \
    yarn cache clean

FROM nginx as production-stage
RUN mkdir /app
COPY --from=build-stage /app/dist /app
