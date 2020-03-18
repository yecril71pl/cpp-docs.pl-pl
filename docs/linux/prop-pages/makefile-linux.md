---
title: Ogólne właściwości (projekt C++ pliku reguł programu make systemu Linux) | Microsoft Docs
ms.date: 06/07/2019
ms.assetid: 3dec6853-43f6-412b-9806-9bfad333a204
ms.openlocfilehash: 72a7919bc94be80acdbf7a2cef5b4a9875595545
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446151"
---
# <a name="makefile-project-properties-linux-c"></a>Właściwości projektu pliku reguł programu C++Make (Linux)

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

Jest to częściowa lista właściwości dostępnych w projekcie reguł programu make systemu Linux. Wiele właściwości projektu pliku reguł programu make jest identycznych z właściwościami projektu aplikacji konsolowych systemu Linux C++ .

## <a name="general"></a>Ogólne

| Właściwość | Opis | Decyzji |
|--|--|--|
| Katalog wyjściowy | Określa ścieżkę względną do katalogu pliku wyjściowego; może zawierać zmienne środowiskowe. |
| Katalog pośredni | Określa ścieżkę względną do pośredniego katalogu plików; może zawierać zmienne środowiskowe. |
| Plik dziennika kompilacji | Określa plik dziennika kompilacji, w którym ma zostać zapisany wpis, gdy rejestrowanie kompilacji jest włączone. |
| Typ konfiguracji | Określa typ danych wyjściowych generowanych przez tę konfigurację. | **Biblioteka dynamiczna (. so)** — Biblioteka dynamiczna (. tak)<br>**Biblioteka statyczna (. a)** — Biblioteka statyczna (. a)<br>**Aplikacja (. out)** — aplikacja (. out)<br>**Reguł programu make** — plik reguł programu make<br> |
| Zdalna maszyna kompilacji | Maszyna docelowa lub urządzenie, które ma być używane do zdalnego kompilowania, wdrażania i debugowania. |
| Zdalny katalog główny kompilacji | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu. |
| Katalog projektu kompilacji zdalnej | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu dla projektu. |

## <a name="debugging"></a>Debugowanie

Zobacz [Właściwości debugera (Linux C++)](debugging-linux.md)

## <a name="copy-sources"></a>Kopiuj źródła

Zobacz [Kopiuj źródła właściwości projektu (Linux C++)](copy-sources-project.md).

## <a name="build-events"></a>Zdarzenia kompilacji

### <a name="pre-build-event"></a>Zdarzenie sprzed kompilacji

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia dla narzędzia zdarzenia przed kompilacją, które ma zostać uruchomione. |
| Opis | Określa opis narzędzia zdarzenia przed kompilacją do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie listę można dostarczyć jako lokalną do zdalnych par mapowania przy użyciu składni podobnej do następującej: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, gdzie plik lokalny można skopiować do określonej lokalizacji zdalnej w systemie zdalnym. |

### <a name="post-build-event"></a>Zdarzenie po kompilacji

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia dla narzędzia zdarzenia po kompilacji, które ma zostać uruchomione. |
| Opis | Określa opis narzędzia zdarzenia po kompilacji do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie listę można dostarczyć jako lokalną do zdalnych par mapowania przy użyciu składni podobnej do następującej: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, gdzie plik lokalny można skopiować do określonej lokalizacji zdalnej w systemie zdalnym. |

### <a name="remote-pre-build-event"></a>Zdalne zdarzenie sprzed kompilacji

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia dla narzędzia zdarzenia przed kompilacją do uruchomienia w systemie zdalnym. |
| Opis | Określa opis narzędzia zdarzenia przed kompilacją do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania z systemu zdalnego. Opcjonalnie listę można dostarczyć jako zdalna do lokalnych par mapowania przy użyciu składni podobnej do następującej: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, gdzie plik zdalny można skopiować do określonej lokalizacji na komputerze lokalnym. |

### <a name="remote-post-build-event"></a>Zdalne zdarzenie po kompilacji

| Właściwość | Opis |
|--|--|
| Wiersz polecenia | Określa wiersz polecenia dla narzędzia zdarzenia po kompilacji do uruchomienia w systemie zdalnym. |
| Opis | Określa opis narzędzia zdarzenia po kompilacji do wyświetlenia. |
| Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji. |
| Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania z systemu zdalnego. Opcjonalnie listę można dostarczyć jako zdalna do lokalnych par mapowania przy użyciu składni podobnej do następującej: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, gdzie plik zdalny można skopiować do określonej lokalizacji na komputerze lokalnym. |

## <a name="cc"></a>C/C++

### <a name="intellisense"></a>IntelliSense

Właściwości IntelliSense można ustawić na poziomie projektu lub pliku, aby zapewnić wskazówki dotyczące aparatu IntelliSense. Nie wpływają one na kompilację.

| Właściwość | Opis |
|--|--|
| Ścieżka wyszukiwania dołączania | Określa ścieżkę wyszukiwania dołączania do rozpoznawania dołączonych plików. |
| Wymuszone dołączenia | Określa pliki, które są objęte wymuszone. |
| Definicje preprocesora | Określa Definicje preprocesora używane przez pliki źródłowe. |
| Usuń Definicje preprocesora | Określa co najmniej jedną definicję preprocesora.     (/U [makro]) |
| Opcje dodatkowe | Określa dodatkowe przełączniki kompilatora, które mają być używane przez funkcję C++ IntelliSense podczas analizowania plików. |

### <a name="build"></a>Kompilacja

| Właściwość | Opis |
|--|--|
| Wiersz polecenia kompilacji | Określa wiersz polecenia do uruchomienia polecenia "Kompiluj". |
| Kompiluj ponownie wszystkie wiersze polecenia | Określa wiersz polecenia do uruchomienia dla polecenia "Skompiluj ponownie wszystko". |
| Wyczyść wiersz polecenia | Określa wiersz polecenia do uruchomienia polecenia "Wyczyść". |

### <a name="remote-build"></a>Kompilacja zdalna

| Właściwość | Opis |
|--|--|
| Wiersz polecenia kompilacji | Określa wiersz polecenia do uruchomienia polecenia "Kompiluj". Jest ono wykonywane w systemie zdalnym. |
| Kompiluj ponownie wszystkie wiersze polecenia | Określa wiersz polecenia do uruchomienia dla polecenia "Skompiluj ponownie wszystko". Jest ono wykonywane w systemie zdalnym. |
| Wyczyść wiersz polecenia | Określa wiersz polecenia do uruchomienia polecenia "Wyczyść". Jest ono wykonywane w systemie zdalnym. |
| Dane wyjściowe | Określa dane wyjściowe generowane przez kompilację zdalną w systemie zdalnym. |

::: moniker-end
