---
title: '&lt;iostream&gt;'
ms.date: 09/20/2017
f1_keywords:
- <iostream>
- iostream/std::cerr
- iostream/std::cin
- iostream/std::clog
- iostream/std::cout
- iostream/std::wcerr
- iostream/std::wcin
- iostream/std::wclog
- iostream/std::wcout
helpviewer_keywords:
- iostream header
ms.assetid: de5d39e1-7e77-4b55-bcd1-7c77b41515c8
ms.openlocfilehash: 5805d441b4fc2fc2927b57f4d94ba8b8ccecb22a
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845474"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

Deklaruje obiekty kontrolujące odczyt i zapis w standardowym strumieniu. Jest to często jedyny nagłówek, który jest potrzebny do wprowadzania danych wejściowych i wyjściowych z programu C++.

## <a name="syntax"></a>Składnia

```cpp
#include <iostream>
```

> [!NOTE]
> \<iostream>Biblioteka używa `#include <ios>` `#include <streambuf>` instrukcji,, `#include <istream>` , i `#include <ostream>` .

## <a name="remarks"></a>Uwagi

Obiekty mieszczą się w dwóch grupach:

- [CIN](#cin), [cout](#cout), [cerr](#cerr)i [CLOG](#clog) są zorientowane na bajty, co umożliwia transfer konwencjonalnych bajtów w czasie.

- [wcin](#wcin), [wcout](#wcout), [wcerr](#wcerr)i [wclog](#wclog) są zorientowane na szerokie, tłumaczenie na i od znaków dwubajtowych, które program operuje wewnętrznie.

Po wykonaniu pewnych operacji na strumieniu, takich jak standardowe dane wejściowe, nie można wykonać operacji o innej orientacji w tym samym strumieniu. W związku z tym program nie może działać zamiennie zarówno na [CIN](#cin) , jak i [wcin](#wcin), na przykład.

Wszystkie obiekty zadeklarowane w tym nagłówku współdzielą Właściwość szczególną — można założyć, że są one konstruowane przed zdefiniowanymi statycznymi obiektami w jednostce translacji, która zawiera \<iostream> . Równiej można założyć, że te obiekty nie są niszczone przed destruktorami dla wszystkich zdefiniowanych obiektów statycznych. (Strumienie wyjściowe są jednak opróżniane podczas kończenia działania programu). W związku z tym można bezpiecznie odczytywać i zapisywać strumienie standardowe przed uruchomieniem programu i po zakończeniu działania programu.

Ta gwarancja nie jest jednak uniwersalna. Konstruktor statyczny może wywołać funkcję w innej jednostce translacji. Wywołana funkcja nie może przyjąć, że obiekty zadeklarowane w tym nagłówku zostały skonstruowane, z uwzględnieniem niepewnej kolejności, w której jednostki translacji uczestniczą w konstrukcji statycznej. Aby użyć tych obiektów w tym kontekście, należy najpierw skonstruować obiekt klasy [ios_base:: init](../standard-library/ios-base-class.md#init).

### <a name="global-stream-objects"></a>Obiekty strumienia globalnego

|Nazwa|Opis|
|-|-|
|[cerr](#cerr)|Określa `cerr` strumień globalny.|
|[cin](#cin)|Określa `cin` strumień globalny.|
|[clog](#clog)|Określa `clog` strumień globalny.|
|[cout](#cout)|Określa `cout` strumień globalny.|
|[wcerr](#wcerr)|Określa `wcerr` strumień globalny.|
|[wcin](#wcin)|Określa `wcin` strumień globalny.|
|[wclog](#wclog)|Określa `wclog` strumień globalny.|
|[wcout](#wcout)|Określa `wcout` strumień globalny.|

### <a name="cerr"></a><a name="cerr"></a> cerr

Obiekt `cerr` kontroluje wyjście do bufora strumienia skojarzonego z obiektem `stderr` zadeklarowanym w \<cstdio> .

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [ostream](../standard-library/ostream-typedefs.md#ostream) .

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje niebuforowane wstawienia do standardowego wyjścia błędu jako strumień bajtów. Po skonstruowaniu obiektu wyrażenie `cerr.` [flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) ma wartość różną od zera i `cerr.tie() == &cout` .

#### <a name="example"></a>Przykład

```cpp
// iostream_cerr.cpp
// compile with: /EHsc
#include <iostream>
#include <fstream>

using namespace std;

void TestWide( )
{
   int i = 0;
   wcout << L"Enter a number: ";
   wcin >> i;
   wcerr << L"test for wcerr" << endl;
   wclog << L"test for wclog" << endl;
}

int main( )
{
   int i = 0;
   cout << "Enter a number: ";
   cin >> i;
   cerr << "test for cerr" << endl;
   clog << "test for clog" << endl;
   TestWide( );
}
```

### <a name="cin"></a><a name="cin"></a> cin

Określa `cin` strumień globalny.

```cpp
extern istream cin;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [IStream](../standard-library/istream-typedefs.md#istream) .

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje wyodrębnianie ze standardowego wejścia jako strumień bajtów. Gdy obiekt zostanie skonstruowany, wywołanie Call `cin.` [tie](../standard-library/basic-ios-class.md#tie) zwraca `&` [cout](#cout).

#### <a name="example"></a>Przykład

W tym przykładzie `cin` ustawia bit niepowodzenia w strumieniu, gdy zawiera on znaki niebędące cyframi. Program czyści bit błędu i przyłączy nieprawidłowy znak ze strumienia, aby kontynuować.

```cpp
// iostream_cin.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main()
{
   int x;
   cout << "enter choice:";
   cin >> x;
   while (x < 1 || x > 4)
   {
      cout << "Invalid choice, try again:";
      cin >> x;
      // not a numeric character, probably
      // clear the failure and pull off the non-numeric character
      if (cin.fail())
      {
         cin.clear();
         char c;
         cin >> c;
      }
   }
}
```

```Output
2
```

### <a name="clog"></a><a name="clog"></a> clog

Określa `clog` strumień globalny.

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [ostream](../standard-library/ostream-typedefs.md#ostream) .

#### <a name="remarks"></a>Uwagi

Obiekt steruje buforowanymi wstawieniami do standardowego wyjścia błędu jako strumień bajtów.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) , aby poznać przykład użycia `clog` .

### <a name="cout"></a><a name="cout"></a> cout

Określa `cout` strumień globalny.

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [ostream](../standard-library/ostream-typedefs.md#ostream) .

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje wstawienia do wyjścia standardowego jako strumień bajtów.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) , aby poznać przykład użycia `cout` .

### <a name="wcerr"></a><a name="wcerr"></a> wcerr

Określa `wcerr` strumień globalny.

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [wostream —](../standard-library/ostream-typedefs.md#wostream) .

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje niebuforowane wstawienia do standardowego wyjścia błędu jako strumień szeroki. Po skonstruowaniu obiektu wyrażenie `wcerr.` [flags](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) ma wartość różną od zera.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) , aby poznać przykład użycia `wcerr` .

### <a name="wcin"></a><a name="wcin"></a> wcin

Określa `wcin` strumień globalny.

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [wistream](../standard-library/istream-typedefs.md#wistream) .

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje wyodrębnianie ze standardowego wejścia jako strumień szeroki. Gdy obiekt zostanie skonstruowany, wywołanie Call `wcin.` [tie](../standard-library/basic-ios-class.md#tie) zwraca `&` [wcout](#wcout).

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) , aby poznać przykład użycia `wcin` .

### <a name="wclog"></a><a name="wclog"></a> wclog

Określa `wclog` strumień globalny.

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [wostream —](../standard-library/ostream-typedefs.md#wostream) .

#### <a name="remarks"></a>Uwagi

Obiekt steruje buforowanymi wstawieniami do standardowego wyjścia błędu jako strumień szeroki.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) , aby poznać przykład użycia `wclog` .

### <a name="wcout"></a><a name="wcout"></a> wcout

Określa `wcout` strumień globalny.

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [wostream —](../standard-library/ostream-typedefs.md#wostream) .

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje wstawienia do wyjścia standardowego jako strumień szeroki.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) , aby poznać przykład użycia `wcout` .

`CString` wystąpienia w `wcout` instrukcji muszą być rzutowane do `const wchar_t*` , jak pokazano w poniższym przykładzie.

```cpp
CString cs("meow");

wcout <<(const wchar_t*) cs <<endl;
```

Aby uzyskać więcej informacji, zobacz [podstawowe operacje CString](../atl-mfc-shared/basic-cstring-operations.md).

## <a name="see-also"></a>Zobacz też

[Dokumentacja plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostreams](../standard-library/iostreams-conventions.md)
