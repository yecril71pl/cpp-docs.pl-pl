---
title: "Usuń zależności w bibliotece wewnętrzne | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 05/24/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- library internals in an upgraded Visual C++ project
- _Hash_seq in an upgraded Visual C++ project
ms.assetid: 493e0452-6ecb-4edc-ae20-b6fce2d7d3c5
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c356e5f7a8bdd9441e506c9ca30c34fa3c8d5144
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="fix-your-dependencies-on-library-internals"></a>Usuń zależności w bibliotece wewnętrzne

Firma Microsoft udostępniła kodu źródłowego dla biblioteki standardowej większość biblioteki wykonawczej C i innych bibliotek Microsoft wiele wersji programu Visual Studio. Celem jest, aby lepiej zrozumieć zachowanie biblioteki i debugowania kodu. Jeden efekt uboczny publikowania kodu źródłowego biblioteki jest czy niektóre wartości wewnętrznych, struktur danych i funkcje są dostępne, nawet jeśli nie są częścią interfejsu biblioteki. Zwykle mają nazwy zaczynające się od dwóch znaków podkreślenia lub znaku podkreślenia następuje litera, nazw, które rezerwuje C++ Standard do implementacji. Te wartości, struktur i funkcje są szczegóły implementacji, które mogą ulec zmianie, zgodnie z bibliotekami ewoluują z upływem czasu, w związku z czym zdecydowanie zaleca się przed podjęciem wszelkie zależności na nich. Jeśli to zrobisz, istnieje ryzyko nieprzenośne kodu i problemy podczas migracji do nowej wersji bibliotek kodu.  

W większości przypadków What's New lub dokument fundamentalne zmiany dla każdej wersji programu Visual Studio nie wspomina zmiany wewnętrzne biblioteki. Po wszystkich jest nie może mieć wpływ następujące szczegóły implementacji. Jednak czasami możliwość przesłania użyć kodu można znaleźć w bibliotece jest zbyt duża. W tym temacie omówiono zależności dotyczące CRT lub biblioteki standardowej wewnętrzne, które mogą być stosowane na i zaktualizuj swój kod, aby usunąć te zależności, umożliwiając była przenośną lub przeprowadzić migrację do nowych wersji biblioteki.

## <a name="hashseq"></a>_Hash_seq  

Funkcja skrótu wewnętrznego `std::_Hash_seq(const unsigned char *, size_t)`, używana do zaimplementowania `std::hash` na niektóre typy ciąg był widoczny w nowszych wersjach biblioteki standardowej. Ta funkcja zaimplementowana [skrótu FNV 1a]( https://en.wikipedia.org/wiki/Fowler%E2%80%93Noll%E2%80%93Vo_hash_function) sekwencji znaków.  
  
Aby usunąć tę zależność, masz kilka opcji.  

-   Jeśli celem użytkownika jest umieszczenie `const char *` sekwencji do nieuporządkowaną kontenera za pomocą tej samej maszyny kod skrótu jako `basic_string`, możesz to zrobić za pomocą `std::hash` przeciążenia szablonu, który pobiera `std::string_view`, która zwraca tego skrótu w przenośne sposób. Kod biblioteki ciąg może lub może nie zależą od Użyj skrótu FNV 1a w przyszłości, dlatego najlepszym sposobem uniknięcia zależności algorytmu wyznaczania wartości skrótu określonej. 
  
-   Jeśli Twoje celem jest generowanie skrótów FNV 1a przez dowolnego pamięci, wprowadziliśmy kodu dostępne w serwisie GitHub w [VCSamples]( https://github.com/Microsoft/vcsamples) repozytorium w pliku nagłówka autonomicznej [fnv1a.hpp](https://github.com/Microsoft/VCSamples/tree/master/VC2015Samples/_Hash_seq), w obszarze [Licencji MIT](https://github.com/Microsoft/VCSamples/blob/master/license.txt). Dołączono również kopia wygody. Możesz skopiować ten kod do pliku nagłówka, Dodaj nagłówek dla odpowiednich kodu, a następnie znajdź i Zamień `_Hash_seq` przez `fnv1a_hash_bytes`. Otrzymasz identyczne zachowanie w wewnętrznej implementacji w `_Hash_seq`. 

```cpp  
/*
VCSamples
Copyright (c) Microsoft Corporation
All rights reserved. 
MIT License
Permission is hereby granted, free of charge, to any person obtaining a copy of
this software and associated documentation files (the "Software"), to deal in
the Software without restriction, including without limitation the rights to
use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies
of the Software, and to permit persons to whom the Software is furnished to do
so, subject to the following conditions:
The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
THE SOFTWARE IS PROVIDED *AS IS*, WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
*/
#include <stddef.h>

inline size_t fnv1a_hash_bytes(const unsigned char * first, size_t count) {
#if defined(_WIN64)
    static_assert(sizeof(size_t) == 8, "This code is for 64-bit size_t.");
    const size_t fnv_offset_basis = 14695981039346656037ULL;
    const size_t fnv_prime = 1099511628211ULL;

#else /* defined(_WIN64) */
    static_assert(sizeof(size_t) == 4, "This code is for 32-bit size_t.");
    const size_t fnv_offset_basis = 2166136261U;
    const size_t fnv_prime = 16777619U;
#endif /* defined(_WIN64) */

    size_t result = fnv_offset_basis;
    for (size_t next = 0; next < count; ++next)
        {   // fold in another byte
        result ^= (size_t)first[next];
        result *= fnv_prime;
        }
    return (result);
}
```  
  
## <a name="see-also"></a>Zobacz także  
  
[Uaktualnianie projektów ze starszych wersji programu Visual C++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)  
[Omówienie potencjalne problemy z uaktualnieniem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)  
[Uaktualnienie kodu do Universal CRT](upgrade-your-code-to-the-universal-crt.md)  
