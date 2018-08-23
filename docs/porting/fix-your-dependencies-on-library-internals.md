---
title: Naprawianie zależności w bibliotece wewnętrznej | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 05/24/2017
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- library internals in an upgraded Visual C++ project
- _Hash_seq in an upgraded Visual C++ project
ms.assetid: 493e0452-6ecb-4edc-ae20-b6fce2d7d3c5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c80bad11a13c454d8b4025e5cc0745514696a0f7
ms.sourcegitcommit: e9ce38decc9f986edab5543de3464b11ebccb123
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/13/2018
ms.locfileid: "42465241"
---
# <a name="fix-your-dependencies-on-library-internals"></a>Naprawianie zależności w bibliotece wewnętrznej

Firma Microsoft opublikowała kod źródłowy biblioteki standardowej, większość Biblioteka uruchomieniowa C i inne biblioteki Microsoft wiele wersji programu Visual Studio. Celem jest, aby lepiej zrozumieć zachowanie biblioteki i debugowania kodu. Jeden efekt uboczny publikowania kod źródłowy biblioteki jest czy niektóre wartości wewnętrznych struktur danych i funkcje są widoczne, mimo że nie są one częścią interfejs biblioteki. Zazwyczaj mają nazwy rozpoczynające się z dwoma podkreśleniami lub znakiem podkreślenia następuje litera, nazw, które C++ Standard zastrzega sobie do implementacji. Te wartości, struktur i funkcje są szczegóły implementacji, które mogą ulec zmianie, zgodnie z czasem ewoluować biblioteki, więc zdecydowanie zaleca się wykonanie wszelkich zależności na nich. Jeśli to zrobisz, istnieje ryzyko kod przenośny między i problemy podczas próby migracji kodu do nowej wersji bibliotek.  

W większości przypadków What's New lub dokumentu fundamentalne zmiany w każdej wersji programu Visual Studio nie wspomnieć o zmiany w bibliotece wewnętrznej. Po wszystkich nie są powinien mieć wpływ tych szczegółów implementacji. Jednak czasami stosowania kodu, które widać w bibliotece jest zbyt duża. W tym temacie omówiono zależności na CRT i standardowej biblioteki elementy wewnętrzne, które mogą mieć skorzystała z i zaktualizuj kod w celu usunięcia tych zależności, co pozwala dowolnie bardziej przenośny lub migrację do nowych wersji biblioteki.

## <a name="hashseq"></a>_Hash_seq  

Funkcja skrótu wewnętrznego `std::_Hash_seq(const unsigned char *, size_t)`, który jest używany do implementowania `std::hash` na niektórych typach parametrów był widoczny w nowszych wersjach standardowej biblioteki. Ta funkcja implementowana [skrótu FNV 1a]( https://en.wikipedia.org/wiki/Fowler%E2%80%93Noll%E2%80%93Vo_hash_function) na sekwencję znaków.  
  
Aby usunąć tę zależność, masz kilka opcji.  

- Jeśli zgodne z zamiarami użytkownika polega na umieszczeniu `const char *` sekwencji do nieuporządkowaną kontenera przy użyciu tej samej maszyny kod skrótu jako `basic_string`, możecie przy użyciu `std::hash` przeciążenia szablonu, który przyjmuje `std::string_view`, która zwraca wartość tego skrótu w przenośne sposób. Kod biblioteki ciąg może być lub może nie zależą od stosowania skrótów FNV 1a w przyszłości, więc jest najlepszym sposobem uniknięcia zależności algorytmu mieszania określonego. 
  
- Jeśli jest zgodne z zamiarami użytkownika do generowania skrótów FNV 1a za pośrednictwem dowolnego pamięci, wprowadziliśmy kod dostępne w usłudze GitHub w [VCSamples]( https://github.com/Microsoft/vcsamples) repozytorium w pliku nagłówka autonomicznej [fnv1a.hpp](https://github.com/Microsoft/VCSamples/tree/master/VC2015Samples/_Hash_seq), w obszarze [Licencją MIT](https://github.com/Microsoft/VCSamples/blob/master/license.txt). Dołączono również Kopiuj tutaj dla Twojej wygody. Możesz skopiować ten kod do pliku nagłówka, Dodaj nagłówek do jakiegokolwiek kodu, których dotyczy problem, a następnie znajdź i Zamień `_Hash_seq` przez `fnv1a_hash_bytes`. Otrzymasz identyczne zachowanie wewnętrznej implementacji w `_Hash_seq`. 

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
[Omówienie potencjalnych problemów z uaktualnieniem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)  
[Uaktualnienie kodu do Universal CRT](upgrade-your-code-to-the-universal-crt.md)  