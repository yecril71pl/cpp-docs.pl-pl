---
title: Ogólne właściwości (projekt C++ Linux) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 82dbdb4b2978860faba4e31c756ab0b69928e080
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
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
