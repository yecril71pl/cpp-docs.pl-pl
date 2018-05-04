---
title: Algorytmy (Modern C++) | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6f758d3c-a7c7-4a50-92bb-97b2f6d4ab27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fdd5742bb86992ce20f5a52f587c8557d46a97eb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="algorithms-modern-c"></a>Algorytmy (Modern C++)
Dla nowoczesnych programowania w języku C++, zalecane jest użycie algorytmów w [standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md). Oto kilka przykładów ważne:  
  
-   `for_each`, który jest domyślnym algorytmem przechodzenie. (Również `transform` dla semantyki nie w miejscu.)  
  
-   `find_if`, która jest domyślny algorytm wyszukiwania.  
  
-   `sort`, `lower_bound`, wartością domyślną, sortowanie i wyszukiwanie algorytmów.  
  
 Aby napisać komparatora, użyj strict `<` i użyj *o nazwie wyrażeń lambda* po można.  
  
```cpp  
auto comp = [](const widget& w1, const widget& w2)  
      { return w1.weight() < w2.weight(); }  
  
sort( v.begin(), v.end(), comp );  
  
auto i = lower_bound( v.begin(), v.end(), comp );  
```  
  
## <a name="loops"></a>Pętle  
 Jeśli to możliwe, użyj opartej na zakresie `for` pętle wywołania algorytmu, i/lub zamiast odręcznego pętli.`copy`, `transform`, `count_if`, `remove_if`, i inne jak ich są znacznie lepszą niż odręcznie pętle ponieważ ich celem jest jasne, a umożliwiają łatwiejsze do pisania kodu bez błędów. Wiele algorytmów standardowa biblioteka C++ mieć optymalizacje implementacji, które były bardziej wydajne.  
  
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
  
 Użyj nowoczesnych wersji języka C++ następująco:  
  
```cpp  
for_each( begin(strings), end(strings), [](string& s) {  
   // ...  
} );  
  
auto i = find_if( begin(v), end(v),  [=](int i) { return i > x && i < y; } );  
```  
  
### <a name="range-based-for-loops"></a>Na podstawie zakresu dla pętli  
 Zakres oparty `for` pętla jest funkcją języka C ++ 11, języka, nie jest algorytm standardowa biblioteka C++. Ale wymaga ona uwagi w tej dyskusji o pętle. Oparta na zakresie `for` pętle są rozszerzeniem `for` — słowo kluczowe i zapewniają wygodne i skuteczny sposób zapisu pętli, które iteracja zakresu wartości. Standardowa biblioteka C++ kontenerów, ciągi i tablice są gotowe do opartej na zakresie `for` pętli. Aby włączyć tej nowej składni iteracji dla danego typu zdefiniowane przez użytkownika, należy dodać następujące możliwości:  
  
-   A `begin` metodę zwracającą iterator na początku struktury i `end` metodę zwracającą iterator na końcu struktury.  
  
-   Obsługa w iterator dotyczącej tych metod: `operator*`, `operator!=`, i `operator++` (prefiks wersji).  
  
 Te metody można elementów członkowskich lub autonomicznych funkcji.  
  
## <a name="random-numbers"></a>Liczby losowe  
 Nie jest brak tajne który starego CRT `rand()` funkcja ma wiele błędów, które długości omówione w społeczności C++. W nowoczesnych wersji języka C++, nie trzeba uwzględniać tych nieprawidłowości — ani mieć magazynowa własne jednolicie rozproszonej generatora liczb losowych — narzędzia do szybkiego i łatwego tworzenia ich nie są dostępne w standardowej bibliotece C++, jak pokazano w [ \<losowe >](../standard-library/random.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Zapraszamy ponownie do języka C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Dokumentacja języka C++](../cpp/cpp-language-reference.md)   
 [Standardowa biblioteka C++](../standard-library/cpp-standard-library-reference.md)