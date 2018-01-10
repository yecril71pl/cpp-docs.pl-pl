---
title: "&lt;iostream —&gt; | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 09/20/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords: iostream header
ms.assetid: de5d39e1-7e77-4b55-bcd1-7c77b41515c8
caps.latest.revision: "23"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 430981da5ec304bf832e759d40870ee88f3e6557
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/21/2017
---
# <a name="ltiostreamgt"></a>&lt;iostream&gt;
Deklaruje kontrolować odczytywanie z oraz zapisywanie do standardowych strumieni. Często jest tylko nagłówek potrzebne do dołączenia do wykonania programu C++ danych wejściowych i wyjściowych.  
  
## <a name="syntax"></a>Składnia  
  
```  
#include <iostream>  
  
```  
  
## <a name="remarks"></a>Uwagi  
 Obiektów można podzielić na dwie grupy:  
  
- [CIN](#cin), [cout](#cout), [cerr](#cerr), i [clog —](#clog) są bajtów skoncentrowany na zadaniach, konwencjonalnych transferu bajtów w czasie wykonywania.  
  
- [wcin](#wcin), [wcout](#wcout), [wcerr](#wcerr), i [wclog](#wclog) całego układane, tłumaczenia do i z znaki dwubajtowe, które program manipuluje wewnętrznie.  
  
 Po wykonaniu pewnych operacji na strumieniu, takich jak standardowe dane wejściowe, nie można wykonać operacji inną orientację na tym samym strumienia. W związku z tym program nie może działać zamiennie zarówno [cin](#cin) i [wcin](#wcin), np.  
  
 Wszystkie obiekty zadeklarowany w tym udziale nagłówka wspólnych właściwości — można założyć one przed wszystkie obiekty statyczne można zdefiniować w jednostce tłumaczenia, która obejmuje \<iostream >. Jednakowo można założyć, że te obiekty nie zostaną zniszczone przed destruktory dla takich statycznych obiektów zdefiniowanych. (Strumienie wyjściowe jednak opróżnionych podczas przerywania program). W związku z tym można bezpiecznie odczytywanie i zapisywanie do standardowych strumieni przed uruchamianie programu i po Kończenie działania programu.  
  
 Nie uniwersalnego, jest jednak gwarancji. Statyczny Konstruktor może wywołać funkcję w innej jednostce tłumaczenia. Wywołana funkcja nie założono, że obiekty zadeklarowane w nagłówku tego ma skonstruowane, podany w nieokreślonej kolejności, w których tłumaczenia jednostki uczestniczyć w konstrukcji statycznych. W takiej sytuacji należy używać tych obiektów, należy najpierw utworzyć obiekt klasy [ios_base::Init](../standard-library/ios-base-class.md#init).  
  
### <a name="global-stream-objects"></a>Obiekty globalne strumienia  
  
|||  
|-|-|  
|[cerr](#cerr)|Określa `cerr` globalnego strumienia.|  
|[CIN](#cin)|Określa `cin` globalnego strumienia.|  
|[clog](#clog)|Określa `clog` globalnego strumienia.|  
|[Cout](#cout)|Określa `cout` globalnego strumienia.|  
|[wcerr](#wcerr)|Określa `wcerr` globalnego strumienia.|  
|[wcin](#wcin)|Określa `wcin` globalnego strumienia.|  
|[wclog](#wclog)|Określa `wclog` globalnego strumienia.|  
|[wcout](#wcout)|Określa `wcout` globalnego strumienia.|  
  
###  <a name="cerr"></a>cerr  
 Obiekt `cerr` Określa dane wyjściowe do strumienia buforu skojarzony z obiektem `stderr`, zadeklarowanych w \<cstdio — >.  
  
```  
extern ostream cerr;  
```  
  
#### <a name="return-value"></a>Wartość zwracana  
 [Ostream](../standard-library/ostream-typedefs.md#ostream) obiektu.  
  
#### <a name="remarks"></a>Uwagi  
 Obiekt steruje Niebuforowane wstawienia w wyniku standardowy błąd jako strumień bajtów. Gdy obiekt jest tworzony, wyrażenie `cerr.` [flagi](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) jest różna od zera, i `cerr.tie() == &cout`.  
  
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
  
###  <a name="cin"></a>CIN  
 Określa `cin` globalnego strumienia.  
  
```  
extern istream cin;  
```  
  
#### <a name="return-value"></a>Wartość zwracana  
 [Istream](../standard-library/istream-typedefs.md#istream) obiektu.  
  
#### <a name="remarks"></a>Uwagi  
 Obiekt steruje ekstrakcje standardowe dane wejściowe jako strumień bajtów. Gdy obiekt jest tworzony, wywołanie `cin.` [tie](../standard-library/basic-ios-class.md#tie) zwraca `&` [cout](#cout).  
  
#### <a name="example"></a>Przykład  
  W tym przykładzie `cin` ustawia niepowodzenie bitów w strumieniu po napotkaniu znaków nienumerycznych. Program czyści kończyć się niepowodzeniem i usuwa nieprawidłowy znak ze strumienia, aby kontynuować.  
  
```  
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
 Określa `clog` globalnego strumienia.  
  
```  
extern ostream clog;  
```  
  
#### <a name="return-value"></a>Wartość zwracana  
 [Ostream](../standard-library/ostream-typedefs.md#ostream) obiektu.  
  
#### <a name="remarks"></a>Uwagi  
 Formanty obiektu buforowana wstawienia w wyniku standardowy błąd jako strumień bajtów.  
  
#### <a name="example"></a>Przykład  
  Zobacz [cerr](#cerr) przykład przy użyciu `clog`.  
  
###  <a name="cout"></a>Cout  
 Określa `cout` globalnego strumienia.  
  
```  
extern ostream cout;  
```  
  
#### <a name="return-value"></a>Wartość zwracana  
 [Ostream](../standard-library/ostream-typedefs.md#ostream) obiektu.  
  
#### <a name="remarks"></a>Uwagi  
 Obiekt steruje wstawiania do wyjścia standardowego jako strumień bajtów.  
  
#### <a name="example"></a>Przykład  
  Zobacz [cerr](#cerr) przykład przy użyciu `cout`.  
  
###  <a name="wcerr"></a>wcerr  
 Określa `wcerr` globalnego strumienia.  
  
```  
extern wostream wcerr;  
```  
  
#### <a name="return-value"></a>Wartość zwracana  
 A [wostream](../standard-library/ostream-typedefs.md#wostream) obiektu.  
  
#### <a name="remarks"></a>Uwagi  
 Obiekt steruje Niebuforowane wstawienia w wyniku standardowy błąd jako strumień szerokości. Gdy obiekt jest tworzony, wyrażenie `wcerr.` [flagi](../standard-library/ios-base-class.md#flags) `&` [unitbuf](../standard-library/ios-functions.md#unitbuf) jest różna od zera.  
  
#### <a name="example"></a>Przykład  
  Zobacz [cerr](#cerr) przykład przy użyciu `wcerr`.  
  
###  <a name="wcin"></a>wcin  
 Określa `wcin` globalnego strumienia.  
  
```  
extern wistream wcin;  
```  
  
#### <a name="return-value"></a>Wartość zwracana  
 A [wistream](../standard-library/istream-typedefs.md#wistream) obiektu.  
  
#### <a name="remarks"></a>Uwagi  
 Obiekt steruje ekstrakcje standardowe dane wejściowe jako strumień szerokości. Gdy obiekt jest tworzony, wywołanie `wcin.` [tie](../standard-library/basic-ios-class.md#tie) zwraca `&` [wcout](#wcout).  
  
#### <a name="example"></a>Przykład  
  Zobacz [cerr](#cerr) przykład przy użyciu `wcin`.  
  
###  <a name="wclog"></a>wclog  
 Określa `wclog` globalnego strumienia.  
  
```  
extern wostream wclog;  
```  
  
#### <a name="return-value"></a>Wartość zwracana  
 A [wostream](../standard-library/ostream-typedefs.md#wostream) obiektu.  
  
#### <a name="remarks"></a>Uwagi  
 Formanty obiektu buforowana wstawienia w wyniku standardowy błąd jako strumień szerokości.  
  
#### <a name="example"></a>Przykład  
  Zobacz [cerr](#cerr) przykład przy użyciu `wclog`.  
  
###  <a name="wcout"></a>wcout  
 Określa `wcout` globalnego strumienia.  
  
```  
extern wostream wcout;  
```  
  
#### <a name="return-value"></a>Wartość zwracana  
 A [wostream](../standard-library/ostream-typedefs.md#wostream) obiektu.  
  
#### <a name="remarks"></a>Uwagi  
 Obiekt steruje wstawiania do wyjścia standardowego jako strumień szerokości.  
  
#### <a name="example"></a>Przykład  
  Zobacz [cerr](#cerr) przykład przy użyciu `wcout`.  
  
 `CString`wystąpienia w `wcout` instrukcji musi być rzutowane na `const wchar_t*`, jak pokazano w poniższym przykładzie.  
  
```  
 
    CString cs("meow");

    wcout <<(const wchar_t*) cs <<endl;  
```  
  
 Aby uzyskać więcej informacji, zobacz [podstawowe operacje cstring —](../atl-mfc-shared/basic-cstring-operations.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie do plików nagłówkowych](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream — programowanie](../standard-library/iostream-programming.md)   
 [Konwencje iostream](../standard-library/iostreams-conventions.md)

