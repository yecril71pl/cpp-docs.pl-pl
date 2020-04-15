---
title: Właściwości C/C++ (Linux C++)
ms.date: 06/07/2019
ms.assetid: 4bb8894b-c874-4a68-935e-b127d54e484f
f1_keywords: []
ms.openlocfilehash: 394cb501b4df6caed6a358ffa96ce0de5d187ae1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "79441474"
---
# <a name="cc-properties-linux-c"></a>Właściwości C/C++ (Linux C++)

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="general"></a>Ogólne

| Właściwość | Opis | Choices |
|--|--|--|
| Dodatkowe katalogi dołączania | Określa jeden lub więcej katalogów do dodania do ścieżki dołączania. Użyj średników, aby oddzielić wiele katalogów. (-I\[ścieżka]). |
| Format informacji debugowania | Określa typ informacji debugowania generowanych przez kompilator. | **Brak** — nie generuje żadnych informacji debugowania, więc kompilacja może być szybsza.<br/>**Minimalne informacje debugowania** — generowanie minimalnych informacji debugowania.<br/>**Pełne informacje debugowania (DWARF2)** — generowanie informacji debugowania DWARF2.<br/> |
| Nazwa pliku obiektu | Określa nazwę, która ma zastąpić domyślną nazwę pliku obiektu. Może to być nazwa pliku lub katalogu. (-o [nazwa]). |
| Poziom ostrzeżenia | Wybiera, jak ścisłe, że kompilator ma być o błędach kodu.  Dodaj inne flagi bezpośrednio do **opcji dodatkowych**. (/w, /Weverything). | **Wyłącz wszystkie ostrzeżenia** — wyłącza wszystkie ostrzeżenia kompilatora.<br/>**EnableAllWarnings** — domyślnie włącza wszystkie ostrzeżenia, w tym ostrzeżenia wyłączone.<br/> |
| Potraktuj ostrzeżenia jako błędy | Traktuje wszystkie ostrzeżenia kompilatora jako błędy. Dla nowego projektu może być najlepiej użyć /Werror we wszystkich kompilacjach. Rozwiąż wszystkie ostrzeżenia, aby zapewnić jak najmniejszą dziewienie się wad kodu. |
| C Dodatkowe ostrzeżenia | Definiuje zestaw dodatkowych komunikatów ostrzegawczych. |
| Dodatkowe ostrzeżenia języka C++ | Definiuje zestaw dodatkowych komunikatów ostrzegawczych. |
| Włącz tryb pełny | Gdy tryb pełne jest włączony, drukuje więcej informacji, aby zdiagnozować kompilacji. |
| Kompilator C | Określa program do wywołania podczas kompilacji plików źródłowych C lub ścieżkę do kompilatora C w systemie zdalnym. |
| Kompilator C++ | Określa program do wywołania podczas kompilacji plików źródłowych języka C++ lub ścieżkę do kompilatora C++ w systemie zdalnym. |
| Limit czasu kompilacji | Limit czasu kompilacji zdalnej w milisekundach. |
| Kopiowanie plików obiektów | Określa, czy skompilowane pliki obiektów mają być kopiowane z systemu zdalnego na komputer lokalny. |

## <a name="optimization"></a>Optymalizacja

| Właściwość | Opis | Choices |
|--|--|--|
| Optymalizacja | Określa poziom optymalizacji dla aplikacji. | **Niestandardowe** — optymalizacja niestandardowa.<br/>**Wyłączone** — wyłącz optymalizację.<br/>**Minimalizuj rozmiar** — optymalizuj pod kątem rozmiaru.<br/>**Maksymalizuj prędkość** - Optymalizuj prędkość.<br/>**Pełna optymalizacja** - kosztowne optymalizacje. |
| Ścisła aliasing | Przyjęto najsurowsze reguły aliasowania.  Obiekt jednego typu nigdy nie zakłada się, że ma ten sam adres jako obiekt innego typu. |
| Rozpiąć pętle | Rozwiń pętle, aby aplikacja szybciej przez zmniejszenie liczby oddziałów wykonywanych, kosztem większego rozmiaru kodu. |
| Optymalizacja czasu łącza | Umożliwia optymalizacje między proceduralne, umożliwiając optymalizatorowi przeglądanie plików obiektów w aplikacji. |
| Wskaźnik pominiętej ramki | Pomija tworzenie wskaźników ramek na stosie wywołań. |
| Brak wspólnych bloków | Przydziela nawet niezainicjowane zmienne globalne w sekcji danych pliku obiektu, zamiast generować je jako wspólne bloki. |

## <a name="preprocessor"></a>Preprocesor

| Właściwość | Opis | Choices |
|--|--|--|
| Definicje preprocesora | Definiuje symbole przetwarzania wstępnego dla pliku źródłowego. (-D) |
| Definicje przederocesora przeddefine | Określa co najmniej jedną niedrobnie wolną od przetwarzania preprocesora.  (-U \[makro]) |
| Undefine Wszystkie definicje preprocesora | Undefines wszystkie uprzednio zdefiniowane wartości preprocesora.  (-undef) |
| Pokaż zawiera | Generuje listę plików dołączanych z wyjściem kompilatora.  (-H) |

## <a name="code-generation"></a>Generowanie kodu

| Właściwość | Opis | Choices |
|--|--|--|
| Niezależny kod pozycji | Generuje kod niezależny od pozycji (PIC) do użycia w bibliotece udostępnionej. |
| Statyki są bezpieczne dla gwintów | Emituje dodatkowy kod do korzystania z procedur określonych w C++ ABI dla inicjowania lokalnych statycznych bezpiecznych wątków. | **Nie** - Wyłącz statyczne bezpieczne dla wątków.<br/>**Tak** - Włącz statyczne bezpieczne dla wątków. |
| Optymalizacja zmiennoprzecinkowa | Umożliwia optymalizację zmiennoprzecinkową, rozluźniając zgodność z IEEE-754. |
| Ukryte metody wbudowane | Gdy ta opcja jest włączona, są deklarowane `private extern`nieliniowe kopie metod wbudowanych . |
| Symbole domyślnie ukryte | Wszystkie symbole `private extern` są zadeklarowane, chyba że `__attribute` jawnie oznaczone do eksportu przy użyciu makra. |
| Włącz wyjątki języka C++ | Określa model obsługi wyjątków używany przez kompilator. | **Nie** - Wyłącz obsługę wyjątków.<br/>**Tak** — włącz obsługę wyjątków. |

## <a name="language"></a>Język

| Właściwość | Opis | Choices |
|--|--|--|
| Włącz informacje o typie czasu wykonywania | Dodaje kod do sprawdzania typów obiektów języka C++ w czasie wykonywania (informacje o typie środowiska wykonawczego).     (frtti, fno-rtti) |
| C Standard językowy | Określa standard języka C. | **Domyślny**<br/>**C89** - C89 Standard językowy.<br/>**C99** - C99 Standard językowy.<br/>**C11** - C11 Standard językowy.<br/>**C99 (GNU Dialekt)** - C99 (GNU Dialekt) Language Standard.<br/>**C11 (GNU Dialekt)** - C11 (GNU Dialekt) Language Standard. |
| Standard językowy języka C++ | Określa standard języka C++. | **Domyślny**<br/>**C++03** - C++03 Standard językowy.<br/>**C++11** - Standard językowy C++11.<br/>**C++14** - Standard językowy C++14.<br/>**C++03 (GNU Dialekt)** - C++03 (GNU Dialekt) Standard językowy.<br/>**C++11 (GNU Dialekt)** - C++11 (GNU Dialekt) Standard językowy.<br/>**C++14 (GNU Dialekt)** - C++14 (GNU Dialekt) Standard językowy. |

## <a name="advanced"></a>Zaawansowane

| Właściwość | Opis | Choices |
|--|--|--|
| Skompiluj jako | Wybiera opcję języka kompilacji dla plików .c i .cpp. (-x c, -x c++) | **Domyślnie** — wykrywanie na podstawie rozszerzenia .c lub .cpp.<br/>**Skompiluj jako kod C** - skompiluj jako kod C.<br/>**Skompiluj jako kod C++** — skompiluj jako kod C++. |
| Wymuszone pliki dołączania | Określa jeden lub więcej wymuszonych \[plików dołączania (-nazwa dołączania]) |

::: moniker-end
