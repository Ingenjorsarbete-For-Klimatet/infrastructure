FROM node:lts-bookworm-slim

RUN git clone https://github.com/vencax/netlify-cms-github-oauth-provider.git oauth
RUN cd oauth && \
    git checkout 1.0.0
WORKDIR oauth
RUN npm install

CMD [ "npm", "start" ]