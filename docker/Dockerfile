FROM golang:alpine as go_builder
COPY http.go /go/http.go
RUN CGO_ENABLED=0 GOOS=linux go build -a -installsuffix cgo -o /go/bin/http http.go

FROM scratch
COPY --from=go_builder /go/bin/http /
COPY helm /helm
ENV PORT=8080
EXPOSE 8080
ENTRYPOINT ["/http"]