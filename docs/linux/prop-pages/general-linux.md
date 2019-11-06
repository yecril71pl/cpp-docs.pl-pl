---
title: Właściwości ogólne (projekt C++ systemu Linux) | Microsoft Docs
ms.date: 06/07/2019
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: c17a5e0214e6365d604a80bd4b3891858f0f9186
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626813"
---
# <a name="general-properties-linux-c"></a>Właściwości ogólne (Linux C++)

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

Właściwość | Opis | Decyzji
--- | ---| ---
Katalog wyjściowy | Określa ścieżkę względną do katalogu pliku wyjściowego; może zawierać zmienne środowiskowe.
Katalog pośredni | Określa ścieżkę względną do pośredniego katalogu plików; może zawierać zmienne środowiskowe.
Nazwa obiektu docelowego | Określa nazwę pliku, który zostanie wygenerowany przez ten projekt.
Rozszerzenie docelowe | Określa rozszerzenie pliku, który zostanie wygenerowany przez ten projekt. (Przykład:. a)
Rozszerzenia do usunięcia podczas czyszczenia | Rozdzielana średnikami Specyfikacja symboli wieloznacznych, dla których pliki w katalogu pośrednim mają zostać usunięte podczas czyszczenia lub odbudowy.
Plik dziennika kompilacji | Określa plik dziennika kompilacji, w którym ma zostać zapisany wpis, gdy rejestrowanie kompilacji jest włączone.
Zestaw narzędzi platformy | Określa zestaw narzędzi używany do tworzenia bieżącej konfiguracji; Jeśli nie zostanie ustawiona, używany jest domyślny zestaw narzędzi
Zdalna maszyna kompilacji | Maszyna docelowa lub urządzenie, które ma być używane do zdalnego kompilowania, wdrażania i debugowania. **Visual Studio 2019 w wersji 16,1** Na stronie [debugowanie](debugging-linux.md) można określić inny komputer na potrzeby debugowania.
Zdalny katalog główny kompilacji | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu.
Katalog projektu kompilacji zdalnej | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu dla projektu.
Typ konfiguracji | Określa typ danych wyjściowych generowanych przez tę konfigurację. | **Biblioteka dynamiczna (. so)** — Biblioteka dynamiczna (. tak)<br>**Biblioteka statyczna (. a)** — Biblioteka statyczna (. a)<br>**Aplikacja (. out)** — aplikacja (. out)<br>**Reguł programu make** — plik reguł programu make<br>
Użycie STL | Określa, C++ która Biblioteka standardowa ma być używana dla tej konfiguracji. | **Udostępniona biblioteka standardowa C++ GNU**<br>**Statyczna C++ Biblioteka GNU (-static)**<br>

::: moniker-end
