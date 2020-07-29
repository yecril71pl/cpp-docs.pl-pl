---
title: '&lt;elementy &gt; typedef systemu iOS'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
ms.openlocfilehash: 6167856c579acfca2bde600b2dd4d457199cafcc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87212283"
---
# <a name="ltiosgt-typedefs"></a>&lt;elementy &gt; typedef systemu iOS

## <a name="ios"></a><a name="ios"></a>wykonane

Obsługuje klasę systemu iOS ze starej biblioteki iostream.

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_ios](../standard-library/basic-ios-class.md), wyspecjalizowany dla elementów typu **`char`** z cechami domyślnymi znaków.

## <a name="streamoff"></a><a name="streamoff"></a>streamoff —

Obsługuje operacje wewnętrzne.

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>Uwagi

Typ to liczba całkowita ze znakiem, która opisuje obiekt, który może przechowywać przesunięcie bajtów związane z różnymi operacjami pozycjonowania strumienia. Jego reprezentacja ma co najmniej 32 bitów wartości. Nie musi być wystarczająco duże, aby reprezentować dowolną pozycję bajtową w strumieniu. Wartość `streamoff(-1)` zwykle wskazuje błędne przesunięcie.

## <a name="streampos"></a><a name="streampos"></a>streampos

Przechowuje bieżącą pozycję wskaźnika buforu lub wskaźnika pliku.

```cpp
typedef fpos<mbstate_t> streampos;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla [fpos](../standard-library/fpos-class.md) <  `mbstate_t`>.

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

## <a name="streamsize"></a><a name="streamsize"></a>dane StreamSize

Określa rozmiar strumienia.

```cpp
#ifdef _WIN64
    typedef __int64 streamsize;
#else
    typedef int streamsize;
#endif
```

### <a name="remarks"></a>Uwagi

Typ to liczba całkowita ze znakiem, która opisuje obiekt, który może przechowywać liczbę elementów występujących w różnych operacjach strumienia. Jego reprezentacja ma co najmniej 16 bitów. Nie musi być wystarczająco duże, aby reprezentować dowolną pozycję bajtową w strumieniu.

### <a name="example"></a>Przykład

Po skompilowaniu i uruchomieniu następującego programu Przyjrzyj się test.txt pliku, aby zobaczyć efekt ustawienia `streamsize` .

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

Typ jest synonimem dla szablonu klasy [basic_ios](../standard-library/basic-ios-class.md), wyspecjalizowany dla elementów typu **`wchar_t`** z cechami domyślnymi znaków.

## <a name="wstreampos"></a><a name="wstreampos"></a>wstreampos

Przechowuje bieżącą pozycję wskaźnika buforu lub wskaźnika pliku.

```cpp
typedef fpos<mbstate_t> wstreampos;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla [fpos](../standard-library/fpos-class.md) <  `mbstate_t`>.

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
