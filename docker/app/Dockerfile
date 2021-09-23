# TODO change here
ARG REPO_NAME="go-template"
ARG APP_NAME="app"

FROM golang:1.17 as build
ARG REPO_NAME
ARG APP_NAME
COPY . /go/src/${REPO_NAME}
WORKDIR /go/src/${REPO_NAME}
RUN go build -o /go/bin/${APP_NAME} ./cmd/${APP_NAME}

FROM gcr.io/distroless/base
ARG APP_NAME
COPY --from=build /go/bin/${APP_NAME} /${APP_NAME}
CMD ["/app"]