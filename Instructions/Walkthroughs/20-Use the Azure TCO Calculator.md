---
wts:
  title: 20 - Menggunakan Kalkulator Azure TCO (10 mnt)
  module: 'Module 06: Describe Azure cost management and service level agreements'
ms.openlocfilehash: 8044b922cef99fae814fb6418a33ed7334eb506b
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908164"
---
# <a name="20---use-the-azure-tco-calculator-10-min"></a>20 - Menggunakan Kalkulator Azure TCO (10 mnt)


Dalam panduan ini, Anda akan menggunakan Kalkulator Total Biaya Kepemilikan (TCO) guna menghasilkan laporan perbandingan biaya untuk lingkungan lokal.

**Catatan**: Panduan ini memberikan contoh definisi infrastruktur lokal dan beban kerja untuk pusat data yang khas. Untuk membuat laporan Kalkulator TCO, gunakan definisi contoh atau berikan detail infrastruktur dan beban kerja lokal Anda *yang sebenarnya*.

# <a name="task-1-configure-the-tco-calculator"></a>Tugas 1: Mengonfigurasi kalkulator TCO

Dalam tugas ini, kita akan menambahkan informasi infrastruktur ke kalkulator. 

1. Di browser, buka halaman [Kalkulator Total Biaya Kepemilikan (TCO)](https://azure.microsoft.com/en-us/pricing/tco/calculator/).

2. Untuk menambahkan detail infrastruktur lokal Anda, klik **+ Add server workload** di panel **Define your workloads**.

    | Pengaturan | Nilai |
    | -- | -- |
    | Nama | **Server: VM Windows** |
    | Beban kerja | **Server Windows/Linux** |
    | Lingkungan | **Komputer Virtual** |
    | Sistem operasi | **Windows** |  
    | VM | **50** |
    | Virtualization | **Hyper-V** |
    | Inti | **8**|
    | RAM (GB) | **16** |
    | Dioptimalkan dengan | **CPU** |
    | Windows Server 2008/2008 R2 | **Nonaktif** |

3. Pilih **+ Add server workload** untuk membuat baris definisi beban kerja server yang baru. 

    | Pengaturan | Nilai |
    | -- | -- |
    | Nama | **Server: VM Linux** |
    | Beban kerja | **Server Windows/Linux** |
    | Lingkungan | **Komputer Virtual** |
    | Sistem operasi | **Linux** |  
    | VM | **50** |
    | Virtualization | **VMware** |
    | Inti | **8**|
    | RAM (GB) | **16** |
    | Dioptimalkan dengan | **CPU** |
    | Windows Server 2008/2008 R2 | **Nonaktif** |

4. Di panel **Storage**, klik **Add storage**.

    | Pengaturan | Nilai |
    | -- | -- |
    | Nama | **Penyimpanan Server** |
    | Jenis penyimpanan | **Disk/SAN Lokal** |
    | Jenis disk OS | **HDD** |
    | Kapasitas | **60 TB** |  
    | Cadangan | **120 TB** |
    | Arsip | **0 TB** |

5. Di panel **Networking**, tambahkan bandwidth. 

    | Pengaturan | Nilai |
    | -- | -- |
    | Bandwidth keluar | 15 TB|

6. Klik **Berikutnya**.

7. Jelajahi opsi dan buat penyesuaian yang Anda butuhkan. 

    | Pengaturan | Nilai |
    | -- | -- |
    | Mata uang | **Euro** |

8. Klik **Berikutnya**.

# <a name="task-2-review-the-results-and-save-a-copy"></a>Tugas 2: Meninjau hasil dan menyimpan salinannya

Dalam tugas ini, kita akan meninjau rekomendasi penghematan biaya dan mengunduh laporan. 

1. Meninjau rekomendasi dan visualisasi penghematan biaya Azure.

    | Pengaturan | Nilai |
    | -- | -- |
    | Jangka waktu| **3 tahun** |
    | Wilayah | **Eropa Utara** |

2. Untuk mengubah informasi yang Anda berikan, pergi ke bagian bawah halaman, dan klik **Back**. 

3. Untuk menyimpan atau mencetak salinan PDF laporan, klik **Download**.

    ![Cuplikan layar dari panel laporan kalkulator tco di Azure. Kolom masukan yang disorot dan diisi menunjukkan cara mengatur jangka waktu kalkulator tco menjadi tiga tahun dan kawasan ke eropa utara. Grafik memperlihatkan biaya infrastruktur lokal dan beban kerja yang disesuaikan dengan pengurangan biaya penggunaan Azure.](../images/2001.png)

Selamat! Anda telah menggunakan Kalkulator TCO guna membuat laporan perbandingan biaya untuk lingkungan lokal.
