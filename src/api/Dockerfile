FROM golang:1.19 AS civoTest

WORKDIR /go/src

COPY go.sum .

COPY go.mod .

RUN go get -d || true

COPY . .

RUN mkdir -p ${HOME}/.ksctl/config/civo && \
mkdir -p ${HOME}/.ksctl/cred && \
touch ${HOME}/.ksctl/cred/civo


WORKDIR /go/src/civo

CMD ["go", "test", "-v", "."]


FROM golang:1.19 AS localTest

WORKDIR /go/src

COPY go.sum .

COPY go.mod .

RUN go get -d || true

COPY . .

RUN mkdir -p ${HOME}/.ksctl/config/local

WORKDIR /go/src/local

CMD ["go", "test", "-v", "."]

