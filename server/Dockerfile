#FROM golang:1.15.8-alpine3.13 AS builder
FROM trumandk/gobuilder AS builder

#RUN apk update
#RUN apk add --no-cache git
#RUN apk --no-cache add ca-certificates
WORKDIR /app/
RUN git clone https://github.com/go-oauth2/oauth2.git
WORKDIR /app/oauth2/example/server/
#RUN cat server.go
#RUN go get github.com/go-oauth2/oauth2/
COPY server.go server.go
#RUN go get golang.org/x/sys/unix
#RUN go get github.com/docker/docker/client
#RUN go get github.com/gorilla/securecookie
#RUN go get github.com/elastic/go-elasticsearch
#RUN go get github.com/jtblin/go-ldap-client
#RUN go get gopkg.in/ldap.v3
#RUN go get github.com/caddyserver/certmagic
#RUN go get github.com/cretz/bine/tor
#RUN go get github.com/go-oauth2/oauth2/
#RUN go get golang.org/x/oauth2
#RUN go get github.com/dgrijalva/jwt-go
#RUN go get github.com/go-session/session
#RUN go version
#RUN go get github.com/go-oauth2/oauth2/v4/...
#COPY go.sum go.sum
#COPY go.mod go.mod
#RUN wget https://raw.githubusercontent.com/go-oauth2/oauth2/v4.2.0/go.mod
#COPY server.go server.go
RUN CGO_ENABLED=0 go build -o /main


FROM scratch
WORKDIR /
COPY static /static/
COPY --from=builder /main /main
ENTRYPOINT ["/main"]
