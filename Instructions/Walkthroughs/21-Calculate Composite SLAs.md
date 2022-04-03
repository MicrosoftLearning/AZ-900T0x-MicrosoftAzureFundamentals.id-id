---
wts:
  title: 21 - Menghitung SLA Komposit (5 mnt)
  module: 'Module 06: Describe Azure cost management and service level agreements'
ms.openlocfilehash: 1d27d18cd1a0b2ad6ab09c7fc65a51d5a8f13711
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 01/27/2022
ms.locfileid: "137907688"
---
# <a name="21---calculate-composite-slas-5-min"></a>21 - Menghitung SLA Komposit (5 mnt)

Dalam panduan ini, kita akan menentukan ketersediaan SLA layanan Azure dan kemudian menghitung ketersediaan yang diharapkan berdasarkan SLA komposit aplikasi.

Aplikasi contoh kita terdiri dari layanan Azure ini. Kita tidak akan membahas konfigurasi dan pertimbangan arsitektural secara mendalam, maksudnya di sini adalah untuk memberikan contoh tingkat tinggi.

+ **Layanan aplikasi**: Untuk membuat host aplikasi.
+ **Azure Active Directory B2C**: Untuk mengautentikasi login pengguna dan mengelola profil.
+ **Application Gateway**: Untuk mengelola akses aplikasi, dan penskalaan. 
+ **Azure SQL Database**: Untuk menyimpan data aplikasi. 

# <a name="task-1-determine-the-sla-uptime-percentage-values-for-our-application"></a>Tugas 1: Menentukan nilai persentase waktu aktif SLA untuk aplikasi kita

1. Di browser, buka halaman [Ringkasan SLA untuk layanan Azure](https://azure.microsoft.com/en-us/support/legal/sla/summary/).

2. Temukan nilai waktu aktif SLA **App Service**, **99.95%** . Klik **View full details**, dan lalu perluas **SLA details**. Perhatikan **Monthly uptime percentages** dan **Service Credits**.

3. Kembali ke halaman web SLA dan temukan layanan **Azure Active Directory B2C** dan tentukan nilai waktu aktif SLA, **99.9%** . 

4. Temukan nilai waktu aktif SLA **Application Gateway** , **99.95%** . 

5. Azure SQL database menggunakan tingkatan Premium tetapi tidak dikonfigurasi untuk Penyebaran Zona Redundan. Temukan nilai waktu aktif SLA **Azure SQL Database**, **99.99%** . 

    **Catatan**: Ada nilai waktu aktif yang berbeda untuk konfigurasi dan penyebaran Azure SQL Database yang berbeda. Anda harus memahami dengan jelas nilai waktu aktif yang diperlukan saat merencanakan dan menentukan biaya penerapan serta konfigurasi Anda. Perubahan kecil dalam waktu aktif dapat berdampak pada biaya layanan serta berpotensi meningkatkan kompleksitas konfigurasi. Beberapa layanan lain yang mungkin menarik di halaman ringkasan Azure SLA akan mencakup **Komputer Virtual**, **Akun Penyimpanan**, dan **Cosmos DB**.

# <a name="task-2-calculate-the-application-composite-sla-percentage-uptime"></a>Tugas 2: Hitung waktu aktif persentase SLA Komposit Aplikasi

1. Jika salah satu layanan yang terdiri dari aplikasi kita tidak tersedia, aplikasi kita tidak akan tersedia bagi pengguna untuk masuk dan digunakan. Dengan demikian total waktu aktif untuk aplikasi kita terdiri dari berikut ini:

    **Waktu aktif % App Service** X **Waktu aktif % Azure Active Directory B2C** X **waktu aktif % Azure Application Gateway** X **Waktu aktif % Azure SQL Database** = **Total % Waktu Aktif**

    yang dalam persentase adalah sebagai berikut:

    **99,95%** X **99,9%** X **99,95%** X **99,99%**  = **99,79%**

    Ini adalah ketersediaan yang diharapkan berbasis SLA dari aplikasi kita dengan layanan dan arsitektur saat ini.

Selamat! Anda telah menentukan waktu aktif berbasis SLA untuk setiap layanan dalam aplikasi sampel kita dan kemudian menghitung ketersediaan yang diharapkan berbasis SLA gabungan untuk aplikasi tersebut.
