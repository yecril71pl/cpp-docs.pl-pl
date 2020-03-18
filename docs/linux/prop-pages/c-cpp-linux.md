---
title: C/C++ właściwości (Linux C++)
ms.date: 06/07/2019
ms.assetid: 4bb8894b-c874-4a68-935e-b127d54e484f
f1_keywords: []
ms.openlocfilehash: 394cb501b4df6caed6a358ffa96ce0de5d187ae1
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/17/2020
ms.locfileid: "79441474"
---
# <a name="cc-properties-linux-c"></a>C/C++ właściwości (Linux C++)

::: moniker range="vs-2015"

Obsługa systemu Linux jest dostępna w programie Visual Studio 2017 i nowszych.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="general"></a>Ogólne

| Właściwość | Opis | Decyzji |
|--|--|--|
| Dodatkowe katalogi dołączane | Określa co najmniej jeden katalog do dodania do ścieżki dołączania. Użyj średników do rozdzielenia wielu katalogów. (-I\[ścieżka]). |
| Format informacji o debugowaniu | Określa typ informacji o debugowaniu generowanych przez kompilator. | **Brak** — nie tworzy informacji o debugowaniu, dzięki czemu kompilacja może być szybsza.<br/>**Minimalne informacje debugowania** — generowanie minimalnych informacji o debugowaniu.<br/>**Pełne informacje o debugowaniu (DWARF2)** — generują informacje debugowania DWARF2.<br/> |
| Nazwa pliku obiektu | Określa nazwę do przesłaniania domyślnej nazwy pliku obiektu. Może to być nazwa pliku lub katalogu. (-o [nazwa]). |
| Poziom ostrzeżeń | Wybiera, jak ścisłość kompilator ma mieć wpływ na błędy kodu.  Dodaj inne flagi bezpośrednio do **dodatkowych opcji**. (/w,/Weverything). | Wyłącz **wszystkie ostrzeżenia** — wyłącza wszystkie ostrzeżenia kompilatora.<br/>**Włącz wszystkie ostrzeżenia** — włącza wszystkie ostrzeżenia, w tym wyłączone domyślnie.<br/> |
| Traktuj ostrzeżenia jako błędy | Traktuje wszystkie ostrzeżenia kompilatora jako błędy. W przypadku nowego projektu najlepiej jest używać/Werror we wszystkich kompilacjach. Usuń wszystkie ostrzeżenia, aby upewnić się, że wady kodu są trudne do znalezienia. |
| Dodatkowe ostrzeżenia dotyczące języka C | Definiuje zestaw dodatkowych komunikatów ostrzegawczych. |
| C++Dodatkowe ostrzeżenia | Definiuje zestaw dodatkowych komunikatów ostrzegawczych. |
| Włącz tryb pełny | Gdy tryb informacji pełnej jest włączony, program drukuje więcej informacji umożliwiających zdiagnozowanie kompilacji. |
| Kompilator języka C | Określa program do wywołania podczas kompilacji źródłowych plików języka C lub ścieżkę do kompilatora języka C w systemie zdalnym. |
| Kompilator C++ | Określa program do wywołania podczas kompilacji plików C++ źródłowych lub ścieżkę do C++ kompilatora w systemie zdalnym. |
| Limit czasu kompilacji | Limit czasu kompilacji zdalnej (w milisekundach). |
| Kopiuj pliki obiektów | Określa, czy mają być kopiowane skompilowane pliki obiektów z systemu zdalnego na maszynę lokalną. |

## <a name="optimization"></a>Optymalizacja

| Właściwość | Opis | Decyzji |
|--|--|--|
| Optymalizacja | Określa poziom optymalizacji aplikacji. | Optymalizacja **niestandardowa** .<br/>**Wyłączone** — wyłączenie optymalizacji.<br/>**Minimalizuj rozmiar** — Optymalizuj pod kątem rozmiaru.<br/>**Maksymalizuj szybkość** — Optymalizuj szybkość.<br/>**Pełna optymalizacja** — kosztowna Optymalizacja. |
| Jednostrictne aliasowanie | Przyjmuje zasady najdokładniejszych aliasów.  Obiekt jednego typu nigdy nie przyjmuje się, że ma taki sam adres jak obiekt innego typu. |
| Odwrócenie pętli | Wycofuje pętle, aby przyspieszyć działanie aplikacji dzięki zmniejszeniu liczby wykonywanych gałęzi przy użyciu kosztu większego rozmiaru kodu. |
| Optymalizacja czasu konsolidacji | Włącza optymalizacje między procedurami, umożliwiając Optymalizatorowi przeglądanie plików obiektów w aplikacji. |
| Pomiń wskaźnik ramki | Pomija tworzenie wskaźników ramek na stosie wywołań. |
| Brak wspólnych bloków | Przydziela nawet Niezainicjowane zmienne globalne w sekcji danych pliku obiektu, zamiast generować je jako bloki wspólne. |

## <a name="preprocessor"></a>Preprocesor

| Właściwość | Opis | Decyzji |
|--|--|--|
| Definicje preprocesora | Definiuje symbole przetwarzania wstępnego dla pliku źródłowego. (-D) |
| Usuń Definicje preprocesora | Określa co najmniej jedną definicję preprocesora.  (-U \[makro]) |
| Usuń wszystkie Definicje preprocesora | Definiuje wszystkie zdefiniowane wcześniej wartości preprocesora.  (-undef) |
| Pokaż zawiera | Generuje listę plików dołączanych z danymi wyjściowymi kompilatora.  (-H) |

## <a name="code-generation"></a>Generowanie kodu

| Właściwość | Opis | Decyzji |
|--|--|--|
| Umieść kod niezależny | Generuje kod niezależny od pozycji (PIC) do użycia w bibliotece udostępnionej. |
| Elementy statyczne są wątkowo bezpieczne | Emituje dodatkowy kod, aby użyć procedur określonych w C++ ABI na potrzeby inicjowania bezpiecznego wątku lokalnych elementów statycznych. | **Nie** — Wyłącz statycznie bezpieczne dla wątków.<br/>**Tak** — Włącz statycznie bezpieczne wątki. |
| Optymalizacja liczb zmiennoprzecinkowych | Włącza optymalizacje zmiennoprzecinkowe przez złagodzeniu wymagań dotyczących zgodności IEEE-754. |
| Ukryte metody wbudowane | Gdy ta funkcja jest włączona, nieaktualne kopie metod wbudowanych są deklarowane `private extern`. |
| Symbole są domyślnie ukryte | Wszystkie symbole są deklarowane `private extern`, chyba że zostaną jawnie oznaczone do eksportu przy użyciu makra `__attribute`. |
| Włącz C++ wyjątki | Określa model obsługi wyjątków używany przez kompilator. | **Nie** -Wyłącz obsługę wyjątków.<br/>**Tak** — Włącz obsługę wyjątków. |

## <a name="language"></a>Język

| Właściwość | Opis | Decyzji |
|--|--|--|
| Włącz informacje o typie w czasie wykonywania | Dodaje kod do sprawdzania C++ typów obiektów w czasie wykonywania (informacje o typie środowiska uruchomieniowego).     (frtti, FNO-RTTI) |
| Standard języka C | Określa standard języka C. | **Domyślne**<br/>Standard języka **C89** -c89.<br/>Standard języka **C99** -C99.<br/>Standard języka **C11** -C11.<br/>Standard języka **C99 (DIALEKT GNU)** — C99 (dialekt GNU).<br/>Standard języka **C11 (DIALEKT GNU)** — C11 (dialekt GNU). |
| C++Standard języka | Określa standard C++ języka. | **Domyślne**<br/>Standard języka **C++ 03** -c++ 03.<br/>Standard języka **C++ 11** — c++ 11.<br/>Standard języka **C++ 14** -c++ 14.<br/>**C++ 03 (DIALEKT GNU)** — Standard języka c++ 03 (dialekt GNU).<br/>**C++ 11 (DIALEKT GNU)** — Standard języka c++ 11 (dialekt GNU).<br/>**C++ 14 (DIALEKT GNU)** — Standard języka c++ 14 (dialekt GNU). |

## <a name="advanced"></a>Zaawansowane

| Właściwość | Opis | Decyzji |
|--|--|--|
| Kompiluj jako | Wybiera opcję języka kompilacji dla plików. c i. cpp. (-x c, -x c++) | **Domyślne** — wykrywanie na podstawie rozszerzenia. c lub. cpp.<br/>**Kompiluj jako kod c** Kompiluj jako kod c.<br/>**Kompiluj jako C++**  kod Kompiluj jako C++ kod. |
| Wymuszone pliki dołączane | Określa co najmniej jeden wymuszony plik dyrektywy include (-include \[Name]) |

::: moniker-end
