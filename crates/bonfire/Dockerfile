# Build Stage
FROM ghcr.io/revoltchat/base@sha256:7b8c4e9d15e22f2d5d1e3b6b0bd01ffa206f72078521628044f111529c54794b AS builder

# Bundle Stage
FROM debian:bullseye-slim
RUN apt-get update && \
    apt-get install -y ca-certificates && \
    apt-get clean
COPY --from=builder /home/rust/src/target/release/revolt-bonfire ./
EXPOSE 9000
CMD ["./revolt-bonfire"]
