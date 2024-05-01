## TSABIT CODA RAFISUKMAWAN 2206081414

## TUTORIAL 9 

## 1. What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable?

- Unary : Client memberikan 1 request ke server dan server mengirimkan 1 response pada client.

- Server streaming :  Client memberikan 1 request ke server dan server mengirimkan aliran response pada client.

- Bi-directional streaming : Client dan server mengirimkan response secara bersamaan (komunikasi)

## 2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption?  

- Auth : Memastikan bahwa hanya kalian yg terotentikasi yang dapat mengakses laman (penggunaan JWT dapat menjadi opsi)

- Enkripsi : grpc menggunakan TLS/SSL yang dapat mengamankan data yang dikirim melalui jaringan.

- Input validation : Menghindari adanya sql injection.

## 3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications? 

- Manejemen state : Menjaga state yang sesuai dan konsisten pada 2 sisi koneksi

- Pemeliharaan koneksi : Menjaga koneksi tetap hidup + mengelola ulang koneksi yang error.

- Penggunaan resource : Streaming dapat menguras CPU dan memory

## 4. What are the advantages and disadvantages of using the `tokio_stream::wrappers::ReceiverStream` for streaming responses in Rust gRPC services?  

- (+) Memudahkan receiver menjadi stream sehingga dapat digunakan oleh grpc. Hal tersebut membuat pengiriman data streaming lebih sederhana.

- (-) Dapat menjadi kurang efisien jika penggunaannya belum sesuai.

## 5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time?  

Untuk menjaga agar layanan gRPC di Rust dapat dikembangkan dan dipelihara dengan efektif, gunakan perpustakaan yang sudah ada untuk mengulang penggunaan dan merawat kode. Terapkan struktur modular dengan mengorganisir kode ke dalam modul yang berbeda yang memiliki tanggung jawab yang spesifik, serta gunakan fitur yang memungkinkan penciptaan antarmuka yang bisa digunakan kembali.

## 6. In the **MyPaymentService** implementation, what additional steps might be necessary to handle more complex payment processing logic?  

Untuk mengelola logika pemrosesan pembayaran yang lebih rumit, MyPaymentService bisa diperbaiki dengan merubah metode process_payment menjadi server streaming. Hal ini memungkinkan pengiriman data yang kompleks secara bertahap dan lebih efisien kepada klien.

## 7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms?  

Adopsi gRPC sebagai protokol komunikasi sangat mempengaruhi arsitektur sistem terdistribusi. gRPC mengeliminasi kebutuhan pemikiran modul akses melalui HTTP, dengan otomatis mengatur koneksi untuk pemanggilan metode yang diinginkan melalui kesepakatan file proto. Ini memungkinkan klien memanggil fungsi server seolah berinteraksi langsung, memfasilitasi konektivitas dan operasi lintas teknologi, platform, dan sistem, serta meningkatkan interoperabilitas dalam arsitektur sistem yang kompleks.

## 8. What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs?  

HTTP/2 memiliki keunggulan atas HTTP/1.1 dan WebSocket dengan fitur seperti multiplexing untuk permintaan bersamaan, server push, kompresi header, protokol biner, dan prioritas aliran yang meningkatkan efisiensi dan manajemen sumber daya. Namun, ini juga menambah kompleksitas implementasi, overhead enkripsi, masalah kemacetan TCP, dan isu kompatibilitas browser. Sementara itu, WebSocket cocok untuk komunikasi dua arah real-time melalui satu koneksi TCP, sedangkan HTTP/2 lebih efektif untuk aplikasi web dengan banyak transaksi kecil.

## 9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness?

REST API sederhana menggunakan metode HTTP standar dan bersifat stateless untuk kemudahan penggunaan tetapi tidak mendukung komunikasi real-time, sering bergantung pada polling yang menambah latensi dan kerumitan. Sebaliknya, gRPC mendukung streaming dua arah, memungkinkan klien dan server untuk bertukar data secara mandiri, ideal untuk skenario real-time dan meningkatkan responsiveness. Meski lebih kompleks, streaming gRPC bisa memberikan kinerja lebih baik dan manfaat komunikasi real-time dibandingkan dengan REST API dalam beberapa kasus.

## 10. What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads?  



