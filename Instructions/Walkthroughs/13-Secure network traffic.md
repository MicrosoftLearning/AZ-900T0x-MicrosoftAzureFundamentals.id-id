---
wts:
  title: 13 - Mengamankan lalu lintas jaringan (10 mnt)
  module: 'Module 04: Describe general security and network security features'
ms.openlocfilehash: 27216b913111de76e00546319b56f69034819918
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907977"
---
# <a name="13---secure-network-traffic-10-min"></a>13 - Mengamankan lalu lintas jaringan (10 mnt)

Dalam panduan ini, kita akan mengonfigurasi kelompok keamanan jaringan.

# <a name="task-1-create-a-virtual-machine"></a>Tugas 1: Membuat komputer virtual

Dalam tugas ini, kita akan membuat komputer virtual Windows Server 2019 Datacenter. 

1. Masuk ke [portal Microsoft Azure](https://portal.azure.com).

2. Dari bilah **All services**, cari dan pilih **Virtual machines**, lalu klik **+ Add, + Create, + New** Komputer Virtual.

3. Pada tab **Basics**, isi informasi berikut (biarkan default untuk yang lainnya):

    | Pengaturan | Nilai |
    |  -- | -- |
    | Langganan | **Menggunakan default yang disediakan** |
    | Grup sumber daya | **Membuat grup sumber daya baru** |
    | Nama komputer virtual | **SimpleWinVM** |
    | Wilayah | **(AS) AS Timur**|
    | Gambar | **Pusat Data Windows Server 2019 Gen 2**|
    | Ukuran | **Standar D2s v3**|
    | Administrator account username | **azureuser** |
    | Administrator account password | **Pa$$w 0rd1234**|
    | Aturan port masuk | **Tidak ada**|

4. Beralih ke tab **Networking**, dan konfigurasikan pengaturan berikut:

    | Pengaturan | Nilai |
    | -- | -- |
    | Grup keamanan jaringan NIC | **Tidak ada**|

5. Beralih ke tab **Management**, dan di bagian **Monitoring**, pilih pengaturan berikut:

    | Pengaturan | Nilai |
    | -- | -- |
    | Diagnostik boot | **Nonaktifkan**|

6. Biarkan default yang tersisa lalu klik tombol **Review + create** di bagian bawah halaman.

7. Setelah melewati proses Validasi, klik tombol **Create**. Diperlukan waktu sekitar lima menit untuk menyebarkan komputer virtual.

8. Pantau penyebarannya. Mungkin perlu beberapa menit untuk membuat grup sumber daya dan komputer virtual. 

9. Dari bilah deployment atau dari area Notification, klik **Go to resource**. 

10. Pada bilah komputer virtual **SimpleWinVM**, klik **Networking**, tinjau tab **Inbound port rules**, dan perhatikan bahwa tidak ada kelompok keamanan jaringan yang terkait dengan antarmuka jaringan dari komputer virtual atau subnet tempat antarmuka jaringan dikaitkan.

    **Catatan**: Identifikasi nama antarmuka jaringan. Anda akan membutuhkannya di tugas berikutnya.

# <a name="task-2-create-a-network-security-group"></a>Tugas 2: Membuat kelompok keamanan jaringan

Dalam tugas ini, kita akan membuat kelompok keamanan jaringan dan mengaitkannya dengan antarmuka jaringan. 

1. Dari bilah **All services**, cari dan pilih **Network security groups**, lalu klik **+ Add, + Create, + New**

2. Pada tab **Basics** dari bilah **Create network security groups** tentukan pengaturan berikut.

    | Pengaturan | Nilai |
    | -- | -- |
    | Langganan | **Menggunakan langganan bawaan** |
    | Grup sumber daya | **Memilih default dari tarik-turun** |
    | Nama | **myNSGSecure** |
    | Wilayah | **(AS) AS Timur**  |

3. Klik **Review + create** lalu setelah validasi, klik **Create**.

4. Setelah NSG dibuat, klik **Go to resource**.

5. Di bawah **Pengaturan** klik **Antarmuka jaringan** lalu ** Kaitkan**.

6. Pilih antarmuka jaringan yang telah Anda identifikasi di tugas sebelumnya. 

# <a name="task-3-configure-an-inbound-security-port-rule-to-allow-rdp"></a>Tugas 3: Mengonfigurasi aturan port keamanan masuk untuk mengizinkan RDP

Dalam tugas ini, kita akan mengizinkan lalu lintas RDP ke komputer virtual dengan mengonfigurasi aturan port keamanan masuk. 

1. Di portal Microsoft Azure, navigasikan ke bilah komputer virtual **SimpleWinVM**. 

2. Di panel **Overview**, klik **Connect**.

3. Coba menyambungkan ke komputer virtual dengan memilih RDP dan mengunduh file RDP yang dijalankan. Secara default, kelompok keamanan jaringan tidak mengizinkan RDP. Tutup jendela kesalahan. 


    ![Cuplikan layar dari pesan kesalahan bahwa koneksi komputer virtual telah gagal.](../images/1201.png)

4. Pada bilah komputer virtual, gulir turun ke bagian **Settings**, klik **Networking**, dan perhatikan aturan masuk untuk kelompok keamanan jaringan **myNSGSecure (attached to network interface: myVMNic)** menolak semua lalu lintas masuk kecuali lalu lintas dalam jaringan virtual dan probe penyeimbang beban.

5. Di tab **Inbound port rules**, klik **Add inbound port rules**. Klik **Add** setelah Anda selesai. 

    | Pengaturan | Nilai |
    | -- | -- |
    | Sumber | **Mana pun**|
    | Rentang port sumber | **\*** |
    | Tujuan | **Mana pun** |
    | Rentang port tujuan | **3389** |
    | Protokol | **TCP** |
    | Tindakan | **Izinkan** |
    | Prioritas | **300** |
    | Nama | **AllowRDP** |

6. Pilih **Add** dan tunggu hingga aturan telah diterapkan, lalu coba kembali pada RDP ke komputer virtual dengan kembali ke **Connect**. Kali ini, Anda akan berhasil. Ingat bahwa pengguna adalah **azureuser** dan kata sandinya adalah **Pa$$w0rd1234**.

# <a name="task-4-configure-an-outbound-security-port-rule-to-deny-internet-access"></a>Tugas 4: Mengonfigurasi aturan port keamanan keluar untuk menolak akses Internet.

Dalam tugas ini, kita akan membuat aturan port keluar NSG yang akan menolak akses Internet, lalu mengujinya untuk memastikan aturan tersebut berfungsi.

1. Lanjutkan di sesi RDP komputer virtual Anda. 

2. Setelah komputer menyala, buka browser **Internet Explorer**. 

3. Pastikan bahwa Anda dapat mengakses **https://www.bing.com** lalu menutup Internet Explorer. Anda perlu bekerja melalui pop-up keamanan yang ditingkatkan IE. 

    **Catatan**: Sekarang kita akan mengonfigurasi aturan untuk menolak akses internet keluar. 

4. Kembali di portal Microsoft Azure, navigasikan kembali ke bilah komputer virtual **SimpleWinVM**. 

5. Di bawah **Settings**, klik **Networking**, lalu **Outbond port rules**.

6. Perhatikan ada aturan, **AllowInternetOutbound**. Ini adalah aturan default dan tidak dapat dihapus. 

7. Klik **Add outbond port rules** di sebelah kanan kelompok keamanan jaringan **myNSGSecure (attached to network interface: myVMNic)** dan konfigurasikan aturan keamanan keluar baru dengan prioritas lebih tinggi yang akan menolak lalu lintas internet. Klik **Add** setelah Anda selesai. 

    | Pengaturan | Nilai |
    | -- | -- |
    | Sumber | **Mana pun**|
    | Rentang port sumber | **\*** |
    | Tujuan | **Tag Layanan** |
    | Tag layanan tujuan | **Internet** |
    | Rentang port tujuan | **\*** |
    | Protokol | **TCP** |
    | Tindakan | **Tolak** |
    | Prioritas | **4000** |
    | Nama | **DenyInternet** |

8. Klik **Add** Kembali ke VM RDP Anda. 

9. Telusuri **https://www.microsoft.com**. Halaman semestinya tidak ditampilkan. Anda mungkin perlu bekerja melalui pop-up keamanan tambahan yang ditingkatkan IE.  

**Catatan**: Untuk menghindari biaya tambahan, Anda dapat memilih untuk menghapus grup sumber daya ini. Telusuri grup sumber daya, klik grup sumber daya, lalu klik **Delete resource group**. Verifikasi nama grup sumber daya, lalu klik **Delete**. Pantau **Notifications** untuk melihat bagaimana proses penghapusan.
