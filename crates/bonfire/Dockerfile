# Build Stage
FROM ghcr.io/revoltchat/base@sha256:f000fd94e2853b06747a1449962bacb233cfb195224854c00bbe6790444628ca AS builder

# Bundle Stage
FROM debian:bullseye-slim
RUN apt-get update && \
    apt-get install -y ca-certificates && \
    apt-get clean
COPY --from=builder /home/rust/src/target/release/revolt-bonfire ./
EXPOSE 9000
CMD ["./revolt-bonfire"]
