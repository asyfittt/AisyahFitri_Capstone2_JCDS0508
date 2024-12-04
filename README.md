# **Pendahuluan**
<p>Industri transportasi di New York City, khususnya dalam layanan taksi dan transportasi berbasis aplikasi, menghadapi tantangan terkait dengan pengelolaan armada, dan efisiensi operasional. Dari analisis pola perjalanan yang dilakukan, ditemukan beberapa tren yang menunjukkan bahwa volume perjalanan cenderung meningkat pada jam sibuk pagi dan sore, dengan puncaknya pada hari Selasa. Selain itu, faktor-faktor seperti jarak perjalanan, durasi, dan jenis pemesanan memiliki pengaruh yang signifikan terhadap jumlah tip yang diterima pengemudi. Oleh karena itu, penting bagi berbagai stakeholder dalam ekosistem ini untuk memahami tren tersebut guna membuat keputusan yang lebih responsifberdasrkan data.

Pentingnya pemahaman ini bertujuan untuk memaksimalkan potensi pendapatan, meningkatkan pengalaman pengguna, serta mengoptimalkan alokasi armada dan pengelolaan infrastruktur. Dengan insight yang diberikan, perusahaan transportasi, otoritas transportasi kota, dan platform pemesanan transportasi dapat merancang strategi yang lebih tepat sasaran, baik dari sisi operasional maupun pelayanan pelanggan.</p>
# **Businees Objective**
- Menyusun strategi untuk mengalokasikan kendaraan dengan lebih tepat berdasarkan waktu dan lokasi dengan volume perjalanan tinggi.
- Menyediakan layanan yang lebih baik melalui penyesuaian algoritma pemesanan, fitur premium, dan pelatihan pengemudi.
- Memberikan wawasan dan insentif kepada pengemudi untuk meningkatkan tip dengan memahami faktor-faktor yang memengaruhi jumlah tip.
- Merancang kebijakan transportasi dan infrastruktur yang dapat mengakomodasi volume perjalanan yang tinggi, terutama di area-area dengan permintaan lebih besar.
# **Stakeholders**
Berikut ini rincian potensial stakeholders :
#### 1. Perusahaan Transportasi atau Operator Taksi
- Menggunakan wawasan tentang pola perjalanan untuk mengoptimalkan armada selama jam sibuk, hari tertentu, dan di lokasi strategis.
- **Manfaat**:
  - Mengurangi waktu tunggu pelanggan dengan alokasi kendaraan yang lebih baik.
  - Menyediakan pelatihan pengemudi tentang cara meningkatkan jumlah tip, seperti memanfaatkan rute tertentu atau meningkatkan layanan pelanggan pada perjalanan jarak jauh.

#### 2. Otoritas Transportasi Kota (seperti NYC Taxi and Limousine Commission)
- Otoritas transportasi dapat menggunakan data ini untuk merancang kebijakan yang meningkatkan efisiensi transportasi di New York City.
- **Manfaat**:
  - Mengembangkan strategi untuk mengurangi kemacetan selama jam sibuk di New York.
  - Meningkatkan infrastruktur di area dengan volume perjalanan tinggi.

#### 3. Pelanggan Korporat atau Perusahaan Teknologi Pemesanan Transportasi
- Platform pemesanan seperti Uber atau Lyft dapat memanfaatkan data untuk meningkatkan algoritma alokasi kendaraan dan pengalaman pelanggan.
- **Manfaat**:
  - Menyediakan opsi perjalanan yang disesuaikan dengan preferensi pelanggan, seperti estimasi durasi perjalanan atau area dengan tip lebih tinggi.
  - Menawarkan fitur promosi di hari dengan volume perjalanan tinggi, untuk meningkatkan loyalitas pelanggan.

 # **Data Understanding**
 Terdapat 2 jenis dataset yaitu:
- **NYC TLC Trip record (csv)** : data mentah yang merekam perjalanan taksi di New York City pada bulan Januari 2023.
- **Taxi zone lookup (csv)** : data ini mencakup nama wilayah dan zona yang terkait dengan setiap ID lokasi

Berikut ini, data spesifik untuk data set NYC TLC Trip record, yang mencakup:
- **VendorID** : Kode yang menunjukkan penyedia LPEP yang menyediakan record.<br>
1 = Creative Mobile Technologies, LLC. 2 = VeriFone Inc
- **lpep_pickup_datetime** : Tanggal dan waktu saat alat meter diaktifkan.
- **lpep_dropoff_datetime** : Tanggal dan waktu ketika alat meter dilepas.
- **passenger_count** : Jumlah penumpang di dalam kendaraan. Ini adalah nilai yang dimasukkan pengemudi.
- **trip_distance** : Jarak perjalanan yang ditempuh dalam **mil** dilaporkan oleh taksimeter.
- **PULocationID** : Zona Taksi TLC tempat argometer dipasang.
- **DOLocationID** : Zona Taksi TLC tempat argometer dimatikan.
- **RateCodeID** : Kode tarif akhir berlaku di akhir perjalanan.<br>
1=Standard rate; 2=JFK; 3=Newark; 4=Nassau or Westchester; 5=Negotiated fare; 6=Group ride
- **store_and_fwd_flag** : menunjukkan apakah catatan perjalanan disimpan dalam memori kendaraan sebelum dikirim ke vendor, alias "store and forward" karena kendaraan tidak memiliki koneksi ke server. <br>
Y = store and forward trip; N = not a store and forward trip
- **payment_type** : Kode numerik yang menunjukkan bagaimana penumpang membayar biaya perjalanan.<br>
1 = Credit card – Pembayaran dilakukan menggunakan kartu kredit.;
2 = Cash – Pembayaran dilakukan dengan uang tunai.;
3 = No charge  – Perjalanan ini tidak dikenakan biaya, bisa jadi karena merupakan perjalanan gratis atau kondisi lainnya;
4 = Dispute – Biaya perjalanan sedang diperselisihkan, biasanya terkait dengan masalah layanan atau pembayaran.;
5 = Unknown - Metode pembayaran atau status perjalanan tidak diketahui atau tidak tercatat;
6 = Voided trip - Perjalanan dibatalkan dan tidak ada biaya yang dikenakan.
- **fare_amount** : Tarif waktu dan jarak dihitung berdasarkan argo (Extra Miscellaneous extras and surcharges).Saat ini, biaya tambahan hanya berlaku untuk jam sibuk dan biaya menginap sebesar **$0,50 dan $1**.
- **extra** : Biaya tambahan. Saat ini, biaya tambahan yang dikenakan **hanya 0,5 dolar dan 1 dolar untuk jam sibuk dan larut malam.**
- **mta_tax** : Pajak MTA sebesar **$0,50** yang dipicu secara otomatis berdasarkan tarif terukur yang digunakan
- **improvement_surcharge** : Biaya perbaikan sebesar **$0,30** dibebankan pada perjalanan yang diberangkatkan pada saat flag drop. Biaya perbaikan mulai dikenakan pada tahun 2015.
- **tip_amount** : Kolom ini otomatis terisi untuk tip kartu kredit. **Tip tunai tidak termasuk.**
- **tolls_amount** : Jumlah total semua tol yang dibayarkan dalam perjalanan.
- **total_amount** : Jumlah total yang dibebankan kepada penumpang. **Tidak termasuk tip berupa uang tunai.**
- **trip_type** : Kode yang menunjukkan apakah perjalanan tersebut merupakan perjalanan street-hail atau dispatch, yang ditetapkan secara otomatis berdasarkan tarif argo yang digunakan, tetapi dapat diubah oleh pengemudi.<br>
1 = Street-hail (istilah yang digunakan untuk menggambarkan proses memanggil taksi langsung di jalan, tanpa menggunakan aplikasi atau sistem pemesanan sebelumnya);
2 = Dispatch (proses mengirimkan taksi ke pelanggan. Ketika seseorang memesan taksi, petugas akan memilih taksi yang tersedia dan mengirimkannya ke lokasi pelanggan. Proses ini bisa dilakukan lewat pusat panggilan atau aplikasi pemesanan taksi.)
- **congestion_surcharge** : Biaya kemacetan sebesar **$2,75** untuk **perjalanan taksi kuning dan hijau di southern Manhattan dari 96th Street** Biaya tambahan ini berlaku pada tahun 2019.<br>
Biaya tambahan tergantung pada jenis kendaraan yang digunakan:: 
    - Medallion taxicab: $2.50 per trip 
    - For-hire vehicle: $2.75 per trip 
