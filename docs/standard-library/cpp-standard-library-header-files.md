---
title: Pliki nagłówkowe standardowej biblioteki języka C++
ms.date: 07/12/2019
helpviewer_keywords:
- header files, C++ Standard Library
- C++ Standard Library, header files
ms.assetid: e7bf497a-0f63-48d0-9b54-cb0eef4073c4
ms.openlocfilehash: 207e7b7d2d689d3912399e3a867102ee893e003a
ms.sourcegitcommit: 1a8fac06478da8bee1f6d70e25afbad94144af1a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/30/2020
ms.locfileid: "84226042"
---
# <a name="c-standard-library-header-files"></a>Pliki nagłówkowe standardowej biblioteki języka C++

Pliki nagłówkowe dla standardowej biblioteki i rozszerzeń języka C++ według kategorii.

## <a name="headers-by-category"></a>Nagłówki według kategorii

::: moniker range=">=vs-2017"

| Kategoria | Nagłówki |
| - | - |
| [Algorytmy](../cpp/algorithms-modern-cpp.md) | [\<algorithm>](algorithm.md), [\<cstdlib>](cstdlib.md), [\<numeric>](numeric.md) |
| Operacje niepodzielne |  [\<atomic>](atomic.md)<sup>11</sup> |
| Otoki biblioteki C | [\<cassert>](cassert.md), [\<ccomplex>](ccomplex.md) <sup>11 a b</sup>, [\<cctype>](cctype.md) , [\<cerrno>](cerrno.md) , [\<cfenv>](cfenv.md) <sup>11</sup>, [\<cfloat>](cfloat.md) , [\<cinttypes>](cinttypes.md) <sup>11</sup>, [\<ciso646>](ciso646.md) <sup>b</sup>, [\<climits>](climits.md) , [\<clocale>](clocale.md) ,,, [\<cmath>](cmath.md) [\<csetjmp>](csetjmp.md) [\<csignal>](csignal.md) , [\<cstdalign>](cstdalign.md) <sup>11 a b</sup>, [\<cstdarg>](cstdarg.md) , [\<cstdbool>](cstdbool.md) <sup>11 a b</sup>, [\<cstddef>](cstddef.md) , [\<cstdint>](cstdint.md) <sup>11</sup>, [\<cstdio>](cstdio.md) , [\<cstdlib>](cstdlib.md) , [\<cstring>](cstring.md) , [\<ctgmath>](ctgmath.md) <sup>11 a b</sup>, [\<ctime>](ctime.md) , [\<cuchar>](cuchar.md) <sup>11</sup>, [\<cwchar>](cwchar.md) ,[\<cwctype>](cwctype.md) |
| Pojęcia | \<concepts><sup>20C</sup> |
| [Containers](../cpp/containers-modern-cpp.md) | |
| Kontenery sekwencji | [\<array>](array.md)<sup>11</sup>, [\<deque>](deque.md) , [\<forward_list>](forward-list.md) <sup>11</sup>, [\<list>](list.md) ,[\<vector>](vector.md) |
| Uporządkowane Kontenery asocjacyjne| [\<map>](map.md), [\<set>](set.md) |
| Nieuporządkowane Kontenery asocjacyjne | [\<unordered_map>](unordered-map.md)<sup>11</sup>, [\<unordered_set>](unordered-set.md) <sup>11</sup> |
| Adaptery kontenerów | [\<queue>](queue.md), [\<stack>](stack.md) |
| Widoki kontenerów | [\<span>](span.md)<sup>20C</sup> |
| [Błędy i obsługa wyjątków](../cpp/errors-and-exception-handling-modern-cpp.md) | [\<cassert>](cassert.md), [\<exception>](exception.md) , [\<stdexcept>](stdexcept.md) , [\<system_error>](system-error.md) <sup>11</sup> |
| Narzędzia ogólne | \<any><sup>17</sup>, [\<bitset>](bitset.md) , \<charconv> <sup>17</sup>, [\<cstdlib>](cstdlib.md) , \<execution> <sup>17</sup>, [\<functional>](functional.md) , [\<memory>](memory.md) , \<memory_resource> <sup>17</sup>, \<optional> <sup>17</sup>, [\<ratio>](ratio.md) <sup>11</sup>, [\<scoped_allocator>](scoped-allocator.md) <sup>11</sup>, [\<tuple>](tuple.md) <sup>11</sup>, [\<type_traits>](type-traits.md) <sup>11</sup>, [\<typeindex>](typeindex.md) <sup>11</sup>, [\<utility>](utility.md) , \<variant> <sup>17</sup> |
| [We/wy i formatowanie](../text/string-and-i-o-formatting-modern-cpp.md) | [\<cinttypes>](cinttypes.md)<sup>11</sup>, [\<cstdio>](cstdio.md) , [\<filesystem>](filesystem.md) <sup>17</sup>,,,,,,,,, [\<fstream>](fstream.md) [\<iomanip>](iomanip.md) [\<ios>](ios.md) [\<iosfwd>](iosfwd.md) [\<iostream>](iostream.md) [\<istream>](istream.md) [\<ostream>](ostream.md) [\<sstream>](sstream.md) [\<streambuf>](streambuf.md) , [\<strstream>](strstream.md) <sup>c</sup>, \<syncstream> <sup>20</sup> |
| Iteratory | [\<iterator>](iterator.md) |
| Obsługa języków | [\<cfloat>](cfloat.md), [\<climits>](climits.md) , [\<codecvt>](codecvt.md) <sup>11 a</sup>, \<compare> <sup>20</sup>, \<contract> <sup>20</sup>, \<coroutine> <sup>20</sup>, [\<csetjmp>](csetjmp.md) ,,, [\<csignal>](csignal.md) [\<cstdarg>](cstdarg.md) [\<cstddef>](cstddef.md) , [\<cstdint>](cstdint.md) <sup>11</sup>, [\<cstdlib>](cstdlib.md) , [\<exception>](exception.md) , [\<initializer_list>](initializer-list.md) <sup>11</sup>, [\<limits>](limits.md) , [\<new>](new.md) , [\<typeinfo>](typeinfo.md) , \<version> <sup>20</sup> |
| Lokalizacja | [\<clocale>](clocale.md), [\<codecvt>](codecvt.md) <sup>11 a</sup>, [\<cvt/wbuffer>](cvt-wbuffer.md) , [\<cvt/wstring>](cvt-wstring.md) ,[\<locale>](locale.md) |
| Obliczenia matematyczne i liczbowe | \<bit><sup>20</sup>, [\<cfenv>](cfenv.md) <sup>11</sup>, [\<cmath>](cmath.md) ,,,,, [\<complex>](complex.md) [\<cstdlib>](cstdlib.md) [\<limits>](limits.md) [\<numeric>](numeric.md) [\<random>](random.md) <sup>11</sup>, [\<ratio>](ratio.md) <sup>11</sup>,[\<valarray>](valarray.md) |
| [Zarządzanie pamięcią](../cpp/smart-pointers-modern-cpp.md) | [\<allocators>](allocators-header.md), [\<memory>](memory.md) , \<memory_resource> <sup>17</sup>, [\<new>](new.md) , [\<scoped_allocator>](scoped-allocator.md) <sup>11</sup> |
| Wielowątkowość | [\<atomic>](atomic.md)<sup>11</sup>, [\<condition_variable>](condition-variable.md) <sup>11</sup>, [\<future>](future.md) <sup>11</sup>, [\<mutex>](mutex.md) <sup>11</sup>, [\<shared_mutex>](shared-mutex.md) <sup>14</sup>, [\<thread>](thread.md) <sup>11</sup> |
| Zakresy | \<ranges><sup>20C</sup> |
| Wyrażenia regularne | [\<regex>](regex.md)<sup>11</sup> |
| Ciągi i dane znakowe | [\<cctype>](cctype.md), [\<cstdlib>](cstdlib.md) , [\<cstring>](cstring.md) , [\<cuchar>](cuchar.md) <sup>11</sup>, [\<cwchar>](cwchar.md) , [\<cwctype>](cwctype.md) , [\<regex>](regex.md) <sup>11</sup>, [\<string>](string.md) , [\<string_view>](string-view.md) <sup>17</sup> |
| Godzina | [\<chrono>](chrono.md)<sup>11</sup>,[\<ctime>](ctime.md) |

<sup>11</sup> dodano w standardzie c++ 11. \
<sup>14</sup> dodano w standardzie c++ 14. \
<sup>17</sup> dodano w standardzie c++ 17. \
<sup>20</sup> dodano w wersji próbnej standardu c++ 20. \
<sup>przestarzałe</sup> w standardzie c++ 17. \
<sup>b</sup> usunięto w wersji próbnej standardu c++ 20. \
język <sup>c</sup> jest przestarzały w standardzie c++ 98.

::: moniker-end

::: moniker range="vs-2015"

|Kategoria|Nagłówki|
|-|-|
|[Algorytmy](../cpp/algorithms-modern-cpp.md)|[\<algorithm>](algorithm.md)|
|Otoki biblioteki C|[\<cassert>](cassert.md), [\<cctype>](cctype.md), [\<cerrno>](cerrno.md), [\<cfenv>](cfenv.md), [\<cfloat>](cfloat.md), [\<cinttypes>](cinttypes.md), [\<ciso646>](ciso646.md), [\<climits>](climits.md), [\<clocale>](clocale.md), [\<cmath>](cmath.md), [\<csetjmp>](csetjmp.md), [\<csignal>](csignal.md), [\<cstdarg>](cstdarg.md), [\<cstdbool>](cstdbool.md), [\<cstddef>](cstddef.md), [\<cstdint>](cstdint.md), [\<cstdio>](cstdio.md), [\<cstdlib>](cstdlib.md), [\<cstring>](cstring.md), [\<ctgmath>](ctgmath.md), [\<ctime>](ctime.md), [\<cwchar>](cwchar.md), [\<cwctype>](cwctype.md)|
|[Containers](../cpp/containers-modern-cpp.md)||
|Kontenery sekwencji|[\<array>](array.md), [\<deque>](deque.md), [\<forward_list>](forward-list.md), [\<list>](list.md), [\<vector>](vector.md)|
|Uporządkowane Kontenery asocjacyjne| [\<map>](map.md), [\<set>](set.md)|
|Nieuporządkowane Kontenery asocjacyjne|[\<unordered_map>](unordered-map.md), [\<unordered_set>](unordered-set.md)|
|Kontenery adaptera|[\<queue>](queue.md), [\<stack>](stack.md)|
|[Błędy i obsługa wyjątków](../cpp/errors-and-exception-handling-modern-cpp.md)|[\<exception>](exception.md), [\<stdexcept>](stdexcept.md), [\<system_error>](system-error.md)|
|[We/wy i formatowanie](../text/string-and-i-o-formatting-modern-cpp.md)|[\<filesystem>](filesystem.md), [\<fstream>](fstream.md), [\<iomanip>](iomanip.md), [\<ios>](ios.md), [\<iosfwd>](iosfwd.md), [\<iostream>](iostream.md), [\<istream>](istream.md), [\<ostream>](ostream.md), [\<sstream>](sstream.md), [\<streambuf>](streambuf.md), [\<strstream>](strstream.md)|
|Iteratory|[\<iterator>](iterator.md)|
|Lokalizacja|[\<codecvt>](codecvt.md), [\<cvt/wbuffer>](cvt-wbuffer.md), [\<cvt/wstring>](cvt-wstring.md), [\<locale>](locale.md)|
|Obliczenia matematyczne i liczbowe|[\<complex>](complex.md), [\<limits>](limits.md), [\<numeric>](numeric.md), [\<random>](random.md), [\<ratio>](ratio.md), [\<valarray>](valarray.md)|
|[Zarządzanie pamięcią](../cpp/smart-pointers-modern-cpp.md)|[\<allocators>](allocators-header.md), [\<memory>](memory.md), [\<new>](new.md), [\<scoped_allocator>](scoped-allocator.md)|
|Wielowątkowość|[\<atomic>](atomic.md), [\<condition_variable>](condition-variable.md), [\<future>](future.md), [\<mutex>](mutex.md), [\<shared_mutex>](shared-mutex.md), [\<thread>](thread.md)|
|Inne narzędzia|[\<bitset>](bitset.md), [\<chrono>](chrono.md), [\<functional>](functional.md), [\<initializer_list>](initializer-list.md), [\<tuple>](tuple.md), [\<type_traits>](type-traits.md), [\<typeinfo>](typeinfo.md), [\<typeindex>](typeindex.md), [\<utility>](utility.md)|
|Ciągi i dane znakowe|[\<regex>](regex.md), [\<string>](string.md), [\<string_view>](string-view.md)

::: moniker-end

## <a name="see-also"></a>Zobacz także

[Korzystanie z nagłówków biblioteki C++](using-cpp-library-headers.md)\
[Standardowa biblioteka C++](cpp-standard-library-reference.md)
