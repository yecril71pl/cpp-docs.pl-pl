---
title: Algorytmy (Modern C++)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6f758d3c-a7c7-4a50-92bb-97b2f6d4ab27
ms.openlocfilehash: b972e575c982ae2523ec560a6237eac76ceaf834
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220156"
---
# <a name="algorithms-modern-c"></a>Algorytmy (Modern C++)

Nowoczesnym programowaniu C++, zaleca się używanie algorytmów w [standardowej biblioteki języka C++](../standard-library/cpp-standard-library-reference.md). Poniżej przedstawiono kilka przykładów ważnych:

- **for_each**, który jest domyślnym algorytmem przechodzenia. (Również **Przekształcanie** dla semantyki not-in-place.)

- **find_if**, który jest domyślnym algorytmem wyszukiwania.

- **Sortuj**, **lower_bound**i inne domyślne algorytmy wyszukiwania i sortowania.

Aby zapisać komparator, należy użyć ściśle **<** i użyj *o nazwie lambdas* kiedy to możliwe.

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="loops"></a>Pętle

Jeśli to możliwe, należy użyć opartej na zakresie **dla** pętli lub wywołań algorytmu lub obu, zamiast pętli napisanych ręcznie. **Kopiuj**, **Przekształcanie**, **count_if —**, **remove_if —**, i inne podobne do tych są znacznie lepsze niż pętle odręczne, ponieważ ich zamiar jest oczywisty i ułatwiają pisanie kodu wolny od błędów. Ponadto wiele algorytmów standardowej biblioteki języka C++ ma zoptymalizowane wdrażanie, które czyni je bardziej efektywnymi.

Zamiast starego C++ następująco:

```cpp
for ( auto i = strings.begin(); i != strings.end(); ++i ) {
    /* ... */
}

auto i = v.begin();

for ( ; i != v.end(); ++i ) {
    if (*i > x && *i < y) break;
}
```

Użyj nowoczesnego C++ następująco:

```cpp
for_each( begin(strings), end(strings), [](string& s) {
  // ...
} );

auto i = find_if( begin(v), end(v),  [=](int i) { return i > x && i < y; } );
```

### <a name="range-based-for-loops"></a>Zakresu pętli for opierających

Bazująca na zakresie **dla** pętla jest funkcją języka C ++ 11, języka, nie algorytmów standardowej biblioteki języka C++. Ale to zasługuje na wzmiankę w tej dyskusji na temat pętli. Oparta na zakresie **dla** pętli stanowią rozszerzenie **dla** — słowo kluczowe i zapewniają wygodny i wydajny sposób pisania pętli, które przechodzą przez zakres wartości. Kontenery standardowej biblioteki C++, ciągi i tablice są gotowe do użycia dla opartej na zakresie **dla** pętli. Aby włączyć nową składnię iteracji dla Twojego typu zdefiniowanego przez użytkownika, należy dodać następującą obsługę:

- A `begin` metodę, która zwraca iterację do początku struktury i `end` metodę, która zwraca iterację na koniec struktury.

- Wsparcie dla iteratorów dla tych metod: **operator**<strong>\*</strong>, **operator! =**, i **operator ++** (wersja prefiks).

Te metody mogą być członkami lub funkcjami autonomicznymi.

## <a name="random-numbers"></a>Liczby losowe

Nie jest tajemnicą, stare CRT `rand()` funkcja ma wiele wad, które zostały omówione szeroko w społeczności C++. W nowoczesnym C++, nie masz do czynienia z tymi niedociągnięciami — ani nie musisz wymyślić własnego równomiernie rozłożonego generatora liczb losowych, ponieważ narzędzia służące do szybkiego i łatwego tworzenia ich są dostępne w standardowej biblioteki C++, jak pokazano na [ \<losowy >](../standard-library/random.md).

## <a name="see-also"></a>Zobacz także

[Witaj z powrotem w języku C++ (Modern C++)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Dokumentacja języka C++](../cpp/cpp-language-reference.md)<br/>
[Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)<br/>
