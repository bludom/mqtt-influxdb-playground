# Multistage Go Build will be here
FROM "golang"
WORKDIR $GOPATH/src/app
COPY main.go .
RUN go get . && go build -o app .
RUN mkdir /app && cp app /app/

# Actual Image will be here
FROM alpine:latest  
RUN apk --no-cache add ca-certificates
WORKDIR /root/
COPY --from=0 /app/app .
CMD ["./app"]  