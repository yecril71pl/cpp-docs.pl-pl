---
title: Właściwości ogólne (Linux C++ projektu pliku reguł programu make) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 3dec6853-43f6-412b-9806-9bfad333a204
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 6fb23d2c7275788b05fe4450613770c268ca6c64
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705702"
---
# <a name="makefile-project-properties-linux-c"></a>Właściwości projektu pliku reguł programu make (Linux C++)

To jest częściowa lista właściwości dostępne w projekcie systemu Linux pliku reguł programu make. Wiele właściwości projektu pliku reguł programu make są takie same jak właściwości projektu aplikacji Konsolowej C++ systemu Linux.

## <a name="general"></a>Ogólne

Właściwość | Opis | Opcje
--- | ---| ---
Katalog wyjściowy | Określa ścieżkę względną do katalogu pliku wyjściowego; może zawierać zmienne środowiskowe.
Katalog pośredni | Określa ścieżkę względną do pośredniego katalogu plików; może zawierać zmienne środowiskowe.
Tworzenie pliku dziennika | Określa plik dziennika kompilacji do zapisu, gdy rejestrowanie kompilacji jest włączona.
Typ konfiguracji | Określa typ danych wyjściowych generowanych przez tę konfigurację. | **Dynamicznymi (.so)** -dynamicznymi (.so)<br>**Biblioteka statyczna (.a)** — biblioteka statyczna (tj.)<br>**Aplikacji (.out)** -aplikacji (.out)<br>**Pliku reguł programu make** -pliku reguł programu make<br>
Maszyny zdalnej kompilacji | Maszyna docelowa lub urządzenie na potrzeby kompilacji zdalnej, wdrażanie i debugowanie.
Katalog główny kompilacji zdalnej | Określa ścieżkę do katalogu na urządzeniu lub komputerze zdalnym.
Katalog projektu kompilacji zdalnej | Określa ścieżkę do katalogu na komputerze zdalnym lub urządzeniu dla projektu.

## <a name="debugging"></a>Debugowanie

Zobacz [debugera właściwości (Linux C++)](debugging-linux.md)

## <a name="copy-sources"></a>Skopiuj źródeł

Zobacz [kopiowania źródła właściwości projektu (Linux C++)](copy-sources-project.md).

## <a name="build-events"></a>Zdarzenia kompilacji

### <a name="pre-build-event"></a>Zdarzenia Prekompilacyjnego

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia prekompilacyjnego do uruchomienia.
Opis | Określa opis narzędzia zdarzenia prekompilacyjnego do wyświetlenia.
Używaj podczas kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie listy można podać jako lokalnego z parami mapowania zdalnego przy użyciu składni następująco: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, w której plik lokalny mogą zostać skopiowane do określonej lokalizacji zdalnego w systemie zdalnym.

### <a name="post-build-event"></a>Zdarzenie mające miejsce po kompilacji

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia postkompilacyjnego do uruchomienia.
Opis | Określa opis narzędzia zdarzenia postkompilacyjnego do wyświetlenia.
Używaj podczas kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki do skopiowania do systemu zdalnego. Opcjonalnie listy można podać jako lokalnego z parami mapowania zdalnego przy użyciu składni następująco: fulllocalpath1: = fullremotepath1; fulllocalpath2: = fullremotepath2, w której plik lokalny mogą zostać skopiowane do określonej lokalizacji zdalnego w systemie zdalnym.

### <a name="remote-pre-build-event"></a>Zdalne zdarzenia Prekompilacyjnego

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia prekompilacyjnego do uruchomienia w systemie zdalnym.
Opis | Określa opis narzędzia zdarzenia prekompilacyjnego do wyświetlenia.
Używaj podczas kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki, aby skopiować z systemu zdalnego. Opcjonalnie listy można podać jako zdalnej z parami mapowania lokalnych przy użyciu składni następująco: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, w której pliku zdalnego mogą zostać skopiowane do określonej lokalizacji na komputerze lokalnym.

### <a name="remote-post-build-event"></a>Zdalne zdarzenie mające miejsce po kompilacji

Właściwość | Opis
--- | ---
Wiersz polecenia | Określa wiersz poleceń dla narzędzia zdarzenia postkompilacyjnego do uruchomienia w systemie zdalnym.
Opis | Określa opis narzędzia zdarzenia postkompilacyjnego do wyświetlenia.
Używaj podczas kompilacji | Określa, czy to zdarzenie kompilacji jest wyłączone z kompilacji w bieżącej konfiguracji.
Dodatkowe pliki do skopiowania | Określa dodatkowe pliki, aby skopiować z systemu zdalnego. Opcjonalnie listy można podać jako zdalnej z parami mapowania lokalnych przy użyciu składni następująco: fullremotepath1: = fulllocalpath1; fullremotepath2: = fulllocalpath2, w której pliku zdalnego mogą zostać skopiowane do określonej lokalizacji na komputerze lokalnym.

## <a name="cc"></a>C/C++

### <a name="intellisense"></a>IntelliSense

Właściwości IntelliSense można ustawiać na poziomie projektu lub pliku zapewnienie wskazówki dotyczące aparatu IntelliSense. Nie ma wpływu na kompilacji.

Właściwość | Opis
--- | ---
Ścieżki wyszukiwania załączania | Określa ścieżkę wyszukiwania include będą pliki załączone.
Wymuszone obejmuje | Określa pliki, które będą uwzględnione.
Definicje preprocesora | Określa definicje preprocesora używane przez pliki źródłowe.
Usuń definicje preprocesora | Określa, że co najmniej jeden anulowanie definicji preprocesora.     (/U[macro])
Dodatkowe opcje | Określa dodatkowe przełączniki kompilatora używane przez funkcję IntelliSense, podczas analizowania plików C++.

### <a name="build"></a>Kompilacja

Właściwość | Opis
--- | ---
Wiersz polecenia kompilacji | Określa wiersz polecenia, aby uruchomić polecenie "Kompiluj".
Wiersz poleceń rekompilacji wszystkiego | Określa wiersz polecenia, aby uruchomić polecenie "Skompiluj ponownie wszystko".
Wiersz poleceń oczyszczenia | Określa wiersz polecenia, aby uruchomić polecenie "Czyść".

### <a name="remote-build"></a>Kompilacji zdalnej

Właściwość | Opis
--- | ---
Wiersz polecenia kompilacji | Określa wiersz polecenia, aby uruchomić polecenie "Kompiluj". Jest to wykonywane w systemie zdalnym.
Wiersz poleceń rekompilacji wszystkiego | Określa wiersz polecenia, aby uruchomić polecenie "Skompiluj ponownie wszystko". Jest to wykonywane w systemie zdalnym.
Wiersz poleceń oczyszczenia | Określa wiersz polecenia, aby uruchomić polecenie "Czyść". Jest to wykonywane w systemie zdalnym.
Dane wyjściowe | Określa pliki wynikowe, generowane przez kompilację zdalnego w systemie zdalnym.
