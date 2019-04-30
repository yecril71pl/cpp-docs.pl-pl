---
title: Ogólne właściwości (projekt języka C++ dla systemu Linux) | Dokumentacja firmy Microsoft
ms.date: 9/26/2017
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: bc4eb39d2d735f8f7f782d2827bf2b938c5c2457
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393054"
---
# <a name="general-properties-linux-c"></a>Właściwości ogólne (Linux C++)

Właściwość | Opis | Opcje
--- | ---| ---
Katalog wyjściowy | Określa ścieżkę względną do katalogu pliku wyjściowego; może zawierać zmienne środowiskowe.
Katalog pośredni | Określa ścieżkę względną do pośredniego katalogu plików; może zawierać zmienne środowiskowe.
Nazwa obiektu docelowego | Określa nazwę pliku, który zostanie wygenerowany przez projekt.
Rozszerzenie docelowe | Określa rozszerzenie pliku, który zostanie wygenerowany przez projekt. (Przykład: .a)
Rozszerzenia do usunięcia podczas oczyszczania | Rozdzielana średnikami Specyfikacja symboli wieloznacznych, które pliki w katalogu pośrednim mają zostać usunięte podczas oczyszczania lub ponownie skompiluj.
Plik dziennika kompilacji | Określa plik dziennika kompilacji do zapisu, gdy rejestrowanie kompilacji jest włączona.
Zestaw narzędzi platformy | Określa zestaw narzędzi, używana do tworzenia bieżącej konfiguracji; Jeśli nie jest używany zestaw, domyślny zestaw narzędzi
Zdalny kompilator | Maszyna docelowa lub urządzenie na potrzeby zdalnego kompilowania, wdrażania i debugowania.
Katalog główny kompilacji zdalnej | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu.
Katalog projektu kompilacji zdalnej | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu dla projektu.
Typ konfiguracji | Określa typ danych wyjściowych generowanych przez tę konfigurację. | **Biblioteka dynamiczna (SO)** — Biblioteka dynamiczna (SO)<br>**Biblioteka statyczna (.a)** — biblioteka statyczna (.a)<br>**Aplikacja (.out)** — aplikacja (.out)<br>**Plik reguł programu make** -pliku reguł programu make<br>
Użycie biblioteki STL | Określa, które standardowej biblioteki języka C++ do użycia dla tej konfiguracji. | **Udostępnione GNU standardowej biblioteki C++**<br>**Statyczne GNU standardowej biblioteki C++ (-statyczne)**<br>
