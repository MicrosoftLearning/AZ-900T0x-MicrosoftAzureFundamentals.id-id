---
wts:
  title: 08 - Menerapkan Azure Functions (5 mnt)
  module: 'Module 03: Describe core solutions and management tools'
ms.openlocfilehash: 419d49832a4059e447d2621fe4f209dc5ada2474
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907764"
---
# <a name="08---implement-azure-functions-5-min"></a>08 - Menerapkan Azure Functions (5 mnt)

Dalam panduan ini, kita akan membuat Aplikasi Fungsi untuk menampilkan pesan Hello ketika ada permintaan HTTP. 

# <a name="task-1-create-a-function-app"></a>Tugas 1: Membuat aplikasi Fungsi 

Dalam tugas ini, kita akan membuat aplikasi Fungsi.

1. Masuk ke [portal Microsoft Azure](https://portal.azure.com).

2. Di bilah **Search** di bagian atas portal, cari dan pilih **Function App**, lalu dari bilah **Function App**, klik **+ Add, + Create, + New**.

3. Pada tab **Basic** bilah **Function App**, tentukan pengaturan berikut (ganti **xxxx** dalam nama fungsi dengan huruf dan angka sehingga namanya unik secara global dan biarkan semua pengaturan lain dengan nilai default): 

    | Pengaturan | Nilai |
    | -- | --|
    | Langganan | **Biarkan default disediakan** |
    | Grup sumber daya | **Membuat grup sumber daya baru** |
    | Nama Aplikasi Fungsi | **function-xxxx** |
    | Terbitkan | **Kode** |
    | Tumpukan runtime | **.NET** |
    | Versi | **3.1** |
    | Wilayah | **AS Timur** |

    **Catatan** - Perlu diingat untuk mengubah **xxxx** sehingga menjadi **nama Aplikasi Fungsi** yang unik

4. Klik **Review + Create.** dan, setelah validasi berhasil, klik **Create** untuk mulai memprovisi dan menyebarkan Aplikasi Fungsi Azure yang baru.

5. Tunggu pemberitahuan bahwa sumber daya telah dibuat.

6. Saat penyebaran telah selesai, klik Go to resource dari bilah penyebaran. Atau, navigasi kembali ke bilah **Function App**, klik **Refresh** dan verifikasi bahwa aplikasi fungsi yang baru dibuat memiliki status **Running**. 

    ![Cuplikan layar halaman Aplikasi Fungsi dengan aplikasi Fungsi baru.](../images/0701.png)

# <a name="task-2-create-a-http-triggered-function-and-test"></a>Tugas 2: Membuat fungsi dan pengujian yang dipicu HTTP

Dalam tugas ini, kita akan menggunakan fungsi Webhook + API untuk menampilkan pesan saat ada permintaan HTTP. 

1. Pada bilah **Function App**, klik aplikasi fungsi yang baru dibuat. 

2. Di bilah aplikasi fungsi, di bagian **Functions**, klik **Functions**, lalu klik **+ Add, + Create, + New**.

    ![Cuplikan layar langkah memilih lingkungan pengembangan di azure functions untuk panel memulai dot net di dalam portal Microsoft Azure. Elemen tampilan untuk membuat fungsi dalam portal baru disorot. Elemen yang disorot adalah memperluas aplikasi fungsi, menambahkan fungsi baru, dalam portal, dan tombol continue.](../images/0702.png)

3. Jendela pop-up **Add function** akan muncul di sebelah kanan. Di bagian **Select a template**, klik **HTTP trigger**. Klik **Tambahkan** 

    ![Cuplikan layar langkah membuat fungsi di azure functions untuk panel memulai dot net di dalam portal Microsoft Azure. Kartu pemicu HTTP disoroti untuk mengilustrasikan elemen tampilan yang digunakan untuk menambahkan webhook baru ke fungsi Azure.](../images/0702a.png)

4. Pada bilah **HttpTrigger1**, di bagian **Developer**, klik **Code + Test**. 

5. Di bilah **Code + Test**, tinjau kode yang dibuat secara otomatis dan perhatikan bahwa kode tersebut dirancang untuk menjalankan permintaan HTTP dan informasi log. Selain itu, perhatikan fungsi menampilkan pesan Hello dengan sebuah nama. 

    ![Cuplikan layar kode fungsi. Pesan Hello disorot.](../images/0704.png)

6. Klik **Get function URL** dari bagian atas editor fungsi. 

7. Pastikan nilai dalam daftar menurun **Key** diatur ke **default** dan klik **Copy** untuk menyalin fungsi URL. 

    ![Cuplikan layar panel dapatkan URL fungsi di dalam editor fungsi di portal Microsoft Azure. Elemen tampilan tombol dapatkan URL fungsi, set kunci menurun, dan tombol copy URL disorot untuk menunjukkan cara mendapatkan dan menyalin URL fungsi dari editor fungsi.](../images/0705.png)

8. Buka tab browser baru dan tempel URL fungsi yang disalin ke bilah alamat browser web Anda. Ketika halaman diminta, fungsi akan berjalan. Perhatikan pesan yang dikembalikan yang menyatakan bahwa fungsi tersebut memerlukan nama di isi permintaan.

    ![Cuplikan layar pesan harap berikan nama.](../images/0706.png)

9. Tambahkan **&name=*yourname*** di akhir URL.

    **Catatan**: Misalnya, jika nama Anda Cindy, URL akhir akan terlihat seperti berikut: `https://azfuncxxx.azurewebsites.net/api/HttpTrigger1?code=X9xx9999xXXXXX9x9xxxXX==&name=cindy`

    ![Cuplikan layar URL fungsi yang disorot dan contoh nama pengguna yang ditambahkan di bilah alamat browser web. Pesan hello dan nama pengguna juga disorot untuk mengilustrasikan output dari fungsi di jendela browser utama.](../images/0707.png)

10. Saat Anda menekan enter, fungsi akan berjalan dan setiap permohonan akan dilacak. Untuk melihat jejak, kembali ke panel Portal **HttpTrigger1 \| Kode + Pengujian** dan klik **Pantau**. Anda dapat **mengonfigurasi** Application Insights dengan memilih stempel waktu dan mengeklik **Jalankan kueri di Application Insights**.

    ![Cuplikan layar log informasi jejak yang dihasilkan dari menjalankan fungsi di dalam editor fungsi di portal Microsoft Azure.](../images/0709.png) 

Selamat! Anda telah membuat Aplikasi Fungsi untuk menampilkan pesan Halo ketika ada permintaan HTTP.  

**Catatan**: Untuk menghindari biaya tambahan, Anda dapat memilih untuk menghapus grup sumber daya ini. Telusuri grup sumber daya, klik grup sumber daya, lalu klik **Delete resource group**. Verifikasi nama grup sumber daya, lalu klik **Delete**. Pantau **Notifications** untuk melihat bagaimana proses penghapusan.
