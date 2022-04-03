---
title: Petunjuk Host Online
permalink: index.html
layout: home
ms.openlocfilehash: c8816b7d9de9c19fbd4c6b3f373d6e4336c6ca5a
ms.sourcegitcommit: 26c283fffdd08057fdce65fa29de218fff21c7d0
ms.translationtype: HT
ms.contentlocale: id-ID
ms.lasthandoff: 01/27/2022
ms.locfileid: "137908177"
---
# <a name="content-directory"></a>Direktori Konten

Hyperlink untuk setiap penelusuran. Instruktur dapat memilih untuk menggunakan penelusuran sebagai demonstrasi atau lab siswa. 

## <a name="walkthroughs"></a>Panduan

{% assign wts = site.pages | where_exp:"page", "page.url berisi '/Instructions/Walkthroughs'" %}
| Modul | Walkthrough |
| --- | --- | 
{% for activity in wts %}| {{ activity.wts.module }} | [{{ activity.wts.title }}{% if activity.wts.type %} - {{ activity.wts.type }}{% endif %}]({{ site.github.url }}{{ activity.url }}) |
{% endfor %}

