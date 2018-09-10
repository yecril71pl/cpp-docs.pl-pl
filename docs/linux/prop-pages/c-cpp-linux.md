---
title: Właściwości języka C/C++ (Linux C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 9/26/2017
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: Linux
ms.topic: conceptual
ms.assetid: 4bb8894b-c874-4a68-935e-b127d54e484f
author: mikeblome
ms.author: mblome
f1_keywords: []
ms.workload:
- cplusplus
- linux
ms.openlocfilehash: 7ab78284929de8e5991abb0d1a8c89ead500096a
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44314706"
---
# <a name="cc-properties-linux-c"></a>Właściwości języka C/C++ (Linux C++)

## <a name="general"></a>Ogólne

Właściwość | Opis | Opcje
--- | ---| ---
Dodatkowe katalogi dyrektywy Include | Określa jeden lub więcej katalogów do dodania do ścieżki dołączenia; Oddziel przy użyciu średnikami, jeśli istnieje więcej niż jedna. (-I[ścieżka]).
Format informacji o debugowaniu | Określa typ informacji o debugowaniu generowanych przez kompilator. | **Brak** — tworzy żadnych informacji debugowania, więc kompilacja może przebiegać szybciej.<br/>**Minimalne informacje debugowania** — Generuj informacje debugowania minimalny.<br/>**Pełne informacje debugowania (DWARF2)** — Generowanie debugowania dwarf2.<br/>
Nazwa pliku obiektu | Określa nazwę do zastąpienia domyślnej nazwy pliku obiektu; może być nazwą pliku lub katalogu. (-o [nazwa]).
Poziom ostrzeżeń | Wybierz jak ścisły kompilator o błędów kodu.  Inne flagi należy dodać bezpośrednio do dodatkowych opcji. (/ w, / weverything). | **Włącz Wyłącz wszystkie ostrzeżenia** — wyłącza wszystkie ostrzeżenia kompilatora.<br/>**EnableAllWarnings** -włącza wszystkie ostrzeżenia, w tym te domyślnie wyłączone.<br/>
Traktuj ostrzeżenia jako błędy | Traktuje wszystkie ostrzeżenia kompilatora jako błędy. Dla nowego projektu może być najlepiej użyć werror we wszystkich kompilacjach; rozwiązanie wszystkich ostrzeżeń zapewni najmniejszą liczbą wad możliwe kodu twardych do znalezienia.
Dodatkowe ostrzeżenia języka C | Definiuje zestaw dodatkowych komunikatów ostrzegawczych.
Dodatkowe ostrzeżenia języka C++ | Definiuje zestaw dodatkowych komunikatów ostrzegawczych.
Włącz tryb informacji pełnej | Po włączeniu trybu informacji pełnej, to narzędzie wypisuje więcej informacji dotyczących diagnozowania kompilacji.
Kompilator języka C | Określa program do wywołania podczas kompilacji źródłowych plików języka C lub ścieżkę do kompilatora języka C w systemie zdalnym.
Kompilator C++ | Określa program do wywołania podczas kompilacji pliki źródłowe C++ lub ścieżkę do kompilatora języka C++ w systemie zdalnym.
Limit czasu kompilacji | Limit czasu zdalnej kompilacji, w milisekundach.
Kopiuj pliki obiektów | Określa, czy kopiować pliki skompilowanych obiektów z systemu zdalnego na maszynę lokalną.

## <a name="optimization"></a>Optymalizacja

Właściwość | Opis | Opcje
--- | ---| ---
Optymalizacja | Określa poziom optymalizacji aplikacji. | **Niestandardowe** — niestandardowa Optymalizacja.<br/>**Wyłączone** -Wyłącz optymalizację.<br/>**Minimalizuj rozmiar** — Optymalizuj pod kątem rozmiaru.<br/>**Maksymalizuj szybkość** — Optymalizuj pod kątem szybkości.<br/>**Pełna optymalizacja** — kosztowne optymalizacje.<br/>
Aliasowanie z ograniczeniami | Przyjęto założenie, najbardziej rygorystyczne reguły aliasowania.  Obiekt danego typu zostanie nigdy nie być zakłada się, że znajdują się na tym samym adresem co obiekt innego typu.
Odwiń pętle | Odwiń pętle, aby szybciej aplikacje dzięki zmniejszeniu liczby wykonywanych gałęzi na rzecz większego rozmiaru kodu.
Optymalizacja czasu łączenia | Włącz optymalizacje między procedurami, umożliwiając optymalizatorowi przeglądanie plików obiektów w aplikacji.
Pominięcie wskaźnika ramki | Pomija tworzenie wskaźników ramek na stosie wywołań.
Brak bloków niestandardowych | Przydziel nawet niezainicjowane zmienne globalne w sekcji danych pliku obiektu, zamiast generować je jako bloki

## <a name="preprocessor"></a>Preprocesor

Właściwość | Opis | Opcje
--- | ---| ---
Definicje preprocesora | Definiuje symbole przetwarzania wstępnego dla pliku źródłowego. (-D)
Usuń definicje preprocesora | Określa, że jedno anulowanie definicji preprocesora jeden lub więcej.  (-U [macro])
Usuń wszystkie definicje preprocesora | Usuń definicje wszystkich zdefiniowanych wcześniej wartości preprocesora.  (-undef)
Pokaż zawierania | Generuje listę załączonych plików z danych wyjściowych kompilatora.  (-H)

## <a name="code-generation"></a>Generowanie kodu

Właściwość | Opis | Opcje
--- | ---| ---
Kod niezależny od położenia | Generowanie niezależnie od kodu położenia (PIC) do użycia w bibliotece udostępnionej.
Dane statyczne są wątkowo bezpieczne | Emituj dodatkowy kod w celu użycia procedur określonych w interfejsie ABI języka C++ dla wątkowo bezpiecznego inicjowania lokalnych danych statycznych. | **Nie** -Wyłącz bezpieczne wątkowo.<br/>**Tak** -Włącz bezpieczne wątkowo.<br/>
Optymalizacja liczb zmiennoprzecinkowych | Włącza liczb zmiennoprzecinkowych optymalizacji punktu według złagodzeniu wymagań zgodności IEEE 754.
Ukryte metody wbudowane | Po włączeniu końca wiersza kopii metod wbudowanych są deklarowane "prywatne elementy zewnętrzne".
Symbole ukryte domyślnie | Wszystkie symbole są deklarowane jako "prywatne elementy zewnętrzne", chyba że jawnie oznaczone do wyeksportowania przy użyciu makra "__attribute".
Włącz wyjątki języka C++ | Określa model obsługi wyjątków, aby używane przez kompilator. | **Nie** -Wyłącz obsługę wyjątków.<br/>**Tak** -Włącz obsługę wyjątków.<br/>

## <a name="language"></a>Język

Właściwość | Opis | Opcje
--- | ---| ---
Włącz informacje typu Run-Time | Dodaje kod do sprawdzania typów obiektów C++ w czasie wykonywania (informacje o typie środowiska uruchomieniowego).     (frtti, fno-rtti)
Standard języka C | Określa standard języka C. | **Default**<br/>**C89** — Standard języka C89.<br/>**C99** — Standard języka C99.<br/>**C11** — Standard języka C11.<br/>**C99 (dialekt GNU)** — Standard języka programu C99 (dialekt GNU).<br/>**C11 (dialekt GNU)** — Standard języka programu C11 (dialekt GNU).<br/>
Standard języka C++ | Określa standard języka C++. | **Default**<br/>**C ++ 03** — Standard C ++ 03 języka.<br/>**C ++ 11** — Standard C ++ 11 język.<br/>**C ++ 14** — Standard C ++ 14 języka.<br/>**C ++ 03 (dialekt GNU)** — C ++ 03 (dialekt GNU) języka Standard.<br/>**C ++ 11 (dialekt GNU)** — C ++ 11 (dialekt GNU) języka Standard.<br/>**C ++ 14 (dialekt GNU)** — C ++ 14 (dialekt GNU) języka Standard.<br/>

## <a name="advanced"></a>Zaawansowane

Właściwość | Opis | Opcje
--- | ---| ---
Kompiluj jako | Wybierz opcję języka kompilowania dla plików .c i .cpp.  "Default" wykryje na podstawie rozszerzenia c lub CPP rozszerzenie. (-x c, - x c ++) | **Domyślne** — domyślne.<br/>**Kompiluj jako kod C** — Kompiluj jako kod C.<br/>**Kompiluj jako kod C++** — Kompiluj jako kod C++.<br/>
Wymuszone pliki dołączane | Co najmniej jeden wymuszony plik dyrektywy include plików (-include [nazwa])

## <a name="additional-options"></a>Dodatkowe opcje 
