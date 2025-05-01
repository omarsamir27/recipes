LABEL authors="omarsamir27"

FROM mikefarah/yq:latest AS yq
FROM bitnami/kubectl:latest AS kubectl

FROM alpine:latest AS upx
RUN apk add --no-cache upx
WORKDIR /tmp
COPY --from=yq /usr/bin/yq .
COPY --from=kubectl /opt/bitnami/kubectl/bin/kubectl .
RUN upx -9 -o yq-small yq  && \
    upx -9 -o kubectl-small kubectl



FROM alpine:latest

COPY --from=upx /tmp/yq-small /usr/bin/yq
COPY --from=upx /tmp/kubectl-small /usr/bin/kubectl

