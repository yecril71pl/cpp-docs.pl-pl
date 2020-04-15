---
title: Właściwości konsolidatora (Linux C++)
ms.date: 06/07/2019
ms.assetid: a0243a94-8164-425b-b2fe-b84ff363d546
ms.openlocfilehash: 934e639199d663cba391c9913b067f32e5e32165
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "79441286"
---
# <a name="linker-properties-linux-c"></a>Właściwości konsolidatora (Linux C++)

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="general"></a>Ogólne

| Właściwość | Opis | Choices |
|--|--|--|
| Plik wyjściowy | Opcja zastępuje domyślną nazwę i lokalizację programu tworzonego przez konsolidator. (-o) |
| Pokaż postęp | Drukuje komunikaty postępu konsolidatora. |
| Wersja | Opcja -version informuje konsolidatora o umieszczeniu numeru wersji w nagłówku pliku wykonywalnego. |
| Włącz pełne dane wyjściowe | Opcja -verbose informuje konsolidatora do wytłumanych komunikatów do debugowania. |
| Ślad | Opcja --trace informuje konsolidatora o wysuwu plików wejściowych podczas przetwarzania. |
| Ślady symboli | Wydrukuj listę plików, w których pojawia się symbol. (--trace-symbol=symbol) |
| Drukuj mapę | Opcja --print-map informuje konsolidatora o wykreślenie mapy łącza. |
| Zgłaszanie nierozwiązanych odwołań do symboli | Ta opcja po włączeniu spowoduje raportowanie nierozwiązanych odniesień do symboli. |
| Optymalizacja pod kątem użycia pamięci | Optymalizuj pod kątem użycia pamięci, w razie potrzeby ponownie odczytując tabele symboli. |
| Ścieżka wyszukiwania biblioteki udostępnionej | Umożliwia użytkownikowi wypełnianie ścieżki wyszukiwania biblioteki udostępnionej. (-rpath-link=ścieżka) |
| Dodatkowe katalogi bibliotek | Umożliwia użytkownikowi zastąpienie ścieżki biblioteki środowiskowej. (-L). |
| Konsolidator | Określa program do wywołania podczas łączenia lub ścieżkę do konsolidatora w systemie zdalnym. |
| Limit czasu łącza | Limit czasu łączenia zdalnego w milisekundach. |
| Kopiuj dane wyjściowe | Określa, czy plik wyjściowy kompilacji ma być kopiowany z systemu zdalnego na komputer lokalny. |

## <a name="input"></a>Dane wejściowe

| Właściwość | Opis | Choices |
|--|--|--|
| Ignoruj określone biblioteki domyślne | Określa jedną lub więcej nazw bibliotek domyślnych do zignorowania. (--exclude-libs lib,lib) |
| Ignoruj biblioteki domyślne | Ignoruj biblioteki domyślne i jawnie określono tylko biblioteki wyszukiwania. |
| Wymuszanie niezdefiniowanych odwołań do symboli | Wymuś wprowadzenie symbolu w pliku wyjściowym jako symbolu niezdefiniowanego. (-u symbol --undefined=symbol) |
| Zależności biblioteki | Ta opcja umożliwia określenie dodatkowych bibliotek, które mają zostać dodane do wiersza polecenia konsolidatora. Dodatkowa biblioteka zostanie dodana na końcu wiersza polecenia konsolidatora poprzedzony 'lib' i zakończy się rozszerzeniem '.a'.  (-lFILE) |
| Dodatkowe zależności | Określa dodatkowe elementy, które mają być dodane do wiersza polecenia łącza. |

## <a name="debugging"></a>Debugowanie

| Właściwość | Opis | Choices |
|--|--|--|
| Informacje o symbolu debugera | Informacje o symbolu debugera z pliku wyjściowego. | **Uwzględnij wszystkie**<br>**Pomijanie tylko informacji o symbolu debugera**<br>**Pomiń wszystkie informacje o symbolu**<br> |
| Nazwa pliku mapy | Opcja Mapa informuje konsolidatora o utworzeniu pliku mapy o określonej nazwie użytkownika. (-Mapa=) |

## <a name="advanced"></a>Zaawansowane

| Właściwość | Opis | Choices |
|--|--|--|
| Oznacz zmienne odczytywane tylko po relokacji | Ta opcja oznacza zmienne tylko do odczytu po przeniesieniu. |
| Włącz bezpośrednie powiązanie funkcji | Ta opcja oznacza obiekt do natychmiastowego wiązania funkcji. |
| Nie wymagaj stosu wykonywalnego | Ta opcja oznacza dane wyjściowe jako nie wymagające stosu wykonywalnego. |
| Całe archiwum | Całe archiwum używa całego kodu ze źródeł i dodatkowych zależności. |

::: moniker-end
