# Build Stage
FROM ghcr.io/revoltchat/base:latest AS builder

# Bundle Stage
FROM debian:bullseye-slim
RUN apt-get update && \
    apt-get install -y ca-certificates wget && \
    wget https://www.openssl.org/source/openssl-3.0.11.tar.gz && \
    tar -xvzf openssl-3.0.11.tar.gz && \
    cd openssl-3.0.11 && \
    ./config && \
    make && \
    make install && \
    apt-get clean && \
    rm -rf openssl-3.0.11.tar.gz openssl-3.0.11
COPY --from=builder /home/rust/src/target/release/revolt-delta ./

EXPOSE 8000
ENV ROCKET_ADDRESS 0.0.0.0
ENV ROCKET_PORT 8000
CMD ["./revolt-delta"]
