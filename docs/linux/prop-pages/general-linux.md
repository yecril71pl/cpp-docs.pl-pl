---
title: "Ogólne właściwości (projekt C++ Linux) | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 9/26/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
author: mikeblome
ms.author: mblome
manager: ghogen
f1_keywords:
- VC.Project.VCConfiguration.OutputDirectory
- VC.Project.VCConfiguration.IntermediateDirectory
- VC.Project.VCConfiguration.TargetName
- VC.Project.VCConfiguration.TargetExt
- VC.Project.VCConfiguration.DeleteExtensionsOnClean
- VC.Project.VCConfiguration.PlatformToolset
- VC.Project.VCConfiguration.BuildLogFile
- VC.Project.VCConfiguration.ConfigurationType
- VC.Project.VCConfiguration.UseOfSTL
ms.openlocfilehash: 4de08a00ddedf1eec97d1872646a986e09c22547
ms.sourcegitcommit: ca2f94dfd015e0098a6eaf5c793ec532f1c97de1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2017
---
# <a name="general-properties-linux-c"></a>Właściwości ogólne (Linux C++)

Właściwość | Opis | Opcje
--- | ---| ---
Katalog wyjściowy | Określa ścieżkę względną do katalogu pliku wyjściowego; może zawierać zmienne środowiskowe.
Katalog pośredni | Określa ścieżkę względną do pośredniego katalogu plików; może zawierać zmienne środowiskowe.
Nazwa obiektu docelowego | Określa nazwę pliku, który zostanie wygenerowany przez projekt.
Rozszerzenie docelowego | Określa rozszerzenie pliku, który zostanie wygenerowany przez projekt. (Przykład: .a)
Rozszerzenia do usunięcia podczas oczyszczania | Rozdzielana średnikami Specyfikacja symboli wieloznacznych określająca jakie pliki w katalogu pośrednim mają zostać usunięte podczas oczyszczania lub Odbuduj.
Tworzenie pliku dziennika | Określa plik dziennika kompilacji do zapisu, gdy rejestrowanie kompilacji jest włączona.
Zestaw narzędzi platformy | Określa zestaw narzędzi używanych do kompilowania bieżącej konfiguracji. Jeśli nie jest używany zestaw, do domyślnego zestawu narzędzi
Maszyny zdalnej kompilacji | Maszyna docelowa lub urządzenie na potrzeby kompilacji zdalnej, wdrażanie i debugowanie.
Katalog główny kompilacji zdalnej | Określa ścieżkę do katalogu na urządzeniu lub komputerze zdalnym.
Katalog projektu kompilacji zdalnej | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu dla projektu.
Typ konfiguracji | Określa typ danych wyjściowych generowanych przez tę konfigurację. | **Dynamicznymi (.so)** -dynamicznymi (.so)<br>**Biblioteka statyczna (.a)** — biblioteka statyczna (tj.)<br>**Aplikacji (.out)** -aplikacji (.out)<br>**Pliku reguł programu make** -pliku reguł programu make<br>
Użyj STL | Określa, która standardowa biblioteka C++ do użycia dla tej konfiguracji. | **Standardowa biblioteka C++ udostępnionego GNU**<br>**Standardowa biblioteka C++ GNU statyczne (— statyczne)**<br>
