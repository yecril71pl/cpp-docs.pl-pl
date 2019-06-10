---
title: Właściwości języka C/C++ (Linux C++)
ms.date: 06/07/2019
ms.assetid: 4bb8894b-c874-4a68-935e-b127d54e484f
f1_keywords: []
ms.openlocfilehash: b5be7582970c45e25f1e2c90971d587c19eac2a0
ms.sourcegitcommit: 8adabe177d557c74566c13145196c11cef5d10d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2019
ms.locfileid: "66821335"
---
# <a name="cc-properties-linux-c"></a>Właściwości języka C/C++ (Linux C++)

::: moniker range="vs-2015"

Pomoc techniczna Linux support jest dostępne w programie Visual Studio 2017 i nowszych wersjach.

::: moniker-end

::: moniker range=">=vs-2017"

## <a name="general"></a>Ogólne

Właściwość | Opis | Opcje
--- | ---| ---
Dodatkowe katalogi dyrektywy Include | Określa jeden lub więcej katalogów do dodania do ścieżki dołączania. Użyj średników do oddzielania wielu katalogów. (-I\[ścieżka]).
Format informacji o debugowaniu | Określa typ informacji o debugowaniu generowanych przez kompilator. | **Brak** — tworzy żadnych informacji debugowania, więc kompilacja może przebiegać szybciej.<br/>**Minimalne informacje debugowania** — Generuj informacje debugowania minimalny.<br/>**Pełne informacje debugowania (DWARF2)** — Generowanie debugowania dwarf2.<br/>
Nazwa pliku obiektu | Określa nazwę do zastąpienia domyślnej nazwy pliku obiektu. Może być nazwa pliku lub katalogu. (-o [nazwa]).
Poziom ostrzeżeń | Wybiera się, jak chcesz, aby kompilator o błędów kodu.  Dodaj inne flagi bezpośrednio do **dodatkowe opcje**. (/ w, / weverything). | **Włącz Wyłącz wszystkie ostrzeżenia** — wyłącza wszystkie ostrzeżenia kompilatora.<br/>**EnableAllWarnings** -włącza wszystkie ostrzeżenia, w tym te domyślnie wyłączone.<br/>
Traktuj ostrzeżenia jako błędy | Traktuje wszystkie ostrzeżenia kompilatora jako błędy. Dla nowego projektu może być najlepiej użyć werror we wszystkich kompilacjach. Rozwiąż wszystkie ostrzeżenia, aby upewnić się, jak najmniejsza liczba usterek możliwe kodu twardych do znalezienia.
Dodatkowe ostrzeżenia języka C | Definiuje zestaw dodatkowych komunikatów ostrzegawczych.
Dodatkowe ostrzeżenia języka C++ | Definiuje zestaw dodatkowych komunikatów ostrzegawczych.
Włącz tryb informacji pełnej | Po włączeniu trybu informacji pełnej do drukowania informacji do diagnozowania kompilacji.
C Compiler | Określa program do wywołania podczas kompilacji źródłowych plików języka C lub ścieżkę do kompilatora języka C w systemie zdalnym.
Kompilator C++ | Określa program do wywołania podczas kompilacji pliki źródłowe C++ lub ścieżkę do kompilatora języka C++ w systemie zdalnym.
Limit czasu kompilacji | Limit czasu zdalnej kompilacji, w milisekundach.
Kopiuj pliki obiektów | Określa, czy kopiować pliki skompilowanych obiektów z systemu zdalnego na maszynę lokalną.

## <a name="optimization"></a>optymalizacja

Właściwość | Opis | Opcje
--- | ---| ---
optymalizacja | Określa poziom optymalizacji aplikacji. | **Niestandardowe** — niestandardowa Optymalizacja.<br/>**Wyłączone** -Wyłącz optymalizację.<br/>**Minimalizuj rozmiar** — Optymalizuj pod kątem rozmiaru.<br/>**Maksymalizuj szybkość** — Optymalizuj pod kątem szybkości.<br/>**Pełna optymalizacja** — kosztowne optymalizacje.
Aliasowanie z ograniczeniami | Zakłada najbardziej rygorystyczne reguły aliasowania.  Obiekt danego typu nigdy nie zakłada się, że mają ten sam adres co obiekt innego typu.
Odwiń pętle | Unrolls pętli, aby szybciej aplikacje dzięki zmniejszeniu liczby wykonywanych na rzecz większego rozmiaru kodu gałęzi.
Optymalizacja czasu łączenia | Włącza optymalizacje między procedurami, umożliwiając optymalizatorowi przeglądanie plików obiektów w aplikacji.
Pominięcie wskaźnika ramki | Pomija tworzenie wskaźników ramek na stosie wywołań.
Brak bloków niestandardowych | Przydziela nawet niezainicjowane zmienne globalne w sekcji danych pliku obiektu, zamiast generować je jako bloki.

## <a name="preprocessor"></a>Preprocesor

Właściwość | Opis | Opcje
--- | ---| ---
Definicje preprocesora | Definiuje symbole przetwarzania wstępnego dla pliku źródłowego. (-D)
Usuń definicje preprocesora | Określa, że jedno anulowanie definicji preprocesora jeden lub więcej.  (-U \[macro])
Usuń wszystkie definicje preprocesora | Definicji do usunięcia wszystkich zdefiniowanych wcześniej wartości preprocesora.  (-undef)
Pokaż zawierania | Generuje listę załączonych plików z danych wyjściowych kompilatora.  (-H)

## <a name="code-generation"></a>Generowanie kodu

Właściwość | Opis | Opcje
--- | ---| ---
Kod niezależny od położenia | Generuje kod niezależny od położenia (PIC) do użycia w bibliotece udostępnionej.
Dane statyczne są wątkowo bezpieczne | Emituje dodatkowego kodu w celu użycia procedur określonych w C++ ABI dla wątkowo inicjowanie lokalnych danych statycznych. | **Nie** -Wyłącz wątkowo bezpieczne elementy statyczne.<br/>**Tak** -Włącz wątkowo bezpieczne elementy statyczne.
Optymalizacja liczb zmiennoprzecinkowych | Umożliwia optymalizacji zmiennopozycyjnych dzięki złagodzeniu wymagań zgodności IEEE 754.
Ukryte metody wbudowane | Po włączeniu końca wiersza kopii metod wbudowanych są deklarowane `private extern`.
Symbole ukryte domyślnie | Wszystkie symbole są deklarowane jako `private extern` , chyba że jawnie oznaczone eksportu `__attribute` makra.
Włącz wyjątki języka C++ | Określa model obsługi wyjątków, używane przez kompilator. | **Nie** -Wyłącz obsługę wyjątków.<br/>**Tak** -Włącz obsługę wyjątków.

## <a name="language"></a>Język

Właściwość | Opis | Opcje
--- | ---| ---
Włącz informacje typu Run-Time | Dodaje kod do sprawdzania typów obiektów C++ w czasie wykonywania (informacje o typie środowiska uruchomieniowego).     (frtti, fno-rtti)
Standard języka C | Określa standard języka C. | **Default**<br/>**C89** — Standard języka C89.<br/>**C99** — Standard języka C99.<br/>**C11** — Standard języka C11.<br/>**C99 (dialekt GNU)** — Standard języka programu C99 (dialekt GNU).<br/>**C11 (dialekt GNU)** — Standard języka programu C11 (dialekt GNU).
Standard języka C++ | Określa standard języka C++. | **Default**<br/>**C ++ 03** — Standard C ++ 03 języka.<br/>**C ++ 11** — Standard C ++ 11 język.<br/>**C ++ 14** — Standard C ++ 14 języka.<br/>**C ++ 03 (dialekt GNU)** — C ++ 03 (dialekt GNU) języka Standard.<br/>**C ++ 11 (dialekt GNU)** — C ++ 11 (dialekt GNU) języka Standard.<br/>**C ++ 14 (dialekt GNU)** — C ++ 14 (dialekt GNU) języka Standard.

## <a name="advanced"></a>Zaawansowane

Właściwość | Opis | Opcje
--- | ---| ---
Kompiluj jako | Wybiera opcję języka kompilowania dla plików .c i .cpp. (-x c, -x c++) | **Domyślne** — wykrywanie na podstawie rozszerzenia c lub CPP rozszerzenia.<br/>**Kompiluj jako kod C** — Kompiluj jako kod C.<br/>**Kompiluj jako C++ kodu** — Kompiluj jako C++ kodu.
Wymuszone pliki dołączane | Określa co najmniej jeden wymuszony plik dyrektywy pliki dołączane (— obejmują \[nazwa])

::: moniker-end
