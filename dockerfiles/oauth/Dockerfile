FROM debian:12.2-slim

RUN apt update && \
  apt install curl && \
  curl -fsSL https://deb.nodesource.com/setup_16.x | sudo -E bash - && \
  apt install nodejs

RUN git clone https://github.com/vencax/netlify-cms-github-oauth-provider.git oauth
RUN cd oauth
RUN npm install

ENV PORT=3000
ENV ORIGINS=ingenjorsarbeteforklimatet.se/greenhouse-majorna/admin/

ENTRYPOINT npm start
