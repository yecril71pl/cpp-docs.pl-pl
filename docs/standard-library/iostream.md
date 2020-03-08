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
ms.openlocfilehash: 2906e802072c43a93c59ca40d15e032adeeeef97
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2020
ms.locfileid: "78856544"
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;

Deklaruje obiekty kontrolujące odczyt i zapis w standardowym strumieniu. Jest to często jedyny nagłówek, który jest potrzebny do wprowadzania danych wejściowych i wyjściowych C++ z programu.

## <a name="syntax"></a>Składnia

```cpp
#include <iostream>
```

> [!NOTE]
> Biblioteka \<iostream > używa instrukcji `#include <ios>`, `#include <streambuf>`, `#include <istream>`i `#include <ostream>`.

## <a name="remarks"></a>Uwagi

Obiekty mieszczą się w dwóch grupach:

- [CIN](#cin), [cout](#cout), [cerr](#cerr)i [CLOG](#clog) są zorientowane na bajty, co umożliwia transfer konwencjonalnych bajtów w czasie.

- [wcin](#wcin), [wcout](#wcout), [wcerr](#wcerr)i [wclog](#wclog) są zorientowane na szerokie, tłumaczenie na i od znaków dwubajtowych, które program operuje wewnętrznie.

Po wykonaniu pewnych operacji na strumieniu, takich jak standardowe dane wejściowe, nie można wykonać operacji o innej orientacji w tym samym strumieniu. W związku z tym program nie może działać zamiennie zarówno na [CIN](#cin) , jak i [wcin](#wcin), na przykład.

Wszystkie obiekty zadeklarowane w tym nagłówku współdzielą Właściwość specyficzną — można założyć, że są one konstruowane przed zdefiniowanymi statycznymi obiektami, w jednostce translacji, która zawiera \<iostream >. Równiej można założyć, że te obiekty nie są niszczone przed destruktorami dla wszystkich zdefiniowanych obiektów statycznych. (Strumienie wyjściowe są jednak opróżniane podczas kończenia działania programu). W związku z tym można bezpiecznie odczytywać i zapisywać strumienie standardowe przed uruchomieniem programu i po zakończeniu działania programu.

Ta gwarancja nie jest jednak uniwersalna. Konstruktor statyczny może wywołać funkcję w innej jednostce translacji. Wywołana funkcja nie może przyjąć, że obiekty zadeklarowane w tym nagłówku zostały skonstruowane, z uwzględnieniem niepewnej kolejności, w której jednostki translacji uczestniczą w konstrukcji statycznej. Aby użyć tych obiektów w tym kontekście, należy najpierw skonstruować obiekt klasy [ios_base:: init](../standard-library/ios-base-class.md#init).

### <a name="global-stream-objects"></a>Obiekty strumienia globalnego

|||
|-|-|
|[cerr](#cerr)|Określa `cerr` strumienia globalnego.|
|[cin](#cin)|Określa `cin` strumienia globalnego.|
|[clog](#clog)|Określa `clog` strumienia globalnego.|
|[cout](#cout)|Określa `cout` strumienia globalnego.|
|[wcerr](#wcerr)|Określa `wcerr` strumienia globalnego.|
|[wcin](#wcin)|Określa `wcin` strumienia globalnego.|
|[wclog](#wclog)|Określa `wclog` strumienia globalnego.|
|[wcout](#wcout)|Określa `wcout` strumienia globalnego.|

###  <a name="cerr"></a>cerr

Obiekt `cerr` kontroluje dane wyjściowe do bufora strumienia skojarzonego z `stderr`obiektu, zadeklarowane w \<cstdio >.

```cpp
extern ostream cerr;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [ostream](../standard-library/ostream-typedefs.md#ostream) .

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje niebuforowane wstawienia do standardowego wyjścia błędu jako strumień bajtów. Po utworzeniu obiektu wyrażenie `cerr.`[flagi](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) ma wartość różną od zera i `cerr.tie() == &cout`.

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

###  <a name="cin"></a>cin

Określa `cin` strumienia globalnego.

```cpp
extern istream cin;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [IStream](../standard-library/istream-typedefs.md#istream) .

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje wyodrębnianie ze standardowego wejścia jako strumień bajtów. Gdy obiekt zostanie skonstruowany, wywołanie `cin.`[krawat](../standard-library/basic-ios-class.md#tie) zwraca `&`[cout](#cout).

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

###  <a name="clog"></a>clog

Określa `clog` strumienia globalnego.

```cpp
extern ostream clog;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [ostream](../standard-library/ostream-typedefs.md#ostream) .

#### <a name="remarks"></a>Uwagi

Obiekt steruje buforowanymi wstawieniami do standardowego wyjścia błędu jako strumień bajtów.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) , aby zapoznać się z przykładem korzystania z `clog`.

###  <a name="cout"></a>cout

Określa `cout` strumienia globalnego.

```cpp
extern ostream cout;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [ostream](../standard-library/ostream-typedefs.md#ostream) .

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje wstawienia do wyjścia standardowego jako strumień bajtów.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) , aby zapoznać się z przykładem korzystania z `cout`.

### <a name="wcerr"></a>wcerr

Określa `wcerr` strumienia globalnego.

```cpp
extern wostream wcerr;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [wostream —](../standard-library/ostream-typedefs.md#wostream) .

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje niebuforowane wstawienia do standardowego wyjścia błędu jako strumień szeroki. Po utworzeniu obiektu wyrażenie `wcerr.`[flag](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) ma wartość różną od zera.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) , aby zapoznać się z przykładem korzystania z `wcerr`.

### <a name="wcin"></a>wcin

Określa `wcin` strumienia globalnego.

```cpp
extern wistream wcin;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [wistream](../standard-library/istream-typedefs.md#wistream) .

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje wyodrębnianie ze standardowego wejścia jako strumień szeroki. Gdy obiekt zostanie skonstruowany, wywołanie `wcin.`[krawat](../standard-library/basic-ios-class.md#tie) zwraca `&`[wcout](#wcout).

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) , aby zapoznać się z przykładem korzystania z `wcin`.

### <a name="wclog"></a>wclog

Określa `wclog` strumienia globalnego.

```cpp
extern wostream wclog;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [wostream —](../standard-library/ostream-typedefs.md#wostream) .

#### <a name="remarks"></a>Uwagi

Obiekt steruje buforowanymi wstawieniami do standardowego wyjścia błędu jako strumień szeroki.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) , aby zapoznać się z przykładem korzystania z `wclog`.

### <a name="wcout"></a>wcout

Określa `wcout` strumienia globalnego.

```cpp
extern wostream wcout;
```

#### <a name="return-value"></a>Wartość zwracana

Obiekt [wostream —](../standard-library/ostream-typedefs.md#wostream) .

#### <a name="remarks"></a>Uwagi

Obiekt kontroluje wstawienia do wyjścia standardowego jako strumień szeroki.

#### <a name="example"></a>Przykład

Zobacz [cerr](#cerr) , aby zapoznać się z przykładem korzystania z `wcout`.

wystąpienia `CString` w instrukcji `wcout` muszą być rzutowane do `const wchar_t*`, jak pokazano w poniższym przykładzie.

```cpp
CString cs("meow");

wcout <<(const wchar_t*) cs <<endl;
```

Aby uzyskać więcej informacji, zobacz [podstawowe operacje CString](../atl-mfc-shared/basic-cstring-operations.md).

## <a name="see-also"></a>Zobacz też

[Odwołania do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)\
[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
\ [programowania iostream](../standard-library/iostream-programming.md)
[Konwencje iostream](../standard-library/iostreams-conventions.md)
