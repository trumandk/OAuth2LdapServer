FROM trumandk/gobuilder AS builder

WORKDIR /app/

COPY client.go client.go
RUN go get golang.org/x/oauth2
RUN CGO_ENABLED=0 go build -o /main

FROM scratch

COPY --from=builder /main /main
ENTRYPOINT ["/main"]
