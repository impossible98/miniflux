FROM golang:alpine AS alpha

RUN apk add --no-cache --update git make

WORKDIR /app

ADD . /app

RUN make build

FROM alpine

EXPOSE 1201

ENV LISTEN_ADDR 0.0.0.0:1201

RUN apk --no-cache add ca-certificates tzdata

COPY --from=alpha /app/dist/miniflux /dist/miniflux

CMD ["/dist/miniflux"]
