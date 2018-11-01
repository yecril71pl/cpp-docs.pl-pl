---
title: '&lt;IOS&gt; definicje typów'
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::ios
- iosfwd/std::streamoff
- iosfwd/std::streampos
- iosfwd/std::streamsize
- iosfwd/std::wios
- iosfwd/std::wstreampos
ms.assetid: 0b962632-3439-44de-bf26-20c67a7f0ff3
ms.openlocfilehash: 1f0ff93c22263ca4b35377b5d9af089816e8895a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537114"
---
# <a name="ltiosgt-typedefs"></a>&lt;IOS&gt; definicje typów

||||
|-|-|-|
|[dla systemu IOS](#ios)|[streamoff](#streamoff)|[streampos](#streampos)|
|[streamsize](#streamsize)|[wios](#wios)|[wstreampos](#wstreampos)|

## <a name="ios"></a>  dla systemu IOS

Obsługuje klasy dla systemu ios ze starego biblioteką iostream.

```cpp
typedef basic_ios<char, char_traits<char>> ios;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_ios —](../standard-library/basic-ios-class.md), wyspecjalizowany dla elementów typu **char** przy użyciu domyślnego cech.

## <a name="streamoff"></a>  streamoff

Obsługuje operacje wewnętrznego.

```cpp
#ifdef _WIN64
    typedef __int64 streamoff;
#else
    typedef long streamoff;
#endif
```

### <a name="remarks"></a>Uwagi

Typ jest liczba całkowita opisująca obiekt, które mogą być przechowywane w strumieniu różnych operacji pozycjonowania liczbę bajtów względem zaangażowane. Jej reprezentacji ma co najmniej 32 bity wartości. Nie jest musi być wystarczająco duży, aby reprezentować pozycji dowolnego bajtów w strumieniu. Wartość `streamoff(-1)` na ogół wskazuje przesunięcie błędne.

## <a name="streampos"></a>  streampos

Zawiera bieżącą pozycję wskaźnika buforu lub wskaźnika pliku.

```cpp
typedef fpos<mbstate_t> streampos;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla [fpos —](../standard-library/fpos-class.md)< `mbstate_t`>.

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

## <a name="streamsize"></a>  streamsize

Wskazuje, że rozmiar strumienia.

```cpp
#ifdef _WIN64
    typedef __int64 streamsize;
#else
    typedef int streamsize;
#endif
```

### <a name="remarks"></a>Uwagi

Typ jest liczba całkowita opisująca obiekt, które mogą być przechowywane liczbę elementów zaangażowanych w różne operacje na strumieniach. Jej reprezentacji ma co najmniej 16 bitów. Nie jest musi być wystarczająco duży, aby reprezentować pozycji dowolnego bajtów w strumieniu.

### <a name="example"></a>Przykład

Po kompilacji i uruchomienia następującego programu Przyjrzyj się jako plik, aby zobaczyć efekt ustawienie `streamsize`.

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

## <a name="wios"></a>  wios

Obsługuje klasy wios ze starego biblioteką iostream.

```cpp
typedef basic_ios<wchar_t, char_traits<wchar_t>> wios;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla szablonu klasy [basic_ios —](../standard-library/basic-ios-class.md), wyspecjalizowany dla elementów typu **wchar_t** przy użyciu domyślnego cech.

## <a name="wstreampos"></a>  wstreampos

Zawiera bieżącą pozycję wskaźnika buforu lub wskaźnika pliku.

```cpp
typedef fpos<mbstate_t> wstreampos;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla [fpos —](../standard-library/fpos-class.md)< `mbstate_t`>.

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

## <a name="see-also"></a>Zobacz także

[\<IOS >](../standard-library/ios.md)<br/>
