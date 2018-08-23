---
title: Debuger właściwości (Linux C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 0c1c0fcc-a49b-451c-a5cb-ce9711fac064
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: df57a884186fe33d91de78647cc225f3a63a6f9f
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2018
ms.locfileid: "42465884"
---
# <a name="c-debugging-properties-linux-c"></a>C++, debugowanie — właściwości (Linux C++)

Właściwość | Opis | Opcje
--- | ---| ---
Polecenie Przeduruchomieniowe | Polecenie, które jest uruchamiane w powłoce przed rozpoczęciem debugowania i uruchomieniem debugera jest uruchomiony i może służyć do modyfikowania środowiska debugowania.
Program | Pełna ścieżka do programu do debugowania w systemie zdalnym. Jest to ścieżka w systemie zdalnym. Jeśli pole pozostanie puste, lub bez zmian, jego wartość domyślna to bieżące dane wyjściowe projektu.
Argumenty programu | Argumenty wiersza polecenia do przekazania do debugowanego programu.
Katalog roboczy | Katalog roboczy aplikacji zdalnej. Domyślnie katalogu macierzystego użytkownika.
Dodatkowe polecenia debugera | Dodatkowe polecenia gdb dla debugera do uruchomienia przed rozpoczęciem debugowania.
Numer portu debugera | Numer portu do komunikacji z debugerem ze zdalnym debugerem. Port nie może być używany lokalnie. Ta wartość musi być dodatnią z przedziału od 1 do 65535. Jeśli nie podano numeru wolnego portu zostanie użyta.
Numer portu debugera zdalnego | Numer portu, na którym serwer debugera zdalnego (serwera gdbserver) nasłuchuje w systemie zdalnym. Port nie może być używany w systemie zdalnym. Ta wartość musi być dodatnią z przedziału od 1 do 65535. Jeśli nie podano numeru wolnego portu rozpoczynającego się od 4444 będą używane.
Tryb debugowania | Określa, jak interfejsy debugera przy użyciu debugera gdb. W trybie gdb debuger dysków gdb przez powłokę w systemie zdalnym. W trybie gdbserver następuje lokalne gdb działa lokalnie i nawiązanie połączenia z serwera gdbserver działa zdalnie. | **serwera gdbserver**<br>**gdb**<br>
Dodatkowa ścieżka wyszukiwania symboli | Dodatkowa ścieżka wyszukiwania symboli debugowania (solib-search-path).
Debuguj procesy podrzędne | Określa, czy włączyć debugowanie procesów podrzędnych.
Włącz Python formatowanie kodu | Włącz formatowanie kodu dla wartości wyrażenia. Obsługiwane tylko w trybie debugowania gdb.
Plik wizualizacji | Domyślny natywny plik wizualizacji (natvis) zawierający dyrektywy dotyczące wizualizacji dla typów SLT. Inne pliki natvis, które należą do bieżącego rozwiązania zostaną załadowane automatycznie.
Mapa ścieżek plików dodatkowych źródeł | Dodatkowe równoważniki służące debugerowi do mapowania Windows źródła nazwy pliku do nazw plików źródłowych systemu Linux. Format to "\<ścieżki systemu windows > =\<ścieżka w systemie linux >;...". Nazwa pliku źródłowego, znajdują się w ścieżce Windows będzie się tak, jakby to zostało znalezione w tej samej pozycji względnej w ścieżce systemu Linux. Pliki znalezione w projekcie lokalnym nie wymagają dodatkowego mapowania.
