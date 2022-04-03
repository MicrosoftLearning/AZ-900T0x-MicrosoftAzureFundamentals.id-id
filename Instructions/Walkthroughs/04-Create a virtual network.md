---
wts:
  title: 04 - Membuat jaringan virtual (20 mnt)
  module: Module 02 - Core Azure Services (Workloads)
ms.openlocfilehash: 08aafa461c0facc43e735bd81ba97aa9650952fa
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907796"
---
# <a name="04---create-a-virtual-network-20-min"></a>04 - Membuat jaringan virtual (20 mnt)

Dalam panduan ini, kita akan membuat jaringan virtual, menyebarkan dua komputer virtual ke jaringan virtual tersebut, kemudian mengonfirgurasinya untuk mengizinkan satu komputer virtual melakukan ping ke yang lain di dalam jaringan virtual.

# <a name="task-1-create-a-virtual-network"></a>Tugas 1: Membuat jaringan virtual 

Dalam tugas ini, kita akan membuat jaringan virtual. 

Catatan: Sebelum memulai lab, nonaktifkan firewall publik dan privat di mesin virtual Anda dengan membuka menu Start > Pengaturan > Jaringan dan Internet > Temukan Windows Firewall

1. Masuk ke portal Microsoft Azure di <a href="https://portal.azure.com" target="_blank"><span style="color: #0066cc;" color="#0066cc">https://portal.azure.com</span></a>

2. Dari bilah **All services**, cari dan pilih **Virtual networks**, lalu klik **+ Add, + Create, + New**. 

3. Pada tab **Basics**, isi informasi berikut (biarkan default untuk yang lainnya):

    | Pengaturan | Nilai | 
    | --- | --- |
    | Langganan | **Biarkan default disediakan** |
    | Grup Sumber Daya | **Membuat grup sumber daya baru** |
    | Nama | **vnet1** |
    | Wilayah | **(AS) AS Timur** |
    
   
4. Klik tombol **Tinjau + buat**. Pastikan validasi lolos. Lalu tekan buat untuk menyebarkan sumber daya.


# <a name="task-2-create-two-virtual-machines"></a>Tugas 2: Buat dua komputer virtual

Dalam tugas ini, kita akan membuat dua komputer virtual di jaringan virtual. 

1. Dari bilah **All services**, cari **Virtual machines**, lalu klik **+ Add, + Create, + New**, dari menu tarik-turun, pilih **Virtual Machine**. 

2. Pada tab **Basics**, isi informasi berikut (biarkan default untuk yang lainnya):

   | Pengaturan | Nilai | 
   | --- | --- |
   | Langganan | **Menggunakan default yang disediakan** |
   | Grup sumber daya |  **Memilih default di tarik-turun** |
   | Nama komputer virtual | **vm1**|
   | Wilayah | **(AS) AS Timur** |
   | Gambar | **Pusat Data Windows Server 2019 - Gen2** |
   | Nama Pengguna| **azureuser** |
   | Kata sandi| **Pa$$w 0rd1234** |
   | Port inbound publik| Pilih **Izinkan port yang dipilih**  |
   | Selected inbound ports| **RDP (3389)** |
   

3. Pilih tab **Networking**. Pastikan komputer virtual ditempatkan di jaringan virtual **vnet1**. Tinjau pengaturan default, tetapi jangan lakukan perubahan apa pun. 

4. Klik **Ulas + buat**. Setelah Validasi lolos, klik **Create**. Waktu penyebaran dapat berbeda-beda, tetapi biasanya perlu waktu antara tiga hingga enam menit untuk disebarkan.

5. Pantau penyebaran Anda, tetapi lanjutkan ke langkah berikutnya. 

6. Buat komputer virtual kedua dengan mengulangi langkah **2 hingga 4** di atas. Pastikan Anda menggunakan nama komputer virtual yang berbeda, komputer virtual tersebut berada dalam jaringan virtual yang sama, dan menggunakan alamat IP publik yang baru:

    | Pengaturan | Nilai |
    | --- | --- |
    | Grup sumber daya | **pilih default di tarik-turun (sama seperti Task1-3 & Task2-2)** |
    | Nama komputer virtual |  **vm2** |
    | Jaringan virtual | **vnet1** |
    | IP Publik | **vm2-ip** |

7. Tunggu hingga kedua komputer virtual disebarkan dan statusnya menjadi *berjalan*.

# <a name="task-3-test-the-connection"></a>Tugas 3: Menguji koneksi 

Pada tugas ini, kita akan coba menguji apakah komputer virtual dapat berkomunikasi (ping) satu sama lain. Jika tidak, kita akan menginstal aturan yang mengizinkan koneksi ICMP. Biasanya koneksi ICMP diblokir secara otomatis.

1. Dari bilah **All resource**, cari **vm1**, buka bilah **Overview**, dan pastikan **Status** adalah **Running**. Anda mungkin perlu melakukan **Refresh** halamannya.

2. Di bilah **Overview**, pilih **Connect**, lalu pilih **RDP** dari menu tarik-turun.

    **Catatan**: Petunjuk berikut memberi tahu Anda cara menyambungkan ke komputer virtual dari komputer Windows. 

3. Di bilah **Connect RDP**, biarkan opsi default untuk tersambung dengan alamat IP melalui port 3389, dan klik **Download RDP File**.

4. Buka file RDP yang diunduh (terletak di sebelah kiri bawah VM) dan klik **Connect** bila diminta. 

5. Di jendela **Windows Security**, ketik nama pengguna **azureuser** dan kata sandi **Pa$$w0rd1234**, lalu klik **OK**.

6. Anda mungkin menerima peringatan sertifikat selama proses masuk. Klik **Yes** untuk membuat koneksi dan menyambungkan ke VM yang Anda sebarkan. Anda akan berhasil tersambung. Tutup Windows Server dan jendela Dasbor yang muncul. Anda akan melihat latar belakang Windows Biru. Kini, Anda berada di komputer virtual.

7. Di **kedua** mesin virtual yang baru dibuat, hubungkan melalui RDP dan nonaktifkan firewall publik dan privat dengan membuka menu Start > Pengaturan > Jaringan dan Internet > Temukan Windows Firewall.

8. Buka PowerShell di komputer virtual dengan mengklik tombol **Start**, dan di Pencarian, ketikkan **PowerShell**, klik kanan **Windows PowerShell**, lalu **Run as administrator**

9. Di Powershell, coba lakukan ping ke vm2 dengan mengetikkan:

   ```PowerShell
   ping vm2
   ```

 10. Anda akan berhasil. Anda telah melakukan ping ke VM2 dari VM1.


**Selamat!** Anda telah mengonfigurasi dan menyebarkan dua komputer virtual di jaringan virtual, lalu Anda juga telah dapat menghubungkan keduanya.

**Catatan**: Untuk menghindari biaya tambahan, Anda dapat memilih untuk menghapus grup sumber daya ini. Telusuri grup sumber daya, klik grup sumber daya, lalu klik **Delete resource group**. Verifikasi nama grup sumber daya, lalu klik **Delete**. Pantau **Notifications** untuk melihat bagaimana proses penghapusan.
