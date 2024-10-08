# Description: This file is used to build the devcontainer at runtime.
# Add additional dependencies below the `FROM` line as needed.

FROM ghcr.io/containercraft/devcontainer:latest

# Install additional dependencies by extending the base image
#ARG DEBIAN_FRONTEND=noninteractive
#ARG APT_PACKAGES="\
#"
#
#RUN set -ex \
#    && apt-get update \
#    && apt-get install -y $APT_PACKAGES \
#    && apt-get clean \
#    && rm -rf /var/lib/apt/lists/* \
#    && echo

# Install AWS CLI
RUN curl "https://awscli.amazonaws.com/awscli-exe-linux-$(uname -m).zip" -o "awscliv2.zip" \
    && unzip awscliv2.zip \
    && sudo ./aws/install \
    && rm -rf awscliv2.zip aws

# Install gRPCurl
RUN go install github.com/fullstorydev/grpcurl/cmd/grpcurl@latest
