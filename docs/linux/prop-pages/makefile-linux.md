---
title: Właściwości ogólne (Linux C++ Makefile Project)| Dokumenty firmy Microsoft
ms.date: 06/07/2019
ms.assetid: 3dec6853-43f6-412b-9806-9bfad333a204
ms.openlocfilehash: 72a7919bc94be80acdbf7a2cef5b4a9875595545
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "79446151"
---
# <a name="makefile-project-properties-linux-c"></a>Właściwości projektu Makefile (Linux C++)

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

Jest to częściowa lista właściwości dostępnych w projekcie Linux Makefile. Wiele właściwości projektu Makefile są identyczne z właściwości projektu aplikacji konsoli Linux C++.

## <a name="general"></a>Ogólne

| Właściwość | Opis | Choices |
|--|--|--|
| Katalog wyjściowy | Określa względną ścieżkę do katalogu plików wyjściowych; mogą zawierać zmienne środowiskowe. |
| Katalog pośredni | Określa względną ścieżkę do katalogu plików pośrednich; mogą zawierać zmienne środowiskowe. |
| Tworzenie pliku dziennika | Określa plik dziennika kompilacji, do którym należy zapisywać podczas rejestrowania kompilacji. |
| Typ konfiguracji | Określa typ danych wyjściowych generowanych przez tę konfigurację. | **Biblioteka dynamiczna (.so)** - Biblioteka dynamiczna (.so)<br>**Biblioteka statyczna (.a)** — biblioteka statyczna (.a)<br>**Aplikacja (.out)** - Aplikacja (.out)<br>**Makefile** - Makefile<br> |
| Zdalna maszyna do kompilacji | Komputer docelowy lub urządzenie do użycia do zdalnej kompilacji, wdrażania i debugowania. |
| Katalog główny kompilacji zdalnej | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu zdalnym. |
| Katalog projektów kompilacji zdalnej | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu dla projektu. |

## <a name="debugging"></a>Debugowanie

Zobacz [Właściwości debugera (Linux C++)](debugging-linux.md)

## <a name="copy-sources"></a>Kopiuj źródła

Zobacz [Właściwości projektu Kopiuj źródła (Linux C++)](copy-sources-project.md).

## <a name="build-events"></a>Tworzenie zdarzeń

### <a name="pre-build-event"></a>Zdarzenie przed kompilacją

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia uruchamiania narzędzia zdarzeń przed kompilacją. |
| Opis | Określa opis narzędzia zdarzeń przed kompilacją do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wykluczone z kompilacji dla bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie lista może być dostarczana jako pary mapowania lokalnego do zdalnego przy użyciu składni w następujący sposób: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, gdzie plik lokalny można skopiować do określonej lokalizacji zdalnej w systemie zdalnym. |

### <a name="post-build-event"></a>Zdarzenie po kompilacji

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia dla narzędzia zdarzeń po kompilacji do uruchomienia. |
| Opis | Określa opis narzędzia zdarzeń po kompilacji do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wykluczone z kompilacji dla bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie lista może być dostarczana jako pary mapowania lokalnego do zdalnego przy użyciu składni w następujący sposób: fulllocalpath1:=fullremotepath1;fulllocalpath2:=fullremotepath2, gdzie plik lokalny można skopiować do określonej lokalizacji zdalnej w systemie zdalnym. |

### <a name="remote-pre-build-event"></a>Zdarzenie zdalnego wstępnego budowania

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia dla narzędzia zdarzeń pre-build do uruchomienia w systemie zdalnym. |
| Opis | Określa opis narzędzia zdarzeń przed kompilacją do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wykluczone z kompilacji dla bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania z systemu zdalnego. Opcjonalnie lista może być dostarczona jako zdalna do lokalnych par mapowania przy użyciu składni w następujący sposób: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, gdzie zdalny plik może być skopiowany do określonej lokalizacji na komputerze lokalnym. |

### <a name="remote-post-build-event"></a>Zdarzenie zdalnego po kompilacji

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia dla narzędzia zdarzeń po kompilacji, które ma być uruchamiane w systemie zdalnym. |
| Opis | Określa opis narzędzia zdarzeń po kompilacji do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wykluczone z kompilacji dla bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania z systemu zdalnego. Opcjonalnie lista może być dostarczona jako zdalna do lokalnych par mapowania przy użyciu składni w następujący sposób: fullremotepath1:=fulllocalpath1;fullremotepath2:=fulllocalpath2, gdzie zdalny plik może być skopiowany do określonej lokalizacji na komputerze lokalnym. |

## <a name="cc"></a>C/C++

### <a name="intellisense"></a>IntelliSense

Właściwości IntelliSense można ustawić na poziomie projektu lub pliku, aby zapewnić wskazówki dotyczące aparatu IntelliSense. Nie wpływają one na kompilację.

| Właściwość | Opis |
|--|--|
| Uwzględnij ścieżkę wyszukiwania | Określa ścieżkę wyszukiwania dołączania do rozwiązywania dołączonych plików. |
| Wymuszone zawiera | Określa pliki, które są wymuszane dołączona. |
| Definicje preprocesora | Określa preprocesor zdefiniowany przez pliki źródłowe. |
| Definicje przederocesora przeddefine | Określa co najmniej jedną niedrobnie wolną od przetwarzania preprocesora.     (/U[makro]) |
| Opcje dodatkowe | Określa dodatkowe przełączniki kompilatora, które mają być używane przez IntelliSense podczas analizowania plików Języka C++. |

### <a name="build"></a>Kompilacja

| Właściwość | Opis |
|--|--|
| Zbuduj wiersz polecenia | Określa wiersz polecenia uruchamiany dla polecenia "Build". |
| Odbuduj cały wiersz polecenia | Określa wiersz polecenia uruchamiany dla polecenia "Odbuduj wszystko". |
| Czysty wiersz polecenia | Określa wiersz polecenia uruchamiany dla polecenia "Wyczyść". |

### <a name="remote-build"></a>Kompilacja zdalna

| Właściwość | Opis |
|--|--|
| Zbuduj wiersz polecenia | Określa wiersz polecenia uruchamiany dla polecenia "Build". Jest to wykonywane w systemie zdalnym. |
| Odbuduj cały wiersz polecenia | Określa wiersz polecenia uruchamiany dla polecenia "Odbuduj wszystko". Jest to wykonywane w systemie zdalnym. |
| Czysty wiersz polecenia | Określa wiersz polecenia uruchamiany dla polecenia "Wyczyść". Jest to wykonywane w systemie zdalnym. |
| Dane wyjściowe | Określa dane wyjściowe generowane przez zdalną kompilację w systemie zdalnym. |

::: moniker-end
