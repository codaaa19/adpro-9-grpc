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

- Trait + Module : 

