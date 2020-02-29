---
title: Ogólne właściwości projektu (Android C++ Makefile)
ms.date: 10/23/2017
ms.assetid: f76d717c-56ed-4373-8cf9-9bd1a053a4cd
f1_keywords:
- VC.Project.VCConfiguration.Android.Makefile.OutputDirectory
- VC.Project.VCConfiguration.Android.Makefile.IntermediateDirectory
- VC.Project.VCConfiguration.Android.Makefile.BuildLogFile
- VC.Project.VCConfiguration.Android.Makefile.ConfigurationType
ms.openlocfilehash: a52cedb1f7f7af1d4a0ff8e1a0d766d6e769e2fa
ms.sourcegitcommit: a673f6a54cc97e3d4cd032b10aa8dce7f0539d39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78177418"
---
# <a name="general-project-properties-android-c-makefile"></a>Ogólne właściwości projektu (plik C++ reguł programu make systemu Android)

Właściwość | Opis | Decyzji
--- | ---| ---
Katalog wyjściowy | Określa ścieżkę względną do katalogu pliku wyjściowego; może zawierać zmienne środowiskowe.
Katalog pośredni | Określa ścieżkę względną do pośredniego katalogu plików; może zawierać zmienne środowiskowe.
Plik dziennika kompilacji | Określa plik dziennika kompilacji, w którym ma zostać zapisany wpis, gdy rejestrowanie kompilacji jest włączone.
Typ konfiguracji | Określa typ danych wyjściowych generowanych przez tę konfigurację. | **Biblioteka dynamiczna (. so)** — Biblioteka dynamiczna ( *. tak*)<br>**Biblioteka statyczna (. a)** — Biblioteka statyczna ( *. a*)<br>**Narzędzia — narzędzie**<br>**Reguł programu make** — plik reguł programu make<br>
