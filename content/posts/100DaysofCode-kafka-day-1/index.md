---
title: "#100DaysofCode Kafka | Day 1"
date: 2022-07-20T12:37:03+07:00
draft: false
tags: [100DaysofCode, kafka]
---

## Membuat kafka cluster

Hari pertama saya mengikuti langkah-langkah membuat cluster kafka di platform confluent cloud dengan nama `cluster_0`.

![kafka cluster](images/kafka-cluster.png)

## Membuat satu topic

Lalu saya membuat satu topic dengan single partition bernama `quickstart`.

![Kafka Topic](images/kafka-topic.png)

Jika ingi membuat topic melalui cli berikut adalah perintahnya

```bash
./bin/kafka-topics --bootstrap-server localhost:9092 \
                   --create \
                   --topic quickstart
```

## Mengirim pesan ke topic

Setelah berhasil membuat topic, saya mencoba mempublish simple message berisikan

```json
{
  "hello": "world"
}
```

![Mengirim pesan kafka](https://images.ctfassets.net/gt6dp23g0g38/iDlE9aABQ3EGUeFwvHP1C/c61b761dcf2373e3552dfa00bcf039c6/cc-write-message-topic-3.jpg)

Untuk mengirim pesan melalui cli berikut adalah perintahnya

```bash
./bin/kafka-console-producer --bootstrap-server localhost:9092 \
                             --topic quickstart
```

Tuliskan pesan yang mau di kirimkan

```
this is my first kafka message
hello world!
this is my third kafka message. I’m on a roll :-D
```

Jika sudah selesai, tekan **Ctrl-D** untuk kembali ke cli

## Membaca pesan dari sebuah topic

setalah berhasil mengirimkan message ke topic `quickstart` saya mencoba untuk membaca message tersebut.

![Membaca pesan kafka](https://images.ctfassets.net/gt6dp23g0g38/5AQ1VGjh9l70jhre0GHIUA/dc56176bcba87a8f160e1beb388c7d6b/cc-read-message-view.jpg)

![Membaca pesan kafka](https://images.ctfassets.net/gt6dp23g0g38/3Z8lsd9c56s755om94kHU1/b904a3af32f4fbc29f2255eaea8820b2/cc-read-message-view-topic.jpg)

Untuk membaca pesan melalu cli jalankan perintah berikut untuk membuka `kafka-console-consumer`

```bash
./bin/kafka-console-consumer --bootstrap-server localhost:9092 \
                             --topic quickstart \
                             --from-beginning
```

Maka kita akan mendapatkan pesan yang telah di inputkan tadi sama seperti step sebelumnya

```
this is my first kafka message
hello world!
this is my third kafka message. I’m on a roll :-D
```

## Kesimpulan

Untuk progress di hari pertama ini memang masih basic karena saya ingin merefresh ingatan saya mengenai kafka.
