FROM trumandk/gobuilder AS builder

WORKDIR /app/
RUN git clone https://github.com/go-oauth2/oauth2.git
WORKDIR /app/oauth2/example/server/
COPY server.go server.go
RUN CGO_ENABLED=0 go build -o /main

FROM scratch
WORKDIR /
COPY static /static/
COPY --from=builder /main /main
ENTRYPOINT ["/main"]
