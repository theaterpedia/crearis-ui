FROM node:16-alpine AS build

WORKDIR /var/www

RUN apk add --no-cache yarn
# needed because of turbo issue
# see: https://github.com/vercel/turbo/issues/2309#issuecomment-1288660455
RUN apk add --no-cache libc6-compat

ARG VITE_DOCS_BASEPATH
ARG VITE_DOCS_EXAMPLES_REACT_PATH
ARG VITE_DOCS_EXAMPLES_VUE_PATH
ARG ENVIRONMENT

ENV VITE_DOCS_BASEPATH=$VITE_DOCS_BASEPATH
ENV VITE_DOCS_EXAMPLES_REACT_PATH=$VITE_DOCS_EXAMPLES_REACT_PATH
ENV VITE_DOCS_EXAMPLES_VUE_PATH=$VITE_DOCS_EXAMPLES_VUE_PATH
ENV ENVIRONMENT=$ENVIRONMENT

COPY . .
RUN yarn
RUN ENV_NAME=$ENVIRONMENT yarn build:replace-assets-url-with
RUN yarn build:peer-next
RUN yarn build:docs

FROM nginx
COPY --from=build /var/www/apps/docs/components/.vuepress/dist /usr/share/nginx/html/v2
COPY .vuestorefrontcloud/docs/default.conf /etc/nginx/conf.d/default.conf

