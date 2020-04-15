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
ms.openlocfilehash: 03afb777dc3926284cf0dc625e94a716ecdf5413
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375346"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

Deklaruje obiekty, które kontrolują odczyt i zapis do standardowych strumieni. Obejmuje to często jest tylko nagłówek, który należy wykonać dane wejściowe i wyjściowe z programu C++.

## <a name="syntax"></a>Składnia

```cpp
#include <iostream>
```

> [!NOTE]
> Biblioteka \<> iostream `#include <ios>`używa , `#include <streambuf>`, `#include <istream>`i `#include <ostream>` instrukcji.

## <a name="remarks"></a>Uwagi

Obiekty dzielą się na dwie grupy:

- [cin](#cin), [cout](#cout), [cerr](#cerr), i [zatykać](#clog) są zorientowane bajt, wykonując konwencjonalne transfery bajtów na czas.

- [wcin](#wcin), [wcout](#wcout), [wcerr](#wcerr)i [wclog](#wclog) są szeroko zorientowane, tłumacząc na szerokie znaki, którymi program manipuluje wewnętrznie.

Po wykonania niektórych operacji w strumieniu, takich jak standardowe dane wejściowe, nie można wykonać operacje o innej orientacji na tym samym strumieniu. Dlatego program nie może działać zamiennie zarówno na [cin](#cin) i [wcin](#wcin), na przykład.

Wszystkie obiekty zadeklarowane w tym nagłówku współużytkują właściwość — można założyć, że są \<one skonstruowane przed zdefiniowanymi obiektami statycznymi w jednostce tłumaczenia, która zawiera> iostream. Podobnie można założyć, że te obiekty nie są niszczone przed destruktorów dla takich obiektów statycznych, które można zdefiniować. (Strumienie wyjściowe są jednak opróżniane podczas zakończenia programu). W związku z tym można bezpiecznie odczytać lub zapisać do standardowych strumieni przed uruchomieniem programu i po zakończeniu programu.

Gwarancja ta nie jest jednak uniwersalna. Konstruktor statyczny może wywołać funkcję w innej jednostce tłumaczenia. Wywołana funkcja nie może zakładać, że obiekty zadeklarowane w tym nagłówku zostały skonstruowane, biorąc pod uwagę niepewną kolejność, w jakiej jednostki translacji uczestniczą w konstrukcji statycznej. Aby użyć tych obiektów w takim kontekście, należy najpierw skonstruować obiekt klasy [ios_base::Init](../standard-library/ios-base-class.md#init).

### <a name="global-stream-objects"></a>Obiekty strumienia globalnego

|||
|-|-|
|[cerr](#cerr)|Określa strumień `cerr` globalny.|
|[Cin](#cin)|Określa strumień `cin` globalny.|
|[Zatyka](#clog)|Określa strumień `clog` globalny.|
|[Cout](#cout)|Określa strumień `cout` globalny.|
|[wcerr](#wcerr)|Określa strumień `wcerr` globalny.|
|[wcin (wcin)](#wcin)|Określa strumień `wcin` globalny.|
|[wclog](#wclog)|Określa strumień `wclog` globalny.|
|[wcout](#wcout)|Określa strumień `wcout` globalny.|

### <a name="cerr"></a><a name="cerr"></a>cerr

Obiekt `cerr` steruje wyjściem do buforu `stderr`strumienia \<skojarzonego z obiektem , zadeklarowanym w cstdio>.

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [ostream.](../standard-library/ostream-typedefs.md#ostream)

#### <a name="remarks"></a>Uwagi

Obiekt steruje niebuforowanymi wstawieniami do standardowego wyjścia błędu jako strumienia bajtów. Po skonstruowaniu `cerr.`obiektu wyrażenie [flaguje](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) jest niezerowy i `cerr.tie() == &cout`.

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

### <a name="cin"></a><a name="cin"></a>Cin

Określa strumień `cin` globalny.

```cpp
extern istream cin;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [istream.](../standard-library/istream-typedefs.md#istream)

#### <a name="remarks"></a>Uwagi

Obiekt steruje wyodrębnianiami ze standardowego wejścia jako strumień bajtów. Po skonstruowaniu `cin.` [obiektu, wywołanie](../standard-library/basic-ios-class.md#tie) `&`krawat zwraca [cout](#cout).

#### <a name="example"></a>Przykład

W tym `cin` przykładzie ustawia bit fail na strumieniu, gdy występuje między znakami nienukrajowymi. Program czyści bit niepowodzenia i usuwa nieprawidłowy znak ze strumienia, aby kontynuować.

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

### <a name="clog"></a><a name="clog"></a>Zatyka

Określa strumień `clog` globalny.

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [ostream.](../standard-library/ostream-typedefs.md#ostream)

#### <a name="remarks"></a>Uwagi

Obiekt steruje buforowanymi wstawieniami do standardowego wyjścia błędu jako strumienia bajtów.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) na przykład `clog`za pomocą .

### <a name="cout"></a><a name="cout"></a>Cout

Określa strumień `cout` globalny.

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [ostream.](../standard-library/ostream-typedefs.md#ostream)

#### <a name="remarks"></a>Uwagi

Obiekt steruje wstawieniami do standardowego wyjścia jako strumień bajtów.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) na przykład `cout`za pomocą .

### <a name="wcerr"></a><a name="wcerr"></a>wcerr

Określa strumień `wcerr` globalny.

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [wostream.](../standard-library/ostream-typedefs.md#wostream)

#### <a name="remarks"></a>Uwagi

Obiekt steruje niebuforowanymi wstawieniami do standardowego wyjścia błędu jako szeroki strumień. Po zbudowaniu obiektu wyrażenie `wcerr.` [flaguje](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) jest niezerowy.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) na przykład `wcerr`za pomocą .

### <a name="wcin"></a><a name="wcin"></a>wcin (wcin)

Określa strumień `wcin` globalny.

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [wistream.](../standard-library/istream-typedefs.md#wistream)

#### <a name="remarks"></a>Uwagi

Obiekt steruje ekstrakcjami ze standardowego wejścia jako szeroki strumień. Po skonstruowaniu `wcin.` [obiektu, połączenie](../standard-library/basic-ios-class.md#tie) wywołania zwraca `&` [wcout](#wcout).

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) na przykład `wcin`za pomocą .

### <a name="wclog"></a><a name="wclog"></a>wclog

Określa strumień `wclog` globalny.

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [wostream.](../standard-library/ostream-typedefs.md#wostream)

#### <a name="remarks"></a>Uwagi

Obiekt steruje buforowanymi wstawieniami do standardowego wyjścia błędu jako szeroki strumień.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) na przykład `wclog`za pomocą .

### <a name="wcout"></a><a name="wcout"></a>wcout

Określa strumień `wcout` globalny.

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [wostream.](../standard-library/ostream-typedefs.md#wostream)

#### <a name="remarks"></a>Uwagi

Obiekt steruje wstawieniami do standardowego wyjścia jako szeroki strumień.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) na przykład `wcout`za pomocą .

`CString`instancje `wcout` w instrukcji muszą `const wchar_t*`być rzutowe do , jak pokazano w poniższym przykładzie.

```cpp
CString cs("meow");

wcout <<(const wchar_t*) cs <<endl;
```

Aby uzyskać więcej informacji, zobacz [Podstawowe operacje cstring](../atl-mfc-shared/basic-cstring-operations.md).

## <a name="see-also"></a>Zobacz też

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
