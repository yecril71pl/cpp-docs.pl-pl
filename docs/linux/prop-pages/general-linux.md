---
title: Ogólne właściwości (projekt języka C++ dla systemu Linux) | Dokumentacja firmy Microsoft
ms.date: 06/07/2019
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: ce3683f11d80c253195b751b5eed364fbc04b68a
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821282"
---
# <a name="general-properties-linux-c"></a>Właściwości ogólne (Linux C++)

::: moniker range="vs-2015"

Pomoc techniczna Linux support jest dostępne w programie Visual Studio 2017 i nowszych wersjach.

::: moniker-end

::: moniker range=">=vs-2017"

Właściwość | Opis | Opcje
--- | ---| ---
Katalog wyjściowy | Określa ścieżkę względną do katalogu pliku wyjściowego; może zawierać zmienne środowiskowe.
Katalog pośredni | Określa ścieżkę względną do pośredniego katalogu plików; może zawierać zmienne środowiskowe.
Nazwa obiektu docelowego | Określa nazwę pliku, który zostanie wygenerowany przez projekt.
Rozszerzenie docelowe | Określa rozszerzenie pliku, który zostanie wygenerowany przez projekt. (Przykład: .a)
Rozszerzenia do usunięcia podczas oczyszczania | Rozdzielana średnikami Specyfikacja symboli wieloznacznych, które pliki w katalogu pośrednim mają zostać usunięte podczas oczyszczania lub ponownie skompiluj.
Plik dziennika kompilacji | Określa plik dziennika kompilacji do zapisu, gdy rejestrowanie kompilacji jest włączona.
Zestaw narzędzi platformy | Określa zestaw narzędzi, używana do tworzenia bieżącej konfiguracji; Jeśli nie jest używany zestaw, domyślny zestaw narzędzi
Zdalny kompilator | Maszyna docelowa lub urządzenie na potrzeby zdalnego kompilowania, wdrażania i debugowania. **Visual Studio 2019 wersji 16.1** można określić inną maszynę do debugowania w [debugowanie](debugging-linux.md) strony.
Katalog główny kompilacji zdalnej | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu.
Katalog projektu kompilacji zdalnej | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu dla projektu.
Typ konfiguracji | Określa typ danych wyjściowych generowanych przez tę konfigurację. | **Biblioteka dynamiczna (SO)** — Biblioteka dynamiczna (SO)<br>**Biblioteka statyczna (.a)** — biblioteka statyczna (.a)<br>**Aplikacja (.out)** — aplikacja (.out)<br>**Plik reguł programu make** -pliku reguł programu make<br>
Użycie biblioteki STL | Określa, które standardowej biblioteki języka C++ do użycia dla tej konfiguracji. | **Udostępnione GNU standardowej biblioteki C++**<br>**Statyczne GNU standardowej biblioteki C++ (-statyczne)**<br>

::: moniker-end

