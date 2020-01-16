---
title: Właściwości ogólne (projekt C++ systemu Linux)
description: Opisuje właściwości projektu systemu Linux, które można ustawić w programie Visual Studio na stronie właściwości ogólne.
ms.date: 01/14/2020
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: 6d598e9d52037d709cba87d98ad375455d8c00b0
ms.sourcegitcommit: 49e4fb3e0300fe86c814130661f1bf68b16e72e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "76031350"
---
# <a name="general-properties-linux-c"></a>Właściwości ogólne (Linux C++)

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

Właściwość | Opis | Choices
--- | ---| ---
Katalog wyjściowy | Określa ścieżkę względną do katalogu pliku wyjściowego. Może zawierać zmienne środowiskowe.
Katalog pośredni | Określa ścieżkę względną do katalogu pliku pośredniego. Może zawierać zmienne środowiskowe.
Nazwa docelowa | Określa nazwę pliku, który generuje ten projekt.
Rozszerzenie docelowe | Określa rozszerzenie pliku (na przykład `.a`), które generuje ten projekt.
Rozszerzenia do usunięcia podczas czyszczenia | Rozdzielana średnikami Specyfikacja symboli wieloznacznych, dla których pliki w katalogu pośrednim mają zostać usunięte podczas czyszczenia lub odbudowy.
Plik dziennika kompilacji | Określa plik dziennika kompilacji, w którym ma zostać zapisany wpis, gdy rejestrowanie kompilacji jest włączone.
Zestaw narzędzi platformy | Określa zestaw narzędzi używany do kompilowania bieżącej konfiguracji. Jeśli nie zostanie ustawiona, używany jest domyślny zestaw narzędzi.
Zdalna maszyna kompilacji | Maszyna docelowa lub urządzenie, które ma być używane do zdalnego kompilowania, wdrażania i debugowania. **Visual Studio 2019 w wersji 16,1** Na stronie [debugowanie](debugging-linux.md) można określić inną maszynę na potrzeby debugowania.
Zdalny katalog główny kompilacji | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu.
Katalog projektu kompilacji zdalnej | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu dla projektu.
Katalog zdalnego wdrażania | **Visual Studio 2019 w wersji 16,1** Określa ścieżkę katalogu na komputerze zdalnym lub urządzeniu do wdrożenia projektu.
Zdalne kopiowanie katalogów | **Visual Studio 2019 w wersji 16,5**  Lista katalogów, które mają zostać skopiowane rekursywnie z docelowego systemu Linux. Ta właściwość ma wpływ na zdalną kopię nagłówka dla funkcji IntelliSense, ale nie kompilacji. Można go użyć, gdy **Funkcja IntelliSense używa domyślnych wartości kompilatora** , ma wartość false. Użyj **dodatkowych katalogów include** na karcie C/C++ ogólne, aby określić dodatkowe katalogi dołączane do użycia zarówno dla technologii IntelliSense, jak i kompilacji.
Kopia zdalna — Wyklucz katalogi | **Visual Studio 2019 w wersji 16,5** Lista katalogów, które *nie* są kopiowane z lokalizacji docelowej systemu Linux. Zazwyczaj ta właściwość służy do usuwania podkatalogów katalogów include.
Technologia IntelliSense używa domyślnych wartości kompilatora | **Visual Studio 2019 w wersji 16,5** Określa, czy ma być wysyłany zapytanie do kompilatora, do którego odwołuje się ten projekt, dla jego domyślnej listy lokalizacji dołączania Te lokalizacje są automatycznie dodawane do listy katalogów zdalnych do skopiowania. Tę właściwość należy ustawić na wartość false, jeśli kompilator nie obsługuje parametrów takich jak. Kompilatory w zatoce i Clang obsługują zapytania dotyczące katalogów dołączanych (na przykład `g++ -x c++ -E -v -std=c++11`).
Typ konfiguracji | Określa typ danych wyjściowych generowanych przez tę konfigurację. | **Biblioteka dynamiczna (. so)**<br/>**Biblioteka statyczna (. a)**<br/>**Aplikacja (. out)**<br/>**Make**
Użycie STL | Określa, C++ która Biblioteka standardowa ma być używana dla tej konfiguracji. | **Udostępniona biblioteka standardowa C++ GNU**<br/>**Statyczna C++ Biblioteka GNU (-static)**

::: moniker-end
