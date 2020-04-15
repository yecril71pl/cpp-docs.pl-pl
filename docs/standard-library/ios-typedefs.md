---
title: '&lt;ios&gt; typedefs'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
ms.openlocfilehash: 0f63f65fb4c10fbe2ad538852222e6468b9061d0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375399"
---
# <a name="ltiosgt-typedefs"></a>&lt;ios&gt; typedefs

## <a name="ios"></a><a name="ios"></a>Ios

Obsługuje klasę ios ze starej biblioteki iostream.

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_ios,](../standard-library/basic-ios-class.md)wyspecjalizowane dla elementów **typu char** z domyślnymi cechami znaków.

## <a name="streamoff"></a><a name="streamoff"></a>streamoff

Obsługuje operacje wewnętrzne.

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>Uwagi

Typ jest podpisaną całkowitej liczby, która opisuje obiekt, który może przechowywać przesunięcie bajtu zaangażowanych w różnych operacji pozycjonowania strumienia. Jego reprezentacja ma co najmniej 32 bity wartości. Niekoniecznie jest wystarczająco duży, aby reprezentować dowolną pozycję bajtu w strumieniu. Wartość `streamoff(-1)` zazwyczaj wskazuje błędne przesunięcie.

## <a name="streampos"></a><a name="streampos"></a>streampos

Przechowuje bieżącą pozycję wskaźnika buforu lub wskaźnika pliku.

```cpp
typedef fpos<mbstate_t> streampos;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem [fpos](../standard-library/fpos-class.md) <  `mbstate_t`>.

### <a name="example"></a>Przykład

```cpp
// ios_streampos.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;

   ofstream x( "iostream.txt" );
   x << "testing";
   streampos y = x.tellp( );
   cout << y << endl;
}
```

```Output
7
```

## <a name="streamsize"></a><a name="streamsize"></a>rozmiar strumienia

Oznacza rozmiar strumienia.

```cpp
#ifdef _WIN64
    typedef __int64 streamsize;
#else
    typedef int streamsize;
#endif
```

### <a name="remarks"></a>Uwagi

Typ jest podpisaną liczbą całkowitą, która opisuje obiekt, który może przechowywać liczbę elementów zaangażowanych w różnych operacji strumienia. Jego reprezentacja ma co najmniej 16 bitów. Niekoniecznie jest wystarczająco duży, aby reprezentować dowolną pozycję bajtu w strumieniu.

### <a name="example"></a>Przykład

Po skompilowaniu i uruchomieniu następującego programu, spójrz na plik `streamsize`test.txt, aby zobaczyć efekt ustawienia .

```cpp
// ios_streamsize.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   char a[16] = "any such text";
   ofstream x( "test.txt" );
   streamsize y = 6;
   x.write( a, y );
}
```

## <a name="wios"></a><a name="wios"></a>wios

Obsługuje klasę wios ze starej biblioteki iostream.

```cpp
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem szablonu klasy [basic_ios,](../standard-library/basic-ios-class.md)wyspecjalizowanym dla elementów typu **wchar_t** z domyślnymi cechami znaków.

## <a name="wstreampos"></a><a name="wstreampos"></a>wstreampos

Przechowuje bieżącą pozycję wskaźnika buforu lub wskaźnika pliku.

```cpp
typedef fpos<mbstate_t> wstreampos;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem [fpos](../standard-library/fpos-class.md) <  `mbstate_t`>.

### <a name="example"></a>Przykład

```cpp
// ios_wstreampos.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   wofstream xw( "wiostream.txt" );
   xw << L"testing";
   wstreampos y = xw.tellp( );
   cout << y << endl;
}
```

```Output
7
```
