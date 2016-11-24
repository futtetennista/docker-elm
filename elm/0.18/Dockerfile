# nvm instead of nodejs since elm-oracle looks for the node executable
# More info here: http://stackoverflow.com/a/24592328/389262

FROM haskell:7.10.3

MAINTAINER Michael Porter <mike@codesimple.net>

ENV ELM_VER=0.18

RUN apt-get update && apt-get install -y \
   curl \
   git \
   libtinfo-dev \
   nvm \
   npm

ENV PATH /opt/Elm-Platform/$ELM_VER/.cabal-sandbox/bin:$PATH

WORKDIR /opt

RUN nvm install 6.9.1

RUN curl https://raw.githubusercontent.com/elm-lang/elm-platform/11c8ecb81a58b82a25c90145418cd70fa61d1679/installers/BuildFromSource.hs > BuildFromSource.hs

RUN runhaskell BuildFromSource.hs $ELM_VER

RUN npm install -g elm-oracle

ENTRYPOINT ["elm"]
