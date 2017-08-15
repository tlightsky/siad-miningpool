FROM golang:1.8.3-alpine3.6

RUN apk update && \
    apk upgrade && \
    apk add git make socat

RUN go-wrapper download -u github.com/NebulousLabs/Sia/...  # "go get -d -v ./..."

WORKDIR /go/src/github.com/NebulousLabs/Sia

RUN git remote add petabyte-storage https://github.com/petabyte-storage/Sia.git
RUN git fetch petabyte-storage
RUN git checkout -b ps-pool petabyte-storage/master
RUN make release-std

EXPOSE 3333

ENTRYPOINT siad --modules=pcgt --no-bootstrap --sia-directory=/var/sia-data