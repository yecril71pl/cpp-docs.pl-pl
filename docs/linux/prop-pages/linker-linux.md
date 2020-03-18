---
title: Właściwości konsolidatora ( C++Linux)
ms.date: 06/07/2019
ms.assetid: a0243a94-8164-425b-b2fe-b84ff363d546
ms.openlocfilehash: 934e639199d663cba391c9913b067f32e5e32165
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441286"
---
# <a name="linker-properties-linux-c"></a>Właściwości konsolidatora ( C++Linux)

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="general"></a>Ogólne

| Właściwość | Opis | Decyzji |
|--|--|--|
| Plik wyjściowy | Opcja zastępuje domyślną nazwę i lokalizację programu tworzonego przez konsolidatora. (-o) |
| Pokaż postęp | Drukuje wiadomości dotyczące postępu konsolidatora. |
| Wersja | Opcja-Version nakazuje konsolidatorowi umieszczenie numeru wersji w nagłówku pliku wykonywalnego. |
| Włącz pełne dane wyjściowe | Opcja-verbose nakazuje konsolidatorowi wyprowadzanie pełnych komunikatów na potrzeby debugowania. |
| Ślad | Opcja--Trace informuje konsolidator, aby wyprowadził pliki wejściowe w miarę ich przetwarzania. |
| Symbole śledzenia | Wydrukuj listę plików, w których pojawia się symbol. (--Trace-symbol = symbol) |
| Drukuj mapę | Opcja--Print-map informuje konsolidator, aby wyprowadził mapę linków. |
| Zgłoś nierozpoznane odwołania do symboli | Ta opcja po włączeniu spowoduje zgłoszenie nierozpoznanych odwołań do symboli. |
| Optymalizuj pod kątem użycia pamięci | Optymalizuj pod kątem użycia pamięci przez odczytanie tabel symboli stosownie do potrzeb. |
| Ścieżka wyszukiwania biblioteki udostępnionej | Zezwala użytkownikowi na wypełnienie ścieżki wyszukiwania biblioteki udostępnionej. (-rpath-link = Path) |
| Dodatkowe katalogi biblioteki | Zezwala użytkownikowi na przesłanianie ścieżki biblioteki środowiskowej. (-L folder). |
| Konsolidator | Określa program do wywołania podczas łączenia lub ścieżkę do konsolidatora w systemie zdalnym. |
| Limit czasu łącza | Limit czasu łączenia zdalnego (w milisekundach). |
| Kopiuj dane wyjściowe | Określa, czy plik danych wyjściowych kompilacji ma być kopiowany z systemu zdalnego na maszynę lokalną. |

## <a name="input"></a>Dane wejściowe

| Właściwość | Opis | Decyzji |
|--|--|--|
| Ignoruj określone biblioteki domyślne | Określa co najmniej jedną nazwę bibliotek domyślnych do zignorowania. (--Exclude-libs lib, lib) |
| Ignoruj biblioteki domyślne | Ignoruj biblioteki domyślne i jawnie określone biblioteki wyszukiwania. |
| Wymuszaj odwołania do niezdefiniowanych symboli | Wymuś wprowadzenie symbolu w pliku wyjściowym jako niezdefiniowanego symbolu. (-u symbol--undefined = symbol) |
| Zależności biblioteki | Ta opcja umożliwia określenie dodatkowych bibliotek, które mają zostać dodane do wiersza polecenia konsolidatora. Dodatkowa biblioteka zostanie dodana na końcu wiersza polecenia konsolidatora z prefiksem "lib" i rozszerzeniem ". a".  (-lFILE) |
| {1&gt;Dodatkowe zależności&lt;1} | Określa dodatkowe elementy do dodania do wiersza polecenia konsolidacji. |

## <a name="debugging"></a>Debugowanie

| Właściwość | Opis | Decyzji |
|--|--|--|
| Informacje o symbolach debugera | Informacje o symbolach debugera z pliku wyjściowego. | **Uwzględnij wszystko**<br>**Pomiń tylko informacje o symbolach debugera**<br>**Pomiń wszystkie informacje o symbolach**<br> |
| Nazwa pliku mapy | Opcja map nakazuje konsolidatorowi utworzenie pliku mapy o nazwie określonej przez użytkownika. (-Map =) |

## <a name="advanced"></a>Zaawansowane

| Właściwość | Opis | Decyzji |
|--|--|--|
| Oznacz zmienne jako tylko do odczytu po relokacji | Ta opcja oznacza zmienne jako tylko do odczytu po relokacji. |
| Włącz natychmiastowe powiązanie funkcji | Ta opcja oznacza obiekt do natychmiastowego powiązania funkcji. |
| Nie wymagaj stosu wykonywalnego | Ta opcja oznacza dane wyjściowe jako niewymagające stosu wykonywalnego. |
| Całe archiwum | Całe archiwum używa całego kodu ze źródeł i dodatkowych zależności. |

::: moniker-end
