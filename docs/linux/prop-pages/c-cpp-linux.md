---
title: Właściwości C/C++ (Linux C++) | Dokumentacja firmy Microsoft
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
ms.openlocfilehash: 1978c566dab949093f0ddbd2aa1aa37ad0942808
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33336193"
---
# <a name="cc-properties-linux-c"></a>Właściwości C/C++ (Linux C++)

## <a name="general"></a>Ogólne
Właściwość | Opis | Opcje
--- | ---| ---
Dodatkowe katalogi dołączenia | Określa jeden lub więcej katalogów do dodania do ścieżki dołączenia; Oddziel przy użyciu średnikami, jeśli istnieje więcej niż jedna. (-I[path]).
Format informacji debugowania | Określa typ informacji dotyczących debugowania generowanych przez kompilator. | **Brak** — tworzy żadnych informacji debugowania, więc kompilacji może przebiegać szybciej.<br>**Minimalne informacje debugowania** -Generuj informacje debugowania minimalny.<br>**Pełne informacje debugowania (DWARF2)** -informacje dotyczące debugowania DWARF2 generowania.<br>
Nazwa pliku obiektu | Określa nazwę do przesłaniania domyślnej nazwy pliku obiektu; może być nazwą pliku lub katalogu. (-o [nazwa]).
Poziom ostrzeżeń | Wybierz, jak ściśle kompilator o błędach kodu.  Inne flagi należy dodać bezpośrednio do dodatkowe opcje. (/ w, / weverything). | **Włącz Wyłącz wszystkie ostrzeżenia** — wyłącza wszystkie ostrzeżenia kompilatora.<br>**EnableAllWarnings** -włącza wszystkie ostrzeżenia, w tym te domyślnie wyłączone.<br>
Traktuj ostrzeżenia jako błędy | Traktuje wszystkie ostrzeżenia kompilatora jako błędy. Dla nowego projektu może być najlepiej użyć /Werror we wszystkich kompilacjach; rozwiązanie wszystkich ostrzeżeń zapewni najmniejszej defektów możliwe kodu twarde do znalezienia.
Dodatkowe ostrzeżenia C | Definiuje zestaw dodatkowych komunikatów ostrzegawczych.
Dodatkowe C++ — ostrzeżenia | Definiuje zestaw dodatkowych komunikatów ostrzegawczych.
Włącz tryb informacji pełnej | Po włączeniu trybu informacji pełnej, to narzędzie przetwarzającej więcej informacji, diagnozowanie kompilacji.
Kompilator języka C | Określa program do wywołania podczas kompilowania plików źródłowych C lub ścieżka do kompilatora C w systemie zdalnym.
Kompilator C++ | Określa program do wywołania podczas kompilowania pliki źródłowe C++ lub ścieżka do kompilatora języka C++ w systemie zdalnym.
Limit czasu kompilacji | Limit kompilacji zdalnej czasu w milisekundach.
Skopiuj pliki obiektów | Określa, czy do kopiowania plików skompilowanych obiektów z systemu zdalnego na komputerze lokalnym.

## <a name="optimization"></a>Optymalizacja
Właściwość | Opis | Opcje
--- | ---| ---
Optymalizacja | Określa poziom optymalizacji dla aplikacji. | **Niestandardowe** -optymalizacji niestandardowe.<br>**Wyłączone** -wyłączenie optymalizacji.<br>**Minimalizuj rozmiar** -Optymalizuj dla rozmiaru.<br>**Maksymalizuj szybkość** -Optymalizacja szybkości.<br>**Pełna optymalizacja** -optymalizacje kosztowne.<br>
Ścisłego aliasów | Przykładowa najbardziej rygorystyczne reguły aliasowania.  Obiekt danego typu zostanie nigdy nie zakłada się, że znajdują się na tym samym adresem co obiekt innego typu.
Skorzystaj z odwijania pętli | Skorzystaj z odwijania pętli, aby przyspieszyć działanie aplikacji dzięki zmniejszeniu liczby wykonywanych gałęzi na rzecz większego rozmiaru kodu.
Optymalizacja czasu łącza | Włącz optymalizacje między procedurami, umożliwiając optymalizatorowi przeglądanie plików obiektów w aplikacji.
Pominięcie wskaźnika ramki | Pomija tworzenie wskaźników ramek na stosie wywołań.
Nie wspólnego bloków | Przydziel nawet niezainicjowane zmienne globalne w sekcji danych pliku obiektu zamiast generować je jako wspólne bloki

## <a name="preprocessor"></a>Preprocesor
Właściwość | Opis | Opcje
--- | ---| ---
Definicje preprocesora | Definiuje symbole przetwarzania wstępnego dla pliku źródłowego. (-D)
Usuń definicje preprocesora | Określa, że co najmniej jeden anulowanie definicji preprocesora.  (-U [macro])
Usuń definicje wszystkich Preprocesorów | Usuń definicje wszystkich zdefiniowanych wcześniej wartości preprocesora.  (-undef)
Pokaż obejmuje | Generuje listę załączonych plików z danych wyjściowych kompilatora.  (-H)

## <a name="code-generation"></a>Generowanie kodu
Właściwość | Opis | Opcje
--- | ---| ---
Kod niezależny | Generowanie pozycji niezależne kodu (PIC) do użycia w bibliotece udostępnionej.
Dane statyczne są wątkowo bezpieczne | Emituj dodatkowy kod w celu użycia procedur określonych w interfejsie ABI języka C++ dla bezpiecznego inicjowania lokalnych danych statycznych w wątkach. | **Nie** — Wyłącz statystykach awaryjny wątku.<br>**Tak** -Włącz statystykach awaryjny wątku.<br>
Liczby zmiennoprzecinkowe punktu optymalizacji | Liczby zmiennoprzecinkowe włącza punktu optymalizacje przez złagodzeniu zgodności IEEE-754.
Wbudowane metody ukryte | Po włączeniu-wiersza kopie metod wbudowanych są deklarowane jako "prywatne elementy zewnętrzne".
Symbole ukryte domyślnie | Wszystkie symbole są deklarowane jako "prywatne elementy zewnętrzne", chyba że jawnie oznaczone do wyeksportowania przy użyciu makra "__attribute".
Włącz wyjątki C++ | Określa model obsługi wyjątków, aby używane przez kompilator. | **Nie** -wyłączenie obsługi wyjątków.<br>**Tak** — Włączanie obsługi wyjątków.<br>

## <a name="language"></a>Język
Właściwość | Opis | Opcje
--- | ---| ---
Włącz informacje typu Run-Time | Dodaje kod do sprawdzania typów obiektów C++ w czasie wykonywania (informacje o typie środowiska uruchomieniowego).     (frtti, fno-rtti)
Standard języka C | Określa standard języka C. | **Default**<br>**C89** -C89 Standard języka.<br>**C99** -C99 Standard języka.<br>**C11** -C11 Standard języka.<br>**C99 (GNU dialekt)** — Standard języka C99 (GNU dialekt).<br>**C11 (GNU dialekt)** — Standard języka C11 (GNU dialekt).<br>
Standard języka C++ | Określa standard języka C++. | **Default**<br>**C ++ 03** — Standard 03 języka C ++.<br>**C ++ 11** -C ++ 11 języka Standard.<br>**C ++ 14** -C ++ 14 języka Standard.<br>**03 c ++ (GNU dialekt)** C ++ - 03 Standard języka (GNU dialekt).<br>**C ++ 11 (GNU dialekt)** - C ++ 11 Standard języka (GNU dialekt).<br>**C ++ 14 (GNU dialekt)** - C ++ 14 Standard języka (GNU dialekt).<br>

## <a name="advanced"></a>Zaawansowane
Właściwość | Opis | Opcje
--- | ---| ---
Skompiluj jako | Wybierz opcję języka kompilowania dla plików .c i .cpp.  "Default" wykryje na podstawie rozszerzenia c lub CPP rozszerzenie. (-x c, - x c ++) | **Domyślna** — domyślna.<br>**Skompiluj jako kod języka C** -skompiluj jako kod języka C.<br>**Skompiluj jako kod języka C++** -skompiluj jako kod języka C++.<br>
Wymuszone pliki dołączane | Co najmniej jeden wymuszony Dołącz pliki (-include [nazwa])

## <a name="additional-options"></a>Dodatkowe opcje 
