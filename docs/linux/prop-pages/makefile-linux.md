---
title: Ogólne właściwości (projekt języka Linux C++ Makefile) | Dokumentacja firmy Microsoft
ms.date: 06/07/2019
ms.assetid: 3dec6853-43f6-412b-9806-9bfad333a204
ms.openlocfilehash: a64066ad3c8d7e6ca8bfa9d3d82670ff1da4b527
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821455"
---
# <a name="makefile-project-properties-linux-c"></a>Właściwości projektu pliku reguł programu make (Linux C++)

::: moniker range="vs-2015"

Pomoc techniczna Linux support jest dostępne w programie Visual Studio 2017 i nowszych wersjach.

::: moniker-end

::: moniker range=">=vs-2017"

To jest częściowa lista właściwości dostępnych w module Projekt pliku reguł programu make w systemie Linux. Wiele właściwości projektu pliku reguł programu make są identyczne z właściwości projektu aplikacji konsoli języka C++ dla systemu Linux.

## <a name="general"></a>Ogólne

Właściwość | Opis | Opcje
--- | ---| ---
Katalog wyjściowy | Określa ścieżkę względną do katalogu pliku wyjściowego; może zawierać zmienne środowiskowe.
Katalog pośredni | Określa ścieżkę względną do pośredniego katalogu plików; może zawierać zmienne środowiskowe.
Plik dziennika kompilacji | Określa plik dziennika kompilacji do zapisu, gdy rejestrowanie kompilacji jest włączona.
Typ konfiguracji | Określa typ danych wyjściowych generowanych przez tę konfigurację. | **Biblioteka dynamiczna (SO)** — Biblioteka dynamiczna (SO)<br>**Biblioteka statyczna (.a)** — biblioteka statyczna (.a)<br>**Aplikacja (.out)** — aplikacja (.out)<br>**Plik reguł programu make** -pliku reguł programu make<br>
Zdalny kompilator | Maszyna docelowa lub urządzenie na potrzeby zdalnego kompilowania, wdrażania i debugowania.
Katalog główny kompilacji zdalnej | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu.
Katalog projektu kompilacji zdalnej | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu dla projektu.

## <a name="debugging"></a>Debugowanie

Zobacz [debugera właściwości (Linux C++)](debugging-linux.md)

## <a name="copy-sources"></a>Kopiuj źródła

Zobacz [kopiowania źródeł właściwości projektu (Linux C++)](copy-sources-project.md).

## <a name="build-events"></a>Zdarzenia kompilacji

### <a name="pre-build-event"></a>Zdarzenie sprzed kompilacji

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia prekompilacyjnego do uruchomienia.
Opis | Określa opis narzędzia zdarzenia prekompilacyjnego do wyświetlenia.
Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie listę można przekazać jako lokalną do par mapowania zdalnego przy użyciu składni: pełna_ścieżka_lokalna_1: = pełna_ścieżka_zdalna_1; pełna_ścieżka_lokalna_2: = pełna_ścieżka_zdalna_2, gdzie można skopiować plik lokalny do określonej lokalizacji zdalnej w systemie zdalnym.

### <a name="post-build-event"></a>Zdarzenie po kompilacji

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia postkompilacyjnego do uruchomienia.
Opis | Określa opis narzędzia zdarzenia postkompilacyjnego do wyświetlenia.
Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie listę można przekazać jako lokalną do par mapowania zdalnego przy użyciu składni: pełna_ścieżka_lokalna_1: = pełna_ścieżka_zdalna_1; pełna_ścieżka_lokalna_2: = pełna_ścieżka_zdalna_2, gdzie można skopiować plik lokalny do określonej lokalizacji zdalnej w systemie zdalnym.

### <a name="remote-pre-build-event"></a>Zdalne zdarzenie Prekompilacyjne

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia prekompilacyjnego do uruchomienia w systemie zdalnym.
Opis | Określa opis narzędzia zdarzenia prekompilacyjnego do wyświetlenia.
Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania z systemu zdalnego. Opcjonalnie listę można przekazać jako zdalną do lokalnych par mapowania przy użyciu składni: pełna_ścieżka_zdalna_1: = pełna_ścieżka_lokalna_1; pełna_ścieżka_zdalna_2: = pełna_ścieżka_lokalna_2, gdzie plik zdalny można skopiować do określonej lokalizacji na komputerze lokalnym.

### <a name="remote-post-build-event"></a>Zdalne zdarzenie Pokompilacyjne

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia postkompilacyjnego do uruchomienia w systemie zdalnym.
Opis | Określa opis narzędzia zdarzenia postkompilacyjnego do wyświetlenia.
Użyj w kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania z systemu zdalnego. Opcjonalnie listę można przekazać jako zdalną do lokalnych par mapowania przy użyciu składni: pełna_ścieżka_zdalna_1: = pełna_ścieżka_lokalna_1; pełna_ścieżka_zdalna_2: = pełna_ścieżka_lokalna_2, gdzie plik zdalny można skopiować do określonej lokalizacji na komputerze lokalnym.

## <a name="cc"></a>C/C++

### <a name="intellisense"></a>IntelliSense

Właściwości funkcji IntelliSense można ustawić na poziomie projektu lub pliku w celu zapewnienia wskazówek w aparacie IntelliSense. Nie wpływają one kompilacji.

Właściwość | Opis
--- | ---
Ścieżka wyszukiwania plików dołączanych | Określa ścieżkę wyszukiwania dołączenia, aby rozpoznać pliki dołączone.
Wymuszone obejmuje | Określa pliki, których jest wymuszone dołączone.
Definicje preprocesora | Określa definicje preprocesora używane przez pliki źródłowe.
Usuń definicje preprocesora | Określa, że jedno anulowanie definicji preprocesora jeden lub więcej.     (/U[makro]))
Dodatkowe opcje | Określa dodatkowe przełączniki kompilatora ma być używany przez funkcję IntelliSense, podczas analizowania plików C++.

### <a name="build"></a>Kompilacja

Właściwość | Opis
--- | ---
Wiersz polecenia kompilacji | Określa wiersz polecenia umożliwiający uruchomienie polecenia "Kompiluj".
Wiersz poleceń rekompilacji wszystkiego | Określa wiersz polecenia umożliwiający uruchomienie polecenia "Kompiluj wszystko ponownie".
Wiersz polecenia Wyczyść | Określa wiersz polecenia umożliwiający uruchomienie polecenia "Wyczyść".

### <a name="remote-build"></a>Kompilacji zdalnej

Właściwość | Opis
--- | ---
Wiersz polecenia kompilacji | Określa wiersz polecenia umożliwiający uruchomienie polecenia "Kompiluj". Jest ono wykonywane w systemie zdalnym.
Wiersz poleceń rekompilacji wszystkiego | Określa wiersz polecenia umożliwiający uruchomienie polecenia "Kompiluj wszystko ponownie". Jest ono wykonywane w systemie zdalnym.
Wiersz polecenia Wyczyść | Określa wiersz polecenia umożliwiający uruchomienie polecenia "Wyczyść". Jest ono wykonywane w systemie zdalnym.
Dane wyjściowe | Określa pliki wynikowe, generowane przez kompilację zdalną w systemie zdalnym.

::: moniker-end
