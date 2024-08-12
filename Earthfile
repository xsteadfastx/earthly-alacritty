VERSION 0.6
ARG VERSION=0.13.2
FROM rust:1.74.0-bullseye

install-deps:
	FROM +base
	RUN set -ex \
		&& apt-get update \
		&& apt-get install -y \
				cmake \
				pkg-config \
				libfreetype6-dev \
				libfontconfig1-dev \
				libxcb-xfixes0-dev \
				python3 \
				git

code:
	FROM +base
	GIT CLONE https://github.com/alacritty/alacritty.git code
	RUN (cd code; git switch -c $VERSION)
	SAVE ARTIFACT code

build:
	FROM +install-deps
	ENV RUSTFLAGS='-C link-arg=-s'
	COPY +code/code code
	WORKDIR /code
	RUN cargo build --release
	SAVE ARTIFACT target/release/alacritty alacritty
