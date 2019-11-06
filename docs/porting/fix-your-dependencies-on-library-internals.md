---
title: Popraw zależności od C++ elementów wewnętrznych biblioteki
ms.date: 05/24/2017
helpviewer_keywords:
- library internals in an upgraded Visual Studio C++ project
- _Hash_seq in an upgraded Visual Studio C++ project
ms.assetid: 493e0452-6ecb-4edc-ae20-b6fce2d7d3c5
ms.openlocfilehash: 5486cd65a34e3ef69f3b2e948ba0ad020e68b326
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627012"
---
# <a name="fix-your-dependencies-on-c-library-internals"></a>Popraw zależności od C++ elementów wewnętrznych biblioteki

Firma Microsoft opublikowała kod źródłowy biblioteki standardowej, większość biblioteki środowiska uruchomieniowego języka C i innych bibliotek firmy Microsoft w wielu wersjach programu Visual Studio. Celem jest ułatwienie zrozumienia zachowania biblioteki i debugowanie kodu. Jedną z efektów ubocznych publikowania kodu źródłowego biblioteki jest to, że niektóre wartości wewnętrzne, struktury danych i funkcje są ujawniane, nawet jeśli nie są częścią interfejsu biblioteki. Zazwyczaj mają nazwy zaczynające się od dwóch znaków podkreślenia lub podkreślenia, po którym następuje Wielka litera, nazwy, które są C++ rezerwy standardowe na implementacje. Te wartości, struktury i funkcje to szczegóły implementacji, które mogą ulec zmianie w miarę rozwoju bibliotek w czasie, dlatego zdecydowanie zalecamy, aby przed przejęciem jakichkolwiek zależności. Jeśli tak zrobisz, będziesz mieć ryzyko związane z nieprzenośnym kodem i problemami podczas próby migracji kodu do nowych wersji bibliotek.

W większości przypadków dokument o nowościach i zmianach w poszczególnych wersjach programu Visual Studio nie zawiera informacji o zmianach wewnętrznych biblioteki. Wszystkie te szczegóły implementacji nie będą miały żadnych zmian. Jednak czasami Temptation użyć kodu, który można zobaczyć w bibliotece, jest zbyt doskonały. W tym temacie omówiono zależności od elementów wewnętrznych w bibliotece CRT lub standardowej, które mogą być używane, oraz sposobu aktualizowania kodu w celu usunięcia tych zależności, aby można było je bardziej przenosić lub migrować do nowych wersji biblioteki.

## <a name="_hash_seq"></a>_Hash_seq

Wewnętrzna funkcja skrótu `std::_Hash_seq(const unsigned char *, size_t)`używana do implementowania `std::hash` dla niektórych typów ciągów była widoczna w ostatnich wersjach biblioteki standardowej. Ta funkcja implementuje [skrót FNV-1a]( https://en.wikipedia.org/wiki/Fowler%E2%80%93Noll%E2%80%93Vo_hash_function) na sekwencji znaków.

Aby usunąć tę zależność, masz kilka opcji.

- Jeśli zamiarem jest umieszczenie sekwencji `const char *` w nieuporządkowanym kontenerze za pomocą tej samej maszyny kodu skrótu jako `basic_string`, można to zrobić przy użyciu przeciążenia szablonu `std::hash` zawierającego `std::string_view`, która zwraca ten kod skrótu w sposób przenośny. Kod biblioteki ciągów może lub nie może polegać na użyciu skrótu FNV-1a w przyszłości, więc jest to najlepszy sposób, aby uniknąć zależności od określonego algorytmu wyznaczania wartości skrótu.

- Jeśli zamiarem jest wygenerowanie skrótu FNV-1A dla dowolnej pamięci, wprowadziliśmy kod dostępny w witrynie GitHub w repozytorium [VCSamples]( https://github.com/Microsoft/vcsamples) w autonomicznym pliku nagłówkowym, [fnv1a. HPP](https://github.com/Microsoft/VCSamples/tree/master/VC2015Samples/_Hash_seq), w ramach [licencji MIT](https://github.com/Microsoft/VCSamples/blob/master/license.txt). Dodaliśmy również tutaj kopię dla wygody użytkownika. Możesz skopiować ten kod do pliku nagłówkowego, dodać nagłówek do dowolnego kodu, którego dotyczy ten kod, a następnie znaleźć i zastąpić `_Hash_seq` przez `fnv1a_hash_bytes`. Nastąpi takie samo zachowanie wewnętrznej implementacji w `_Hash_seq`.

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
    {
        // fold in another byte
        result ^= (size_t)first[next];
        result *= fnv_prime;
    }
    return (result);
}
```

## <a name="see-also"></a>Zobacz także

[Uaktualnianie projektów ze starszych wersji wizualizacjiC++](upgrading-projects-from-earlier-versions-of-visual-cpp.md)<br/>
[Omówienie potencjalnych problemów z uaktualnieniem (Visual C++)](overview-of-potential-upgrade-issues-visual-cpp.md)<br/>
[Uaktualnienie kodu do Universal CRT](upgrade-your-code-to-the-universal-crt.md)