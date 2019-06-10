---
title: Debuger właściwości (Linux C++) | Dokumentacja firmy Microsoft
ms.date: 06/07/2019
ms.assetid: 0c1c0fcc-a49b-451c-a5cb-ce9711fac064
ms.openlocfilehash: d76e398d648db7c5cf65e4ca2bb1665aef4359ad
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821399"
---
# <a name="c-debugging-properties-linux-c"></a>C++, debugowanie — właściwości (Linux C++)

::: moniker range="vs-2015"

Pomoc techniczna Linux support jest dostępne w programie Visual Studio 2017 i nowszych wersjach.

::: moniker-end

::: moniker range=">=vs-2017"

Właściwość | Opis | Opcje
--- | ---| ---
Komputer do debugowania zdalnego | **Visual Studio 2019 wersji 16.1**: Określa komputer, aby zdebugować program na. Może być inna niż maszynę kompilacji zdalnej, która jest określona w [ogólne](general-linux.md) strony.
Polecenie Przeduruchomieniowe | Uruchamia polecenie, które jest uruchamiane w powłoce przed debugera, który może służyć do modyfikowania środowiska debugowania.
Program | Pełna ścieżka w systemie zdalnym do programu do debugowania. Jeśli pole pozostanie puste lub niezmieniony, domyślnie bieżące dane wyjściowe projektu.
Argumenty programu | Argumenty wiersza polecenia do przekazania do debugowanego programu.
Katalog roboczy | Katalog roboczy aplikacji zdalnej. Domyślnie katalogu macierzystego użytkownika.
Dodatkowe polecenia debugera | Dodatkowe `gdb` polecenia dla debugera do uruchomienia przed rozpoczęciem debugowania.
Numer portu debugera | Numer portu do komunikacji z debugerem ze zdalnym debugerem. Port nie może być używany lokalnie. Ta wartość musi być dodatnia i od 1 do 65535. Jeśli nie podano numeru wolnego portu jest używany.
Numer portu debugera zdalnego | Numer portu, debuger zdalny serwer `gdbserver` nasłuchuje w systemie zdalnym. Port nie może być używany w systemie zdalnym. Ta wartość musi być dodatnia i od 1 do 65535. Jeśli nie podano numeru wolnego portu rozpoczynającego się od 4444 jest używany.
Tryb debugowania | Określa, jak interfejsy debugera za pomocą `gdb`. W *trybie gdb*, dyski debugera `gdb` przez powłokę w systemie zdalnym. W *trybie gdbserver następuje lokalne*, `gdb` działa lokalnie, a następnie łączy `gdbserver` działa zdalnie. | **gdbserver**<br/>**gdb**
Dodatkowa ścieżka wyszukiwania symboli | Dodatkowa ścieżka wyszukiwania symboli debugowania (solib-search-path).
Debuguj procesy podrzędne | Określa, czy włączyć debugowanie procesów podrzędnych.
Włącz Python formatowanie kodu | Włącz formatowanie kodu dla wartości wyrażenia. Obsługiwane tylko w trybie debugowania gdb.
Plik wizualizacji | Domyślny natywny plik wizualizacji (natvis) zawierający dyrektywy dotyczące wizualizacji dla typów SLT. Inne pliki natvis, które należą do bieżącego rozwiązania są ładowane automatycznie.
Mapa ścieżek plików dodatkowych źródeł | Dodatkowe równoważniki służące debugerowi do mapowania Windows źródła nazwy pliku do nazw plików źródłowych systemu Linux. Format to "\<ścieżki systemu windows > =\<ścieżka w systemie linux >;...". Nazwa pliku źródłowego, znajdują się w ścieżce Windows odwołuje się tak, jakby znajduje się w tej samej pozycji względnej w ścieżce systemu Linux. Pliki znalezione w projekcie lokalnym nie wymagają dodatkowego mapowania.

::: moniker-end
