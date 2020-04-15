---
title: Właściwości ogólne (Projekt Linux C++)
description: W tym artykule opisano właściwości projektu systemu Linux, które można ustawić w programie Visual Studio na stronie Właściwości ogólne.
ms.date: 01/14/2020
ms.assetid: 56c800a9-3df9-4196-87b2-81adb00e4767
ms.openlocfilehash: 832f10ca2c95e40ff7ece23462105fa49014aa5d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "79446163"
---
# <a name="general-properties-linux-c"></a>Właściwości ogólne (Linux C++)

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

| Właściwość | Opis | Choices |
|--|--|--|
| Katalog wyjściowy | Określa względną ścieżkę do katalogu plików wyjściowych. Może zawierać zmienne środowiskowe. |
| Katalog pośredni | Określa względną ścieżkę do katalogu plików pośrednich. Może zawierać zmienne środowiskowe. |
| Nazwa obiektu docelowego | Określa nazwę pliku, który generuje ten projekt. |
| Rozszerzenie celu | Określa rozszerzenie pliku (na `.a`przykład), które generuje ten projekt. |
| Rozszerzenia do usunięcia przy czyszczeniu | Semi-dwukropek-rozdzielone symbole wieloznaczne specyfikacji, dla których pliki w katalogu pośrednim do usunięcia na czyste lub odbudować. |
| Tworzenie pliku dziennika | Określa plik dziennika kompilacji, do którym należy zapisywać podczas rejestrowania kompilacji. |
| Zestaw narzędzi platformy | Określa zestaw narzędzi używany do tworzenia bieżącej konfiguracji. Jeśli nie jest ustawiona, używany jest domyślny zestaw narzędzi. |
| Zdalna maszyna do kompilacji | Wyświetla komputer docelowy lub urządzenie do użycia do zdalnej kompilacji, wdrażania i debugowania. Docelowe połączenie z komputerem można dodawać lub edytować za pomocą Menedżera połączeń **Narzędzia** > **Opcje** > **wieloplatformowe** > **Connection Manager**.<br /> **Visual Studio 2019 w wersji 16.1** Można określić inny komputer do debugowania na [debugowania](debugging-linux.md) strony. |
| Katalog główny kompilacji zdalnej | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu zdalnym. |
| Katalog projektów kompilacji zdalnej | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu dla projektu. |
| Katalog zdalnego wdrażania | **Visual Studio 2019 w wersji 16.1** Określa ścieżkę katalogową na komputerze zdalnym lub urządzeniu w celu wdrożenia projektu. |
| Katalogi dołączania kopii zdalnych | **Visual Studio 2019 w wersji 16.5**  Lista katalogów do kopiowania cyklicznie z obiektu docelowego systemu Linux. Ta właściwość ma wpływ na zdalną kopię nagłówka dla IntelliSense, ale nie kompilacji. Może być używany, gdy **IntelliSense używa kompilatora domyślne** jest ustawiona na false. Użyj **dodatkowych katalogów dołączanych** na karcie C/C++ Ogólne, aby określić dodatkowe katalogi dołączane do użycia zarówno w programie IntelliSense, jak i kompilacji. |
| Katalogi wykluczeń kopiowania zdalnego | **Visual Studio 2019 w wersji 16.5** Lista *katalogów,* które nie można kopiować z obiektu docelowego Linuksa. Zazwyczaj ta właściwość jest używana do usuwania podkatalogów katalogów dołączanych. |
| IntelliSense używa ustawień domyślnych kompilatora | **Visual Studio 2019 w wersji 16.5** Czy kwerendy kompilatora odwołuje się do tego projektu dla jego domyślnej listy dołącz lokalizacje. Te lokalizacje są automatycznie dodawane do listy katalogów zdalnych do skopiowania. Ta właściwość jest false tylko wtedy, gdy kompilator nie obsługuje parametrów podobnych do gcc. Kompilatory gcc i clang obsługują zapytania dotyczące katalogów `g++ -x c++ -E -v -std=c++11`dołączanych (na przykład ). |
| Typ konfiguracji | Określa typ danych wyjściowych generowanych przez tę konfigurację. | **Biblioteka dynamiczna (.so)**<br/><br/>**Biblioteka statyczna (.a)**<br/><br/>**Aplikacja (.out)**<br/><br/>**Makefile** |
| Korzystanie z STL | Określa, która biblioteka standardowa języka C++ ma być używana dla tej konfiguracji. | **Udostępniona biblioteka GNU Standard C++**<br/><br/>**Statyczna standardowa biblioteka C++ GNU (-statyczna)** |

::: moniker-end
