FROM debian:12.2-slim

ENV NODE_MAJOR=20
RUN apt-get update && \
    apt-get install -y ca-certificates curl gnupg git && \
    mkdir -p /etc/apt/keyrings && \
    curl -fsSL https://deb.nodesource.com/gpgkey/nodesource-repo.gpg.key | gpg --dearmor -o /etc/apt/keyrings/nodesource.gpg
RUN echo "deb [signed-by=/etc/apt/keyrings/nodesource.gpg] https://deb.nodesource.com/node_$NODE_MAJOR.x nodistro main" | tee /etc/apt/sources.list.d/nodesource.list
RUN apt-get update && \
    apt-get install nodejs -y

RUN git clone https://github.com/vencax/netlify-cms-github-oauth-provider.git oauth
RUN cd oauth
RUN npm install

ENV PORT=3000
ENV ORIGINS=ingenjorsarbeteforklimatet.se/greenhouse-majorna/admin/

ENTRYPOINT npm start
