FROM debian:12.2-slim

RUN apt-get update && \
  apt-get install -y curl && \
  curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash - && \
  apt-get install -y nodejs

RUN git clone https://github.com/vencax/netlify-cms-github-oauth-provider.git oauth
RUN cd oauth
RUN npm install

ENV PORT=3000
ENV ORIGINS=ingenjorsarbeteforklimatet.se/greenhouse-majorna/admin/

ENTRYPOINT npm start
