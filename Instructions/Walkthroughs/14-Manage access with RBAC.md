---
wts:
  title: 14 - Mengelola akses dengan RBAC (5 mnt)
  module: 'Module 05: Describe identity, governance, privacy, and compliance features'
ms.openlocfilehash: 4d1369307dc306a367a8a4cc532774c08c513e85
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907738"
---
# <a name="14---manage-access-with-rbac-5-min"></a>14 - Mengelola akses dengan RBAC (5 mnt)

Dalam panduan ini, kita akan menetapkan izin peran ke sumber daya dan menampilkan log.

# <a name="task-1-view-and-assign-roles"></a>Tugas 1: Menampilkan dan menetapkan peran

Dalam tugas ini, kita akan menetapkan peran Kontributor komputer virtual. 

1. Masuk ke [portal Microsoft Azure](https://portal.azure.com).

2. Dari bilah **All services**, cari dan pilih **Resource groups**, lalu klik **+Add +New +Create**.

3. Buat grup sumber daya baru. Klik **Create** setelah Anda selesai. 

    | Pengaturan | Nilai |
    | -- | -- |
    | Langganan | **Menggunakan default yang disediakan** |
    | Grup sumber daya | **myRGRBAC** |
    | Wilayah | **(AS) AS Timur** |
   

4. Buat **Review + create**, lalu klk **Create**.

5. **Refresh** halaman grup sumber daya dan klik entri yang mewakili grup sumber daya yang baru dibuat.

6. Klik bilah **Access control (IAM)** , lalu alihkan ke tab **Roles**. Gulir melalui sejumlah besar definisi peran yang tersedia. Gunakan ikon Informasi untuk mendapatkan ide tentang izin setiap peran. Perhatikan juga informasi tentang jumlah pengguna dan grup yang ditetapkan ke setiap peran.
7. 
![gambar](https://user-images.githubusercontent.com/89808319/144266949-f19d91ab-31d6-4c8b-af36-c00035925cf0.png)

7. Beralih ke tab **Role assignments** pada bilah **myRGRBAC - Access control (IAM)** , klik **+ Add**, lalu klik **Add role assignment**. Cari peran Kontributor Mesin Virtual dan pilih. Beralih ke tab "Anggota" dan Tetapkan akses ke: Pengguna, grup, atau perwakilan layanan. Kemudian klik + Pilih anggota dan ketik nama Anda ke fungsi pencarian popup dan tekan 'pilih'. Kemudian tekan 'Tinjau dan Tetapkan'

    
    ![gambar](https://user-images.githubusercontent.com/89808319/144266255-3a0f8574-9358-4c21-8f95-3503747e77c8.png)

 

    **Catatan:** Peran Kontributor komputer virtual memungkinkan Anda mengelola komputer virtual, tetapi tidak mengakses sistem operasinya atau mengelola jaringan virtual dan akun penyimpanan tempat itu tersambung.

  

8. **Refresh** halaman Penetapan peran dan pastikan Anda sekarang terdaftar sebagai Kontributor komputer virtual. 

    **Catatan**: Penugasan ini ini sebenarnya tidak memberikan hak istimewa tambahan apa pun, karena akun Anda sudah memiliki peran Pemilik, yang mencakup semua hak istimewa yang terkait dengan peran Kontributor.

# <a name="task-2-monitor-role-assignments-and-remove-a-role"></a>Tugas 2: Memantau penetapan peran dan menghapus peran

Dalam tugas ini, kita akan menampilkan log aktivitas untuk memverifikasi penetapan peran, lalu menghapus peran tersebut. 

1. Pada bilah grup sumber daya myRGRBAC, klik **Activity log**.

2. Klik **Add filter**, pilih **Operation**, lalu **Create role assignment**.

    ![Cuplikan layar halaman Log aktivitas dengan filter yang dikonfigurasi.](../images/1503.png)

3. Periksa bahwa Log aktivitas menunjukkan penetapan peran Anda. 

    **Catatan**: Dapatkah Anda mengetahui cara menghapus penetapan peran Anda?

Selamat! Anda telah membuat grup sumber daya, menetapkan peran akses, dan menampilkan log aktivitas. 

**Catatan**: Untuk menghindari biaya tambahan, Anda dapat memilih untuk menghapus grup sumber daya ini. Telusuri grup sumber daya, klik grup sumber daya, lalu klik **Delete resource group**. Verifikasi nama grup sumber daya, lalu klik **Delete**. Pantau **Notifications** untuk melihat bagaimana proses penghapusan.

