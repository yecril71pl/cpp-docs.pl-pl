---
title: C++Pliki nagłówkowe biblioteki standardowej
ms.date: 07/12/2019
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: 807e65c69e55d8790b77a493e4ae1878aa740557
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2019
ms.locfileid: "74305409"
---
# <a name="c-standard-library-header-files"></a>C++Pliki nagłówkowe biblioteki standardowej

Pliki nagłówkowe dla C++ standardowej biblioteki i rozszerzeń, według kategorii.

## <a name="headers-by-category"></a>Nagłówki według kategorii

::: moniker range=">=vs-2017"

| Kategoria | nagłówka |
| - | - |
| [Algorytmy](../cpp/algorithms-modern-cpp.md) | [algorytm\<>](algorithm.md), [\<cstdlib >](cstdlib.md), [\<liczbowe >](numeric.md) |
| Operacje niepodzielne |  [\<niepodzielne >](atomic.md)<sup>11</sup> |
| Otoki biblioteki C | [\<cassert >](cassert.md), [\<ccomplex >](ccomplex.md)<sup>11 a b</sup> [\<cctype >](cctype.md), [\<cerrno >](cerrno.md), [\<cfenv >](cfenv.md)<sup>11</sup>, [\<cfloat >](cfloat.md), [\<](cinttypes.md)cinttypes ><sup>11</sup>, [\<ciso646 >](ciso646.md)<sup>b</sup>, [\<climits](climits.md)>, [\<](clocale.md)CLocale >, [\<cmath](cmath.md)>, [\<](csetjmp.md)csetjmp > [,\<csignal >](csignal.md), [\<cstdalign >](cstdalign.md)<sup>11 a b</sup>, [\<cstdarg >](cstdarg.md), [\<cstdbool >](cstdbool.md)<sup>11 a b</sup> [\<](cstddef.md)cstddef >,\<[cstdint >](cstdint.md)<sup>11</sup>\<cstdio [>,](cstdio.md) [\<cstdlib >](cstdlib.md), [\<](cstring.md)CString >, [\<ctgmath](cuchar.md)<sup></sup> [> 11](ctgmath.md)<sup>a b</sup>\<[CTime >](ctime.md) , [\<cwchar >](cwchar.md), [\<cwctype >](cwctype.md)\< |
| Pojęcia | koncepcje \<><sup>20</sup> |
| [Kontenery](../cpp/containers-modern-cpp.md) | |
| Kontenery sekwencji | [\<array >](array.md)<sup>11</sup>, [\<deque >](deque.md), [\<](forward-list.md)forward_list ><sup>11</sup>, [\<listy](list.md)>, [\<wektor >](vector.md) |
| Uporządkowane Kontenery asocjacyjne| [\<mapowanie >](map.md), [\<ustawić >](set.md) |
| Nieuporządkowane Kontenery asocjacyjne | [\<unordered_map >](unordered-map.md)<sup>11</sup>, [\<unordered_set >](unordered-set.md)<sup>11</sup> |
| Adaptery kontenerów | [\<queue>](queue.md), [\<stack>](stack.md) |
| Widoki kontenerów | \<zakresu ><sup>20</sup> |
| [Błędy i obsługa wyjątków](../cpp/errors-and-exception-handling-modern-cpp.md) | [\<cassert >](cassert.md), [\<> wyjątków](exception.md), [\<stdexcept >](stdexcept.md), [\<](system-error.md)system_error ><sup>11</sup> |
| Narzędzia ogólne | \<dowolnych ><sup>17</sup> [](tuple.md)<sup></sup> [\<bitset >](bitset.md), \<charconv ><sup>17</sup>, [\<cstdlib >](cstdlib.md), \<wykonywania ><sup>17</sup>\<> [funkcjonalnej](functional.md) [\<> \<, memory_resource](memory.md)<sup>> \<</sup> [>](scoped-allocator.md)<sup></sup><sup>17</sup> [\<](ratio.md)<sup></sup> [\<type_traits >](type-traits.md)<sup>11</sup> [\<typeindex >](typeindex.md)<sup>11</sup>\<[narzędzi](utility.md)> \<wariant ><sup>17</sup>\<\< |
| [We/wy i formatowanie](../text/string-and-i-o-formatting-modern-cpp.md) | [\<cinttypes >](cinttypes.md)<sup>11</sup>, [\<cstdio >](cstdio.md), [\<system plików >](filesystem.md)<sup>17</sup>, [\<fstream — >](fstream.md), [\<iomanip >](iomanip.md), [\<iOS](ios.md)> [,\<iosfwd](iosfwd.md) [>,](sstream.md) [\<iostream](iostream.md)> [,\<](istream.md) [IStream](streambuf.md)> [,\<ostream](ostream.md) [>](strstream.md)<sup> </sup>, \<syncstream ><sup>20</sup>\<\<\< |
| Iteratory | [\<iterator>](iterator.md) |
| Obsługa języków | [\<cfloat >](cfloat.md), [\<climits >](climits.md), [\<codecvt >](codecvt.md)<sup>11 a</sup>, \<porównać ><sup>20</sup>, \<umowa ><sup>20</sup>\<współpracującej ><sup>20</sup>, [\<csetjmp >](csetjmp.md), [\<](csignal.md)csignal >, [\<](cstdarg.md)cstdarg [>,\<cstddef >](cstddef.md),\<[cstdint >](cstdint.md)<sup>11</sup>, [\<cstdlib >](cstdlib.md), [\<>](exception.md) , [\<initializer_list >](initializer-list.md)<sup>11</sup> [\<limity >](limits.md), [\<nowe >](new.md), [\<](typeinfo.md)><sup></sup>\< |
| Lokalizacja | [\<clocale >](clocale.md), [\<codecvt >](codecvt.md)<sup>11 a</sup>, [\<CVT/wbuffer >](cvt-wbuffer.md), [\<CVT/wstring >](cvt-wstring.md), [\<ustawienia regionalne >](locale.md) |
| Obliczenia matematyczne i liczbowe | \<bit ><sup>20</sup>, [\<cfenv >](cfenv.md)<sup>11</sup>, [\<cmath >](cmath.md), [\<złożone >](complex.md), [\<cstdlib >](cstdlib.md), [\<ograniczenia](limits.md)>, [\<liczbowe >](numeric.md), [\<losowo >](random.md)<sup>11</sup>, [współczynnik\<>](ratio.md)<sup>11</sup>\<[valarray >](valarray.md) |
| [Zarządzanie pamięcią](../cpp/smart-pointers-modern-cpp.md) | [\<przydzielania >](allocators-header.md), [\<> pamięci](memory.md), \<memory_resource ><sup>17</sup>, [\<nowe >](new.md), [\<](scoped-allocator.md)scoped_allocator ><sup>11</sup> |
| Wielowątkowość | [\<niepodzielną >](atomic.md)<sup>11</sup>, [\<condition_variable >](condition-variable.md)<sup>11</sup> [\<w przyszłości](future.md)><sup>11</sup>, [\<muteks >](mutex.md)<sup>11</sup>, [\<shared_mutex](shared-mutex.md)><sup>14</sup>, [\<wątku >](thread.md)<sup>11</sup> |
| Zakresy | zakresy \<><sup>20</sup> |
| Wyrażenia regularne | [\<wyrażenia regularnego >](regex.md)<sup>11</sup> |
| Ciągi i dane znakowe | [\<cctype >](cctype.md), [\<cstdlib >](cstdlib.md), [\<cstring >](cstring.md), [\<cuchar >](cuchar.md)<sup>11</sup>, [\<cwchar >](cwchar.md), [\<cwctype >](cwctype.md), [\<wyrażenie regularne >](regex.md)<sup>11</sup>, [\<ciąg >](string.md), [\<string_view](string-view.md)><sup>17</sup> |
| Godzina | [\<chrono >](chrono.md)<sup>11</sup> [\<CTime >](ctime.md) |

<sup>11</sup> dodano w standardzie c++ 11. \
<sup>14</sup> dodano w standardzie c++ 14. \
<sup>17</sup> dodano w standardzie c++ 17. \
<sup>20</sup> dodano w wersji próbnej standardu c++ 20. \
<sup>przestarzałe</sup> w standardzie c++ 17. \
<sup>b</sup> usunięto w wersji próbnej standardu c++ 20. \
język <sup>c</sup> jest przestarzały w standardzie c++ 98.

::: moniker-end

::: moniker range="vs-2015"

|Kategoria|nagłówka|
|-|-|
|[Algorytmy](../cpp/algorithms-modern-cpp.md)|[algorytm \<>](algorithm.md)|
|Otoki biblioteki C|[\<cassert>](cassert.md), [\<cctype>](cctype.md), [\<cerrno>](cerrno.md), [\<cfenv>](cfenv.md), [\<cfloat>](cfloat.md), [\<cinttypes>](cinttypes.md), [\<ciso646>](ciso646.md), [\<climits>](climits.md), [\<clocale>](clocale.md), [\<cmath>](cmath.md), [\<csetjmp>](csetjmp.md), [\<csignal>](csignal.md), [\<cstdarg>](cstdarg.md), [\<cstdbool>](cstdbool.md), [\<cstddef>](cstddef.md), [\<cstdint>](cstdint.md), [\<cstdio>](cstdio.md), [\<cstdlib>](cstdlib.md), [\<cstring>](cstring.md), [\<ctgmath>](ctgmath.md), [\<ctime>](ctime.md), [\<cwchar>](cwchar.md), [\<cwctype>](cwctype.md)|
|[Kontenery](../cpp/containers-modern-cpp.md)||
|Kontenery sekwencji|[\<array >](array.md), [\<deque >](deque.md), [\<](forward-list.md)forward_list > [,\<>,](list.md)\<[wektor >](vector.md)|
|Uporządkowane Kontenery asocjacyjne| [\<mapowanie >](map.md), [\<ustawić >](set.md)|
|Nieuporządkowane Kontenery asocjacyjne|[\<unordered_map >](unordered-map.md), [\<unordered_set >](unordered-set.md)|
|Kontenery adaptera|[\<queue>](queue.md), [\<stack>](stack.md)|
|[Błędy i obsługa wyjątków](../cpp/errors-and-exception-handling-modern-cpp.md)|[\<> wyjątków](exception.md), [\<stdexcept >](stdexcept.md), [\<](system-error.md) system_error >|
|[We/wy i formatowanie](../text/string-and-i-o-formatting-modern-cpp.md)|[\<filesystem>](filesystem.md), [\<fstream>](fstream.md), [\<iomanip>](iomanip.md), [\<ios>](ios.md), [\<iosfwd>](iosfwd.md), [\<iostream>](iostream.md), [\<istream>](istream.md), [\<ostream>](ostream.md), [\<sstream>](sstream.md), [\<streambuf>](streambuf.md), [\<strstream>](strstream.md)|
|Iteratory|[\<iterator>](iterator.md)|
|Lokalizacja|[\<codecvt >](codecvt.md), [\<cvt/wbuffer >](cvt-wbuffer.md), [\<cvt/wstring >](cvt-wstring.md), [\<ustawienia regionalne >](locale.md)|
|Obliczenia matematyczne i liczbowe|[\<złożone >](complex.md), [\<ograniczenia >](limits.md), [\<liczb >](numeric.md), [\<losowego >](random.md),\<[współczynnik](ratio.md)>, [\<valarray >](valarray.md)|
|[Zarządzanie pamięcią](../cpp/smart-pointers-modern-cpp.md)|[\<przydzielania >](allocators-header.md), [\<> pamięci](memory.md), [\<nowe >](new.md), [\<](scoped-allocator.md) scoped_allocator >|
|Wielowątkowość|[\<niepodzielne >](atomic.md), [\<condition_variable >](condition-variable.md), [\<przyszłe >](future.md), [\<](mutex.md) [>\<](shared-mutex.md) [](thread.md)\<|
|Inne narzędzia|[\<bitset >](bitset.md), [\<chrono >](chrono.md), [\<funkcjonalne >](functional.md), [\<initializer_list](initializer-list.md)>, [\<> spójnej kolekcji](tuple.md) [\<type_traits](type-traits.md) [typeindex](typeindex.md)> [\<, >](typeinfo.md) [](utility.md)\<\<|
|Ciągi i dane znakowe|[\<> wyrażeń regularnych](regex.md), [\<ciąg >](string.md), [\<](string-view.md) string_view >

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Korzystanie C++ z nagłówków biblioteki](using-cpp-library-headers.md)\
[C++Biblioteka standardowa](cpp-standard-library-reference.md)
