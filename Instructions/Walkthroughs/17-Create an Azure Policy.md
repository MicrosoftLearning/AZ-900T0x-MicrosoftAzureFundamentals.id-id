---
wts:
  title: 17 - Membuat Azure Policy (10 mnt)
  module: 'Module 05: Describe identity, governance, privacy, and compliance features'
ms.openlocfilehash: 2811044ec560b0ac42f49a578666ed1694feb32a
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907932"
---
# <a name="17---create-an-azure-policy-10-min"></a>17 - Membuat Azure Policy (10 mnt)

Dalam panduan ini, kita akan membuat Azure Policy untuk membatasi penyebaran sumber daya Azure ke lokasi tertentu.

# <a name="task-1-create-a-policy-assignment"></a>Tugas 1: Membuat penetapan Kebijakan 

Dalam tugas ini, kita akan mengonfigurasi kebijakan lokasi yang diizinkan dan menetapkannya ke langganan kita. 

1. Masuk ke [portal Microsoft Azure](https://portal.azure.com).

2. Dari bilah **All services**, cari dan pilih **Policy**, di bagian **Authoring**, klik **Definitions**.  Luangkan waktu sejenak untuk meninjau daftar definisi kebijakan bawaan. Misalnya, di menu menurun **Category**, hanya pilih **Compute**. Lihat definisi **Allowed virtual machine Size SKUs** memungkinkan Anda menentukan sekumpulan SKU komputer virtual yang dapat disebarkan organisasi Anda.

3. Kembali ke halaman **Policy**, pada bagian **Authoring**, klik **Assignments**. Tugas adalah kebijakan yang telah ditetapkan untuk berlangsung dalam lingkup tertentu. Misalnya, definisi dapat ditetapkan ke lingkup langganan. 

4. Klik **Assign Policy** di bagian atas halaman **Policy - Assignments**.

5. Di halaman **Assign Policy**, biarkan Cakupan default.

      | Pengaturan | Nilai | 
    | --- | --- |
    | Lingkup| **Menggunakan default yang dipilih**|
    | Definisi kebijakan | Klik elipsis, lalu cari **Allowed Locations**, kemudian **Select** |
    | Assignment Name | **Lokasi yang Diizinkan** |
    
    ![Cuplikan layar dari panel Cakupan dengan nilai bidang yang diisi dan tombol Pilih yang disoroti. ](../images/1402.png)
6. Di tab **Parameters**, pilih **Japan West**. Klik **Review + create.** , lalu klk **Create**.

    **Catatan**: Cakupan menentukan sumber daya atau pengelompokan sumber daya tempat penetapan kebijakan diterapkan. Dalam kasus ini, kita dapat menetapkan kebijakan ini ke grup sumber daya tertentu, tetapi kita memilih untuk menetapkan kebijakan di tingkat langganan. Perlu diketahui bahwa sumber daya dapat dikecualikan berdasarkan konfigurasi cakupan. Pengecualian bersifat opsional.

    **Catatan**: Definisi kebijakan **Allowed Locations** ini akan menentukan lokasi tempat semua sumber daya harus disebarkan. Jika lokasi yang berbeda dipilih, penyebaran tidak akan diizinkan. Untuk mengetahui informasi selengkapnya, lihat halaman [Sampel Azure Policy](https://docs.microsoft.com/en-us/azure/governance/policy/samples/index).

   ![Cuplikan layar dari panel Definisi yang Tersedia dengan berbagai bidang yang disoroti dan komputer virtual Audit yang tidak menggunakan opsi disk terkelola dipilih.](../images/1403.png)

9. Penetapan kebijakan **Allowed locations** kini tercantum di panel **Policy - Assignments** dan sekarang diterapkan, sehingga memberlakukan kebijakan di tingkat cakupan yang telah kita tentukan (tingkat langganan).

# <a name="task-2-test-allowed-location-policy"></a>Tugas 2: Menguji Kebijakan lokasi yang diizinkan

Dalam tugas ini, kita akan menguji kebijakan Lokasi yang diizinkan. 

1. Di Portal Microsoft Azure, dari bilah **All services**, cari dan pilih **Storage accounts**, lalu klik **+ Create**.

2. Konfigurasikan akun penyimpanan (ganti **xxxx** atas nama akun penyimpanan dengan huruf dan angka sehingga namanya unik secara global). Gunakan pengaturan default untuk yang lainnya. 

    | Pengaturan | Nilai | 
    | --- | --- |
    | Langganan | **Menggunakan default yang disediakan** |
    | Grup sumber daya | **myRGPolicy** (buat baru) |
    | Nama akun penyimpanan | **storageaccountxxxx** |
    | Lokasi | **(AS) AS Timur** |

3. Klik **Review + create**, lalu klik **Create**. 

4. Anda akan menerima kesalahan **penyebaran gagal** yang menyatakan bahwa sumber daya dilarang oleh kebijakan, termasuk nama kebijakan **Allowed locations**.

# <a name="task-3-delete-the-policy-assignment"></a>Tugas 3: Hapus penetapan kebijakan

Dalam tugas ini, kita akan menghapus penetapan dan pengujian kebijakan lokasi yang diizinkan. 

Kita akan menghapus penetapan kebijakan untuk memastikan kita tidak diblokir pada pekerjaan apa pun di masa mendatang yang ingin dilakukan.

1. Dari bilah **All services**, cari dan pilih **Policy**, lalu klik kebijakan **Allowed locations**.

    **Catatan**: Di bilah **Policy**, Anda dapat melihat status kepatuhan dari berbagai kebijakan yang telah ditetapkan.

    **Catatan**: Kebijakan lokasi yang diizinkan mungkin menunjukkan sumber daya yang tidak sesuai. Jika demikian, ini adalah sumber daya yang dibuat sebelum penugasan kebijakan.
 
2. Klik **Allowed Locations**, ini akan membuka jendela Kepatuhan Kebijakan Lokasi yang diizinkan.

3. Klik **Delete Assignment** di menu bagian atas. Konfirmasikan bahwa Anda ingin menghapus penetapan kebijakan dengan mengklik **Yes**

   ![Cuplikan layar dari item menu Hapus Penugasan.](../images/1407.png)

4. Coba buat akun penyimpanan lain untuk memastikan bahwa kebijakan tidak berlaku lagi.

    **Catatan**: Skenario umum di mana kebijakan **Lokasi yang diizinkan** dapat berguna meliputi: 
    - *Pelacakan Harga*: Anda dapat memiliki langganan yang berbeda untuk lokasi regional yang berbeda. Kebijakan tersebut akan memastikan bahwa semua sumber daya disebarkan di wilayah yang dituju untuk membantu pelacakan biaya. 
    - *Kepatuhan Residensi Data dan Keamanan*: Anda juga dapat memiliki persyaratan residensi data, dan membuat langganan per pelanggan atau beban kerja tertentu, serta menentukan bahwa semua sumber daya harus digunakan di pusat data tertentu guna memastikan data dan persyaratan kepatuhan keamanan.

Selamat! Anda telah membuat Azure Policy untuk membatasi penyebaran sumber daya Azure ke pusat data tertentu.

**Catatan**: Untuk menghindari biaya tambahan, Anda dapat memilih untuk menghapus grup sumber daya ini. Telusuri grup sumber daya, klik grup sumber daya, lalu klik **Delete resource group**. Verifikasi nama grup sumber daya, lalu klik **Delete**. Pantau **Notifications** untuk melihat bagaimana proses penghapusan.
