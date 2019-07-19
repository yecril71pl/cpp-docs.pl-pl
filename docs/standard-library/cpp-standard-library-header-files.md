---
title: C++Pliki nagłówkowe biblioteki standardowej
ms.date: 07/12/2019
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: dc337ef078108d86849aa7b7452512dfb69e6e18
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341124"
---
# <a name="c-standard-library-header-files"></a>C++Pliki nagłówkowe biblioteki standardowej

Pliki nagłówkowe dla C++ standardowej biblioteki i rozszerzeń, według kategorii.

## <a name="headers-by-category"></a>Nagłówki według kategorii

::: moniker range=">=vs-2017"

| Kategoria | Nagłówka |
| - | - |
| [Algorytmy](../cpp/algorithms-modern-cpp.md) | algorytm > [, cstdlib>,numeryczne\<](cstdlib.md)> [ \<](algorithm.md) [ \<](numeric.md) |
| Operacje niepodzielne |  niepodzielna ><sup>11</sup> [ \<](atomic.md) |
| Otoki biblioteki C | [ \<](cfenv.md)<sup></sup> [ \<](cerrno.md) [ \<cassert >](cctype.md), [ccomplex > 11 a b, cctype >, cerrno >, cfenv > 11, \<](ccomplex.md) [ \<](cassert.md)<sup></sup> [ \<cfloat >](cfloat.md),<sup></sup> [ \<cinttypes >](cinttypes.md)11, [ \<ciso646 >](ciso646.md)<sup>b</sup>, [ \<climits >](climits.md), [ \<CLocale >](clocale.md), [ cmath\<>](cmath.md), [ csetjmp>,csignal>,cstdalign>11ab,cstdarg>,\<](csetjmp.md) [ \<](cstdarg.md) [ \<](csignal.md) [ \<](cstdalign.md)<sup></sup> [ \<cstdbool >](cstdbool.md)<sup>11 a b</sup>, [ \<cstddef >](cstddef.md), [ \<cstdint >](cstdint.md)<sup>11</sup>, [ \<cstdio >](cstdio.md), [ \<cstdlib >](cstdlib.md), [ CString\<>](cstring.md),<sup></sup> [ \<](ctime.md)<sup></sup> [ \<](cuchar.md) [ \<](cwchar.md) [ ctgmath>\<](ctgmath.md)11 a b, CTime > cuchar > 11, cwchar >, [ cwctype\<>](cwctype.md) |
| Pojęcia | \<pojęcia ><sup>20</sup> |
| [Kontenery](../cpp/containers-modern-cpp.md) | |
| Kontenery sekwencji | <sup></sup><sup></sup> [ Array\<>](array.md)11, [ deque>,forward_list>11,list>,Vector>\<](deque.md) [ \<](forward-list.md) [ \<](list.md) [ \<](vector.md) |
| Uporządkowane Kontenery asocjacyjne| Mapuj >, [ \<](map.md) [ Ustaw>\<](set.md) |
| Nieuporządkowane Kontenery asocjacyjne | unordered_map ><sup>11</sup>, [ unordered_set>\<](unordered-set.md)<sup>11</sup> [ \<](unordered-map.md) |
| Adaptery kontenerów | [\<queue>](queue.md), [\<stack>](stack.md) |
| Widoki kontenerów | \<zakres ><sup>20</sup> |
| [Błędy i obsługa wyjątków](../cpp/errors-and-exception-handling-modern-cpp.md) | <sup></sup> [ cassert\<>](cassert.md) [, >\<wyjątków](exception.md) [, stdexcept\<>](stdexcept.md) [, system_error\<>](system-error.md)11 |
| Narzędzia ogólne | \<Każda ><sup>17</sup>, [ \<bitset >](bitset.md), \<charconv ><sup>17</sup>, [ \<cstdlib >](cstdlib.md), \<wykonywanie ><sup>17</sup>, [ \<funkcjonalne >](functional.md), [ >\<pamięci](memory.md), \< [ \<](ratio.md)<sup></sup><sup></sup><sup></sup>memory_resource > 17, opcjonalne > 17, stosunek > 11, scoped_allocator > \< [ \< ](scoped-allocator.md) <sup>11</sup>,<sup></sup><sup></sup><sup></sup> [ \<](type-traits.md) [ \<](typeindex.md) [ \<krotka](utility.md)> 11, type_traits > 11, typeindex > 11, > narzędzi [ \<](tuple.md) \<wariant ><sup>17</sup> |
| [We/wy i formatowanie](../cpp/string-and-i-o-formatting-modern-cpp.md) | <sup></sup><sup></sup> [ cinttypes\<>](cinttypes.md)11, [ cstdio>,FileSystem>17,fstream—>,iomanip>,\<](cstdio.md) [ \<](filesystem.md) [ \<](fstream.md) [ \<](iomanip.md) [ iOS\<>](ios.md), [ iosfwd>,iostream>,IStream>,ostream>,strumienia>\<](iosfwd.md) [ \<](iostream.md) [ \<](istream.md) [ \<](ostream.md) [ \<](sstream.md) \< [ ,\<streambuf >](streambuf.md) [ ,\<strstream >](strstream.md)<sup>c</sup>, syncstream ><sup>20</sup> |
| Iteratory | [\<iterator>](iterator.md) |
| Obsługa języków | \< \< \< <sup></sup><sup></sup><sup></sup> [ cfloat\<>](cfloat.md) [, climits\<>](climits.md) [, codecvt\<>](codecvt.md)11 a, Porównaj > 20, kontrakt > 20, Wspólna ><sup>20</sup>, [ \<csetjmp >](csetjmp.md), [ \<csignal >](csignal.md), [ \<cstdarg >](cstdarg.md), [ \<cstddef >](cstddef.md), [ \<cstdint > ](cstdint.md) <sup>11</sup><sup></sup> [, cstdlib\<>](cstdlib.md) [, wyjątek\<>](exception.md) [, initializer_list\<>](initializer-list.md)11 [, limity>,\<](limits.md) [ \< nowe >](new.md), [ \<>](typeinfo.md), \<wersja ><sup>20</sup> |
| Lokalizacja | [ \<](locale.md) <sup></sup> [ CLocale>\<](cvt-wbuffer.md), [codecvt > 11 a, CVT/wbuffer >, CVT/wstring >, ustawienia regionalne > \<](codecvt.md) [ \<](cvt-wstring.md) [ \<](clocale.md) |
| Obliczenia matematyczne i liczbowe | \<bit ><sup>20</sup>, [ \<cfenv >](cfenv.md)<sup>11</sup>, [ \<cmath >](cmath.md), [ \<złożone >](complex.md), [ \<cstdlib >](cstdlib.md), [ \<limity >](limits.md), [ liczbowe\<>](numeric.md),<sup></sup><sup></sup> [ losowo\<>](random.md)11 [, stosunek>11,valarray>\<](ratio.md) [ \<](valarray.md) |
| [Zarządzanie pamięcią](../cpp/smart-pointers-modern-cpp.md) | <sup></sup><sup></sup> [ przypisania>\<](new.md), \< [ \<](scoped-allocator.md) [ >\<pamięci](memory.md), memory_resource > 17, nowe >, scoped_allocator > 11 [ \<](allocators-header.md) |
| Wielowątkowość | <sup></sup><sup></sup> [ \<](mutex.md)<sup></sup><sup></sup> [ \<](condition-variable.md) [ \<](future.md) [ \<niepodzielna >](atomic.md)11, condition_variable > 11, przyszłość > 11, mutex > 11, [ \< shared_mutex >](shared-mutex.md)<sup>14</sup>, [ \<wątek >](thread.md)<sup>11</sup> |
| Zakresy | \<zakresy ><sup>20</sup> |
| Wyrażenia regularne | wyrażenie regularne ><sup>11</sup> [ \<](regex.md) |
| Ciągi i dane znakowe | <sup></sup> [ cctype\<>](cctype.md), [ cstdlib>,CString>,cuchar>11,cwchar>,cwctype\<](cstdlib.md) [ \<](cstring.md) [ \<](cuchar.md) [ \<](cwchar.md) [ \< >](cwctype.md) [ ,\<wyrażenie regularne >](regex.md)<sup>11</sup>, [ \<ciąg >](string.md), [ \<string_view >](string-view.md)<sup>17</sup> |
| Godzina | Chrono > 11<sup></sup> [ CTime\<>](ctime.md) [ \<](chrono.md) |

<sup>11</sup> dodano w standardzie c++ 11. \
<sup>14</sup> dodano w standardzie c++ 14. \
<sup>17</sup> dodano w standardzie c++ 17. \
<sup>20</sup> dodano w wersji próbnej standardu c++ 20. \
<sup>przestarzałe</sup> w standardzie c++ 17. \
<sup>b</sup> usunięto w wersji próbnej standardu c++ 20. \
język <sup>c</sup> jest przestarzały w standardzie c++ 98.

::: moniker-end

::: moniker range="vs-2015"

|Kategoria|Nagłówka|
|-|-|
|[Algorytmy](../cpp/algorithms-modern-cpp.md)|[\<algorytm >](algorithm.md)|
|Otoki biblioteki C|[\<cassert>](cassert.md), [\<cctype>](cctype.md), [\<cerrno>](cerrno.md), [\<cfenv>](cfenv.md), [\<cfloat>](cfloat.md), [\<cinttypes>](cinttypes.md), [\<ciso646>](ciso646.md), [\<climits>](climits.md), [\<clocale>](clocale.md), [\<cmath>](cmath.md), [\<csetjmp>](csetjmp.md), [\<csignal>](csignal.md), [\<cstdarg>](cstdarg.md), [\<cstdbool>](cstdbool.md), [\<cstddef>](cstddef.md), [\<cstdint>](cstdint.md), [\<cstdio>](cstdio.md), [\<cstdlib>](cstdlib.md), [\<cstring>](cstring.md), [\<ctgmath>](ctgmath.md), [\<ctime>](ctime.md), [\<cwchar>](cwchar.md), [\<cwctype>](cwctype.md)|
|[Kontenery](../cpp/containers-modern-cpp.md)||
|Kontenery sekwencji|[ Array\<>](array.md), [ deque>,forward_list>,list>,Vector>\<](deque.md) [ \<](forward-list.md) [ \<](list.md) [ \<](vector.md)|
|Uporządkowane Kontenery asocjacyjne| Mapuj >, [ \<](map.md) [ Ustaw>\<](set.md)|
|Nieuporządkowane Kontenery asocjacyjne|unordered_map >, [ \<](unordered-map.md) [ unordered_set>\<](unordered-set.md)|
|Kontenery adaptera|[\<queue>](queue.md), [\<stack>](stack.md)|
|[Błędy i obsługa wyjątków](../cpp/errors-and-exception-handling-modern-cpp.md)|wyjątek > [, stdexcept>\<](stdexcept.md), [ system_error\<>](system-error.md) [ \<](exception.md)|
|[We/wy i formatowanie](../cpp/string-and-i-o-formatting-modern-cpp.md)|[\<filesystem>](filesystem.md), [\<fstream>](fstream.md), [\<iomanip>](iomanip.md), [\<ios>](ios.md), [\<iosfwd>](iosfwd.md), [\<iostream>](iostream.md), [\<istream>](istream.md), [\<ostream>](ostream.md), [\<sstream>](sstream.md), [\<streambuf>](streambuf.md), [\<strstream>](strstream.md)|
|Iteratory|[\<iterator>](iterator.md)|
|Lokalizacja|[ \<](locale.md) [ codecvt>\<](cvt-wstring.md), [CVT/wbuffer >, CVT/wstring >, ustawienia regionalne > \<](cvt-wbuffer.md) [ \<](codecvt.md)|
|Obliczenia matematyczne i liczbowe|[ złożone>\<](ratio.md), [ limity\<>](limits.md), [ liczbowe\<>](numeric.md), [ \<losowe >](random.md), współczynnik > [ ,\<valarray >](valarray.md) [ \<](complex.md)|
|[Zarządzanie pamięcią](../cpp/smart-pointers-modern-cpp.md)|przypisania > [, >pamięci\<](memory.md), [ nowe\<>](new.md) [ \<](allocators-header.md) [scoped_allocator >\<](scoped-allocator.md)|
|Wielowątkowość|[ \<](future.md) [ \<](mutex.md) [ \<niepodzielna>, condition_variable >](condition-variable.md), przyszłość >, mutex >, [ \<shared_mutex >](shared-mutex.md), wątek [ \<](atomic.md) [ \< >](thread.md)|
|Inne narzędzia|[ bitset\<>](bitset.md), [ Chrono\<>](chrono.md) [, funkcjonalne\<>](functional.md) [, initializer_list\<>](initializer-list.md), [ krotka>,type_traits\<](tuple.md) [ \< >](type-traits.md) [ ,\<>](typeinfo.md) [, typeindex>,narzędzia>\<](typeindex.md) [ \<](utility.md)|
|Ciągi i dane znakowe|wyrażenie regularne >, [ \<String >](string.md), [ \<string_view >](string-view.md) [ \<](regex.md)

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Korzystanie C++ z nagłówków biblioteki](using-cpp-library-headers.md)\
[C++Biblioteka standardowa](cpp-standard-library-reference.md)
