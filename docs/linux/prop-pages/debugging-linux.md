---
title: Właściwości debugera (Linux C++)| Dokumenty firmy Microsoft
ms.date: 06/07/2019
ms.assetid: 0c1c0fcc-a49b-451c-a5cb-ce9711fac064
ms.openlocfilehash: bebee7a2b3bcfd880a538acae35c9616b3b1bd46
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "79446179"
---
# <a name="c-debugging-properties-linux-c"></a>Właściwości debugowania języka C++ (Linux C++)

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

| Właściwość | Opis | Choices |
|--|--|--|
| Zdalne debugowanie komputera | **Visual Studio 2019 w wersji 16.1**: Określa komputer do debugowania programu. Może się różnić od komputera kompilacji zdalnej, który jest określony na stronie [Ogólne.](general-linux.md) Docelowe połączenie z komputerem można dodawać lub edytować za pomocą Menedżera połączeń **Narzędzia** > **Opcje** > **wieloplatformowe** > **Connection Manager**. |
| Polecenie przed uruchomieniem | Polecenie, które jest uruchamiane w powłoce przed uruchomieniem debugera, które może mieć wpływ na środowisko debugowania. |
| Program | Pełna ścieżka w systemie zdalnym do programu do debugowania. Jeśli pozostanie puste lub niezmienione, domyślnie jest to bieżące dane wyjściowe projektu. |
| Argumenty programu | Argumenty wiersza polecenia, aby przekazać do programu jest debugowane. |
| Katalog roboczy | Katalog roboczy aplikacji zdalnej. Domyślnie katalog domowy użytkownika. |
| Dodatkowe polecenia debugera | Dodatkowe `gdb` polecenia dla debugera do uruchomienia przed rozpoczęciem debugowania. |
| Numer portu debugera | Numer portu do komunikacji debugera ze zdalnym debugerem. Port nie może być używany lokalnie. Ta wartość musi być dodatnia i między 1 a 65535. Jeśli nie podano, używany jest numer portu wolnego. |
| Numer portu zdalnego debugera | Numer portu, na którym serwer `gdbserver` zdalnego debugera nasłuchuje w systemie zdalnym. Port nie może być używany w systemie zdalnym. Ta wartość musi być dodatnia i między 1 a 65535. Jeśli nie podano, używany jest bezpłatny numer portu zaczynając od 4444. |
| Tryb debugowania | Określa sposób interfejsów debugera z programem `gdb`. W *trybie gdb*debuger przejeżdża `gdb` przez powłokę w systemie zdalnym. W *trybie gdbserver*działa `gdb` lokalnie `gdbserver` i łączy się z uruchomieniem zdalnie. | **gdbserver (serwer gdbserver)**<br/>**Gdb** |
| Dodatkowe ścieżki wyszukiwania symboli | Dodatkowa ścieżka wyszukiwania symboli debugowania (ścieżka wyszukiwania solib). |
| Debugowanie procesów podrzędnych | Określa, czy debugowanie procesów podrzędnych ma być włączane. |
| Włącz drukowanie języka Python | Włącz ładne drukowanie wartości wyrażeń. Obsługiwane tylko w trybie debugowania gdb. |
| Plik wizualizacji | Domyślny macierzysty plik wizualizacji (.natvis) zawierający dyrektywy wizualizacji dla typów SLT. Inne pliki .natvis, które należą do bieżącego rozwiązania są ładowane automatycznie. |
| Mapa ścieżki pliku dodatkowych źródeł | Dodatkowe równoważności ścieżki dla debugera do użycia do mapowania nazw plików źródłowych systemu Windows na nazwy plików źródłowych systemu Linux. Format jest\<" windows-path>\<= linux-path>;...". Nazwa pliku źródłowego znaleziona pod ścieżką systemu Windows jest przywoływanie tak, jakby została znaleziona w tej samej pozycji względnej pod ścieżką systemu Linux. Pliki znalezione w projekcie lokalnym nie wymagają dodatkowego mapowania. |

::: moniker-end
