FROM golang:1.16 as build

RUN apt-get update && apt-get install -y ninja-build

# TODO: Змініть на власну реалізацію системи збірки
WORKDIR /go/src
RUN git clone https://github.com/KabirLabibIP84/lab1.1
WORKDIR /go/src/se-lab1
RUN go get -u ./build/cmd/bood

WORKDIR /go/src/se-lab2
COPY . .

RUN CGO_ENABLED=0 bood

# ==== Final image ====
FROM alpine:3.11
WORKDIR /opt/se-lab2
COPY entry.sh ./
COPY --from=build /go/src/labb2/tree/main/lab2.2/out/bin/* ./
ENTRYPOINT ["/opt/lab2.2/entry.sh"]
CMD ["server"]
