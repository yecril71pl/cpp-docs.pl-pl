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
ms.openlocfilehash: aabdc761cc55507f4718a63a0c082325ae1badf7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50504289"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

Deklaruje obiekty, które kontrolują odczytywanie z oraz zapisywanie do standardowych strumieni. Często jest tylko nagłówek, które trzeba uwzględnić wykonać wejście i wyjście z programu C++.

## <a name="syntax"></a>Składnia

```cpp
#include <iostream>

```

## <a name="remarks"></a>Uwagi

Obiekty można podzielić na dwie grupy:

- [CIN](#cin), [cout](#cout), [cerr](#cerr), i [clog —](#clog) są bajt obiektowo, konwencjonalne transferu bajtów w czasie wykonywania.

- [wcin](#wcin), [wcout](#wcout), [wcerr](#wcerr), i [wclog](#wclog) są szerokie ukierunkowane, tłumaczenia ze znaków dwubajtowych, które program manipuluje wewnętrznie.

Po wykonaniu pewnych operacji na strumieniu, takich jak standardowe dane wejściowe nie można wykonać operacji o innej orientacji tego samego strumienia. W związku z tym, program nie może działać zamiennie zarówno [cin](#cin) i [wcin](#wcin), na przykład.

Wszystkie obiekty zadeklarowanych w tym udziale nagłówka wspólnych właściwości, można założyć, które są zbudowane przed wszystkie obiekty statyczne można zdefiniować w jednostce translacji, która zawiera \<iostream >. Tak samo można założyć, że te obiekty nie są niszczone, przed destruktory dla takich statycznych obiektów, jaką zdefiniujesz. (Strumienie wyjściowe jednak opróżnione podczas Kończenie działania programu). W związku z tym można bezpiecznie odczytać lub zapisać do standardowych strumieni przed uruchomieniem programu i po zakończeniu programu.

Gwarancja nie jest uniwersalny, jednak. Statyczny Konstruktor może wywołać funkcję w innej jednostce translacji. Wywołana funkcja nie można zakładać, że obiekty zadeklarowane w tym nagłówku mają został skonstruowany, podane w nieokreślonej kolejności, w której tłumaczenia jednostki uczestniczyć w konstrukcji statyczne. W takiej sytuacji należy używać tych obiektów, należy najpierw utworzyć obiekt klasy [ios_base::Init](../standard-library/ios-base-class.md#init).

### <a name="global-stream-objects"></a>Obiekty globalne Stream

|||
|-|-|
|[cerr](#cerr)|Określa `cerr` globalnego strumienia.|
|[cin](#cin)|Określa `cin` globalnego strumienia.|
|[clog](#clog)|Określa `clog` globalnego strumienia.|
|[Cout](#cout)|Określa `cout` globalnego strumienia.|
|[wcerr](#wcerr)|Określa `wcerr` globalnego strumienia.|
|[wcin](#wcin)|Określa `wcin` globalnego strumienia.|
|[wclog](#wclog)|Określa `wclog` globalnego strumienia.|
|[wcout](#wcout)|Określa `wcout` globalnego strumienia.|

###  <a name="cerr"></a>  cerr

Obiekt `cerr` kontroluje dane wyjściowe do bufora strumienia, skojarzony z obiektem `stderr`, zadeklarowanych w \<cstdio — >.

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>Wartość zwracana

[Ostream](../standard-library/ostream-typedefs.md#ostream) obiektu.

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje Niebuforowane wstawiania do danych wyjściowych błędu standardowego jako strumień bajtów. Gdy obiekt jest konstruowany, wyrażenie `cerr.` [flagi](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) jest różna od zera, a `cerr.tie() == &cout`.

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

###  <a name="cin"></a>  CIN

Określa `cin` globalnego strumienia.

```cpp
extern istream cin;
```

#### <a name="return-value"></a>Wartość zwracana

[Istream](../standard-library/istream-typedefs.md#istream) obiektu.

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje wyodrębniania ze standardowego wejścia jako strumień bajtów. Gdy obiekt jest konstruowany, wywołanie `cin.` [powiązanie](../standard-library/basic-ios-class.md#tie) zwraca `&` [cout](#cout).

#### <a name="example"></a>Przykład

W tym przykładzie `cin` ustawia kończyć się niepowodzeniem, bit w strumieniu po napotkaniu znaków nienumerycznych. Program czyści kończyć się niepowodzeniem i paski nieprawidłowy znak ze strumienia, aby kontynuować.

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

###  <a name="clog"></a>  clog

Określa `clog` globalnego strumienia.

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>Wartość zwracana

[Ostream](../standard-library/ostream-typedefs.md#ostream) obiektu.

#### <a name="remarks"></a>Uwagi

Formanty obiektu buforowana wstawiania do danych wyjściowych błędu standardowego jako strumień bajtów.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) na przykład za pomocą `clog`.

###  <a name="cout"></a>  Cout

Określa `cout` globalnego strumienia.

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>Wartość zwracana

[Ostream](../standard-library/ostream-typedefs.md#ostream) obiektu.

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje wstawień do wyjścia standardowego jako strumień bajtów.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) na przykład za pomocą `cout`.

###  <a name="wcerr"></a>  wcerr

Określa `wcerr` globalnego strumienia.

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>Wartość zwracana

A [wostream](../standard-library/ostream-typedefs.md#wostream) obiektu.

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje Niebuforowane wstawiania do danych wyjściowych błędu standardowego jako strumień szerokości. Gdy obiekt jest konstruowany, wyrażenie `wcerr.` [flagi](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) jest różna od zera.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) na przykład za pomocą `wcerr`.

###  <a name="wcin"></a>  wcin

Określa `wcin` globalnego strumienia.

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>Wartość zwracana

A [wistream](../standard-library/istream-typedefs.md#wistream) obiektu.

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje wyodrębniania ze standardowego wejścia jako strumień szerokości. Gdy obiekt jest konstruowany, wywołanie `wcin.` [powiązanie](../standard-library/basic-ios-class.md#tie) zwraca `&` [wcout](#wcout).

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) na przykład za pomocą `wcin`.

###  <a name="wclog"></a>  wclog

Określa `wclog` globalnego strumienia.

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>Wartość zwracana

A [wostream](../standard-library/ostream-typedefs.md#wostream) obiektu.

#### <a name="remarks"></a>Uwagi

Formanty obiektu buforowana wstawiania do danych wyjściowych błędu standardowego jako strumień szerokości.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) na przykład za pomocą `wclog`.

###  <a name="wcout"></a>  wcout

Określa `wcout` globalnego strumienia.

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>Wartość zwracana

A [wostream](../standard-library/ostream-typedefs.md#wostream) obiektu.

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje wstawień do wyjścia standardowego jako strumień szerokości.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) na przykład za pomocą `wcout`.

`CString` wystąpienia w `wcout` instrukcji należy zrzutować do `const wchar_t*`, jak pokazano w poniższym przykładzie.

```

    CString cs("meow");

    wcout <<(const wchar_t*) cs <<endl;
```

Aby uzyskać więcej informacji, zobacz [podstawowe operacje na obiekcie CString](../atl-mfc-shared/basic-cstring-operations.md).

## <a name="see-also"></a>Zobacz także

[Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
