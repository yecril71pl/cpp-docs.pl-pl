---
title: "&lt;iomanip —&gt; funkcje | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- iomanip/std::get_money
- iomanip/std::get_time
- iomanip/std::put_money
- iomanip/std::put_time
- iomanip/std::quoted
- iomanip/std::resetiosflags
- iomanip/std::setbase
- iomanip/std::setfill
- iomanip/std::setiosflags
- iomanip/std::setprecision
- iomanip/std::setw
ms.assetid: 3ddde610-70cc-4cfa-8a89-3e83d1d356a8
caps.latest.revision: 
manager: ghogen
helpviewer_keywords:
- std::get_money [C++]
- std::get_time [C++]
- std::put_money [C++]
- std::put_time [C++]
- std::quoted [C++]
- std::resetiosflags [C++]
- std::setbase [C++]
- std::setfill [C++]
- std::setiosflags [C++]
- std::setprecision [C++]
- std::setw [C++]
ms.openlocfilehash: 6d36261e237d2a9c4ee7afddd0cb57d60cb5e12c
ms.sourcegitcommit: 9239c52c05e5cd19b6a72005372179587a47a8e4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2018
---
# <a name="ltiomanipgt-functions"></a>&lt;iomanip —&gt; funkcji
||||  
|-|-|-|  
|[get_money](#iomanip_get_money)|[get_time](#iomanip_get_time)|[put_money](#iomanip_put_money)|  
|[put_time](#iomanip_put_time)|[w cudzysłowach](#quoted)|[resetiosflags](#resetiosflags)|  
|[setbase](#setbase)|[setfill](#setfill)|[setiosflags](#setiosflags)|  
|[setprecision](#setprecision)|[setw](#setw)|  
  
##  <a name="iomanip_get_money"></a>  get_money —  
 Wyodrębnia ze strumienia w formacie żądaną wartość pieniężną i zwraca wartość w parametrze.  
  
```  
template <class Money>  
T7 get_money(Money& _Amount, bool _Intl);
```  
  
### <a name="parameters"></a>Parametry  
 _Amount  
 Wartość pieniężną wyodrębnione.  
  
 _Intl  
 Jeśli `true`, użyj formatu międzynarodowe. Wartość domyślna to `false`.  
  
### <a name="remarks"></a>Uwagi  
 Manipulatora zwraca obiekt, gdy wyodrębnione ze strumienia `str`, zachowuje się jak `formatted input function` , który odwołuje się funkcja członkowska `get` dla ustawień regionalnych aspekt `money_get` skojarzone z `str`za pomocą `_Intl` do Wskazuje format międzynarodowe. Jeśli się powiedzie, wywołania są przechowywane w `_Amount` wartość pieniężną wyodrębnione. Zwraca manipulatora `str`.  
  
 `Money` musi być typu `long double` lub instancją typu `basic_string` z takimi samymi parametrami elementu i cech jako `str`.  
  
##  <a name="iomanip_get_time"></a>  get_time  
 Wyodrębnianie wartości typu time ze strumienia żądane formacie. Zwraca wartość w parametrze jako struktura czasu.  
  
```  
template <class Elem>  
T10 put_time(struct tm *_Tptr, const Elem *_Fmt);
```  
  
### <a name="parameters"></a>Parametry  
 `_Tptr`  
 Czas w postaci struktury czasu.  
  
 `_Fmt`  
 Żądany format używany do uzyskania wartości czasu.  
  
### <a name="remarks"></a>Uwagi  
 Manipulatora zwraca obiekt, gdy wyodrębnione ze strumienia `str`, zachowuje się jak `formatted input function` , który odwołuje się funkcja członkowska `get` dla ustawień regionalnych aspekt `time_get` skojarzone z `str`za pomocą `tptr` do wskazuje strukturę czasu i `fmt` wskazująca na początku ciąg formatu zerem. W przypadku powodzenia wywołanie przechowuje w strukturze czasu wartości skojarzone z żadnych pól wyodrębnionego czasu. Zwraca manipulatora `str`.  
  
##  <a name="iomanip_put_money"></a>  put_money —  
 Wstawia kwotę pieniężną w formacie odpowiednie do strumienia.  
  
```  
template <class Money>  
T8 put_money(const Money& _Amount, bool _Intl);
```  
  
### <a name="parameters"></a>Parametry  
 `_Amount`  
 Kwota salda do wstawienia do strumienia.  
  
 `_Intl`  
 Ustaw `true` Jeśli manipulatora powinien mieć format międzynarodowe, `false` Jeśli nie powinien.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca `str`.  
  
### <a name="remarks"></a>Uwagi  
 Manipulatora zwraca obiekt, który po wstawieniu do strumienia `str`, działa jak funkcja sformatowane dane wyjściowe, która wywołuje funkcję elementu członkowskiego `put` dla ustawień regionalnych aspekt `money_put` skojarzone z `str`. Jeśli się powiedzie, wywołanie wstawia `amount` odpowiednio sformatowane, za pomocą `_Intl` wskazująca formacie międzynarodowej i `str.fill()`, jako element wypełnienia. Zwraca manipulatora `str`.  
  
 `Money` musi być typu `long double` lub instancją typu `basic_string` z takimi samymi parametrami elementu i cech jako `str`.  
  
##  <a name="iomanip_put_time"></a>  put_time —  
 Zapisuje wartość godziny z struktura czasowego do strumienia przy użyciu określonego formatu.  
  
```  
template <class Elem>  
T10 put_time(struct tm* _Tptr, const Elem* _Fmt);
```  
  
### <a name="parameters"></a>Parametry  
 `_Tptr`  
 Wartość czasu do zapisu do strumienia, w strukturze czasu.  
  
 `_Fmt`  
 Żądany format można zapisać wartości typu time.  
  
### <a name="remarks"></a>Uwagi  
 Manipulatora zwraca obiekt, który po wstawieniu do strumienia `str`, zachowuje się jak `formatted output function`. Funkcja dane wyjściowe wywołuje funkcję elementu członkowskiego `put` dla ustawień regionalnych aspekt `time_put` skojarzone z `str`. Funkcja dane wyjściowe używa `_Tptr` wskazująca czas struktury i `_Fmt` wskazująca na początku ciąg formatu zakończone NUL. W przypadku powodzenia wywołanie wstawia tekst literału ciągu formatu i przekonwertowane wartości ze struktury czasu. Zwraca manipulatora `str`.  
  
##  <a name="quoted"></a>  w cudzysłowach  
 **(Nowość w języku C ++ 14)**  Manipulatora iostream, która umożliwia wygodne dwustronną komunikację ciągi do i z strumieni przy użyciu >> i << operatorów.  
  
```  
quoted(std::string str) // or wstring  
quoted(const char* str) //or wchar_t* 
quoted(std::string str, char delimiter, char escape) // or wide versions  
quoted(const char* str, char delimiter, char escape) // or wide versions  
```  
  
### <a name="parameters"></a>Parametry  
 `str`  
 Std::string, char *, ciąg literału ciągu literału lub raw lub szerokości wersji tych (np. std::wstring, wchar_t\*).  
  
 `delimiter`  
 Określony użytkownik znak lub znaków dwubajtowych do użycia jako ogranicznik początku i końca ciągu.  
  
 `escape`  
 Określony użytkownik znak lub znaków dwubajtowych do użycia jako znak ucieczki dla sekwencji unikowych w ciągu.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [korzystanie z operatorów wstawiania i formatu kontrolującego](../standard-library/using-insertion-operators-and-controlling-format.md).  
  
### <a name="example"></a>Przykład  
  Ten przykład przedstawia sposób użycia `quoted` przy użyciu domyślnego ogranicznik i przy użyciu znaku ucieczki zawęzić ciągów. Ciągi szeroki jednakowo są obsługiwane.  
  
```cpp  
#include <iostream>  
#include <iomanip>  
#include <sstream>  
  
using namespace std;  
  
void show_quoted_v_nonquoted()  
{  
    // Results are identical regardless of input string type:  
    // string inserted { R"(This is a "sentence".)" }; // raw string literal  
    // string inserted { "This is a \"sentence\"." };  // regular string literal  
    const char* inserted = "This is a \"sentence\".";  // const char*  
    stringstream ss, ss_quoted;  
    string extracted, extracted_quoted;  
  
    ss << inserted;  
    ss_quoted << quoted(inserted);  
  
    cout << "ss.str() is storing       : " << ss.str() << endl;  
    cout << "ss_quoted.str() is storing: " << ss_quoted.str() << endl << endl;  
  
    // Round-trip the strings   
    ss >> extracted;  
    ss_quoted >> quoted(extracted_quoted);  
  
    cout << "After round trip: " << endl;  
    cout << "Non-quoted      : " << extracted << endl;  
    cout << "Quoted          : " << extracted_quoted << endl;  
}  
  
void main(int argc, char* argv[])  
{  
    show_quoted_v_nonquoted();  
  
    // Keep console window open in debug mode.  
    cout << endl << "Press Enter to exit" << endl;  
    string input{};  
    getline(cin, input);  
}  
  
/* Output:  
ss.str() is storing       : This is a "sentence".  
ss_quoted.str() is storing: "This is a \"sentence\"."  
  
After round trip:  
Non-quoted      : This  
Quoted          : This is a "sentence".  
  
Press Enter to exit  
*/  
```  
  
### <a name="example"></a>Przykład  
  Poniższy przykład przedstawia sposób zapewnienia niestandardowy znak ogranicznika i/lub anulowania:  
  
```cpp  
#include <iostream>  
#include <iomanip>  
#include <sstream>  
  
using namespace std;  
  
void show_custom_delimiter()  
{  
    string inserted{ R"("This" "is" "a" "heavily-quoted" "sentence".)" };  
    // string inserted{ "\"This\" \"is\" \"a\" \"heavily-quoted\" \"sentence\"" };  
    // const char* inserted{ "\"This\" \"is\" \"a\" \"heavily-quoted\" \"sentence\"" };  
    stringstream ss, ss_quoted;  
    string extracted;  
  
    ss_quoted << quoted(inserted, '*');  
    ss << inserted;  
    cout << "ss_quoted.str() is storing: " << ss_quoted.str() << endl;  
    cout << "ss.str() is storing       : " << ss.str() << endl << endl;  
  
    // Use the same quoted arguments as on insertion.  
    ss_quoted >> quoted(extracted, '*');  
  
    cout << "After round trip: " << endl;  
    cout << "Quoted          : " << extracted << endl;  
  
    extracted = {};  
    ss >> extracted;  
    cout << "Non-quoted      : " << extracted << endl << endl;  
}  
  
void show_custom_escape()  
{  
    string inserted{ R"(\\root\trunk\branch\nest\egg\yolk)" };  
    // string inserted{ "\\\\root\\trunk\\branch\\nest\\egg\\yolk" };  
    stringstream ss, ss_quoted, ss_quoted_custom;  
    string extracted;  
  
    // Use '"' as delimiter and '~' as escape character.  
    ss_quoted_custom << quoted(inserted, '"', '~');  
    ss_quoted << quoted(inserted);  
    ss << inserted;  
    cout << "ss_quoted_custom.str(): " << ss_quoted_custom.str() << endl;  
    cout << "ss_quoted.str()       : " << ss_quoted.str() << endl;  
    cout << "ss.str()              : " << ss.str() << endl << endl;  
  
    // No spaces in this string, so non-quoted behaves same as quoted  
    // after round-tripping.  
}  
  
void main(int argc, char* argv[])  
{  
    cout << "Custom delimiter:" << endl;  
    show_custom_delimiter();  
    cout << "Custom escape character:" << endl;  
    show_custom_escape();  
  
    // Keep console window open in debug mode.  
    cout << endl << "Press Enter to exit" << endl;  
    string input{};  
    getline(cin, input);  
}  
/* Output:  
Custom delimiter:  
ss_quoted.str() is storing: *"This" "is" "a" "heavily-quoted" "sentence".*  
ss.str() is storing       : "This" "is" "a" "heavily-quoted" "sentence".  
  
After round trip:  
Quoted          : "This" "is" "a" "heavily-quoted" "sentence".  
Non-quoted      : "This"  
  
Custom escape character:  
ss_quoted_custom.str(): "\\root\trunk\branch\nest\egg\yolk"  
ss_quoted.str()       : "\\\\root\\trunk\\branch\\nest\\egg\\yolk"  
ss.str()              : \\root\trunk\branch\nest\egg\yolk  
  
Press Enter to exit  
*/  
  
```  
  
##  <a name="resetiosflags"></a>  resetiosflags  
 Usuwa określone flagi.  
  
```  
T1 resetiosflags(ios_base::fmtflags Mask);
```  
  
### <a name="parameters"></a>Parametry  
 `Mask`  
 Flagi, aby wyczyścić.  
  
### <a name="return-value"></a>Wartość zwracana  
 Manipulatora zwraca obiekt, który wyodrębniony z lub do strumienia **str**, wywołania **str**. [SETF](../standard-library/ios-base-class.md#setf)( `ios_base::` [fmtflags](../standard-library/ios-base-class.md#fmtflags), _ *maski*), a następnie zwraca **str**.  
  
### <a name="example"></a>Przykład  
  Zobacz [setw](../standard-library/iomanip-functions.md#setw) przykład przy użyciu `resetiosflags`.  
  
##  <a name="setbase"></a>  setbase  
 Ustaw podstawowej liczb całkowitych.  
  
```  
T3 setbase(int _Base);
```  
  
### <a name="parameters"></a>Parametry  
 `_Base`  
 Podstawowy numer.  
  
### <a name="return-value"></a>Wartość zwracana  
 Manipulatora zwraca obiekt, który wyodrębniony z lub do strumienia **str**, wywołania **str**. `setf`( **maski**, [ios_base::basefield](../standard-library/ios-base-class.md#fmtflags)), a następnie zwraca **str**. W tym miejscu **maski** jest określane w następujący sposób:  
  
-   Jeśli _ *Base* jest 8, następnie **maski** jest `ios_base::` [oct](../standard-library/ios-functions.md#oct).  
  
-   Jeśli _ *Base* wynosi 10, a następnie maska jest `ios_base::` [gru](../standard-library/ios-functions.md#dec).  
  
-   Jeśli _ *Base* jest 16, następnie **maski** jest `ios_base::` [szesnastkowych](../standard-library/ios-functions.md#hex).  
  
-   Jeśli _ *Base* jest wszelkie inne wartości, a następnie maska jest `ios_base::` [fmtflags](../standard-library/ios-base-class.md#fmtflags)(0).  
  
### <a name="example"></a>Przykład  
  Zobacz [setw](../standard-library/iomanip-functions.md#setw) przykład przy użyciu `setbase`.  
  
##  <a name="setfill"></a>  setfill  
 Ustawia znak używany do wypełniania miejsc w prawej strony ekranu.  
  
```  
template <class Elem>  
T4 setfill(Elem Ch);
```  
  
### <a name="parameters"></a>Parametry  
 `Ch`  
 Znak, który będzie używany do wypełniania miejsc w prawej strony ekranu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Manipulatora szablonu zwraca obiekt, który wyodrębniony z lub do strumienia **str**, wywołania **str**. [wypełnienie](../standard-library/basic-ios-class.md#fill)( `Ch`), a następnie zwraca **str**. Typ **elementu** musi być taki sam jak typ elementu strumienia **str**.  
  
### <a name="example"></a>Przykład  
  Zobacz [setw](../standard-library/iomanip-functions.md#setw) przykład przy użyciu `setfill`.  
  
##  <a name="setiosflags"></a>  setiosflags  
 Ustawia określone flagi.  
  
```  
T2 setiosflags(ios_base::fmtflags Mask);
```  
  
### <a name="parameters"></a>Parametry  
 `Mask`  
 Flagi do ustawienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Manipulatora zwraca obiekt, który wyodrębniony z lub do strumienia **str**, wywołania **str**. [SETF](../standard-library/ios-base-class.md#setf)(_ *maski*), a następnie zwraca **str**.  
  
### <a name="example"></a>Przykład  
  Zobacz [setw](../standard-library/iomanip-functions.md#setw) przykład przy użyciu `setiosflags`.  
  
##  <a name="setprecision"></a>  setprecision  
 Ustawia dokładność wartości zmiennoprzecinkowych.  
  
```  
T5 setprecision(streamsize Prec);
```  
  
### <a name="parameters"></a>Parametry  
 `Prec`  
 Dokładność wartości zmiennoprzecinkowych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Manipulatora zwraca obiekt, który wyodrębniony z lub do strumienia **str**, wywołania **str**. [dokładność](../standard-library/ios-base-class.md#precision)( `Prec`), a następnie zwraca **str**.  
  
### <a name="example"></a>Przykład  
  Zobacz [setw](../standard-library/iomanip-functions.md#setw) przykład przy użyciu `setprecision`.  
  
##  <a name="setw"></a>  setw  
 Określa szerokość pola wyświetlania dla następnego elementu w strumieniu.  
  
```  
T6 setw(streamsize Wide);
```  
  
### <a name="parameters"></a>Parametry  
 `Wide`  
 Szerokość pola wyświetlania.  
  
### <a name="return-value"></a>Wartość zwracana  
 Manipulatora zwraca obiekt, który wyodrębniony z lub do strumienia **str**, wywołania **str**. [szerokość](../standard-library/ios-base-class.md#width)(_ *szeroki*), zwraca **str**.  
  
### <a name="remarks"></a>Uwagi  
 setw Ustawia szerokość tylko dla następnego elementu w strumieniu i muszą być wstawiane przed każdym elementem szerokość, którego ma zostać określony.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// iomanip_setw.cpp   
// compile with: /EHsc  
// Defines the entry point for the console application.  
//  
// Sample use of the following manipulators:  
//   resetiosflags  
//   setiosflags  
//   setbase  
//   setfill  
//   setprecision  
//   setw  
  
#include <iostream>  
#include <iomanip>  
  
using namespace std;  
  
const double   d1 = 1.23456789;  
const double   d2 = 12.3456789;  
const double   d3 = 123.456789;  
const double   d4 = 1234.56789;  
const double   d5 = 12345.6789;  
const long      l1 = 16;  
const long      l2 = 256;  
const long      l3 = 1024;  
const long      l4 = 4096;  
const long      l5 = 65536;  
int         base = 10;  
  
void DisplayDefault( )  
{  
   cout << endl << "default display" << endl;  
   cout << "d1 = " << d1 << endl;  
   cout << "d2 = " << d2 << endl;  
   cout << "d3 = " << d3 << endl;  
   cout << "d4 = " << d4 << endl;  
   cout << "d5 = " << d5 << endl;  
}  
  
void DisplayWidth( int n )  
{  
   cout << endl << "fixed width display set to " << n << ".\n";  
   cout << "d1 = " << setw(n) << d1 << endl;  
   cout << "d2 = " << setw(n) << d2 << endl;  
   cout << "d3 = " << setw(n) << d3 << endl;  
   cout << "d4 = " << setw(n) << d4 << endl;  
   cout << "d5 = " << setw(n) << d5 << endl;  
}  
  
void DisplayLongs( )  
{  
   cout << setbase(10);  
   cout << endl << "setbase(" << base << ")" << endl;  
   cout << setbase(base);  
   cout << "l1 = " << l1 << endl;  
   cout << "l2 = " << l2 << endl;  
   cout << "l3 = " << l3 << endl;  
   cout << "l4 = " << l4 << endl;  
   cout << "l5 = " << l5 << endl;  
}  
  
int main( int argc, char* argv[] )  
{  
   DisplayDefault( );  
  
   cout << endl << "setprecision(" << 3 << ")" << setprecision(3);  
   DisplayDefault( );  
  
   cout << endl << "setprecision(" << 12 << ")" << setprecision(12);  
   DisplayDefault( );  
  
   cout << setiosflags(ios_base::scientific);  
   cout << endl << "setiosflags(" << ios_base::scientific << ")";  
   DisplayDefault( );  
  
   cout << resetiosflags(ios_base::scientific);  
   cout << endl << "resetiosflags(" << ios_base::scientific << ")";  
   DisplayDefault( );  
  
   cout << endl << "setfill('" << 'S' << "')" << setfill('S');  
   DisplayWidth(15);  
   DisplayDefault( );  
  
   cout << endl << "setfill('" << ' ' << "')" << setfill(' ');  
   DisplayWidth(15);  
   DisplayDefault( );  
  
   cout << endl << "setprecision(" << 8 << ")" << setprecision(8);  
   DisplayWidth(10);  
   DisplayDefault( );  
  
   base = 16;  
   DisplayLongs( );  
  
   base = 8;  
   DisplayLongs( );  
  
   base = 10;  
   DisplayLongs( );  
  
   return   0;  
}  
```  
  
```Output  
  
default display  
d1 = 1.23457  
d2 = 12.3457  
d3 = 123.457  
d4 = 1234.57  
d5 = 12345.7  
  
setprecision(3)  
default display  
d1 = 1.23  
d2 = 12.3  
d3 = 123  
d4 = 1.23e+003  
d5 = 1.23e+004  
  
setprecision(12)  
default display  
d1 = 1.23456789  
d2 = 12.3456789  
d3 = 123.456789  
d4 = 1234.56789  
d5 = 12345.6789  
  
setiosflags(4096)  
default display  
d1 = 1.234567890000e+000  
d2 = 1.234567890000e+001  
d3 = 1.234567890000e+002  
d4 = 1.234567890000e+003  
d5 = 1.234567890000e+004  
  
resetiosflags(4096)  
default display  
d1 = 1.23456789  
d2 = 12.3456789  
d3 = 123.456789  
d4 = 1234.56789  
d5 = 12345.6789  
  
setfill('S')  
fixed width display set to 15.  
d1 = SSSSS1.23456789  
d2 = SSSSS12.3456789  
d3 = SSSSS123.456789  
d4 = SSSSS1234.56789  
d5 = SSSSS12345.6789  
  
default display  
d1 = 1.23456789  
d2 = 12.3456789  
d3 = 123.456789  
d4 = 1234.56789  
d5 = 12345.6789  
  
setfill(' ')  
fixed width display set to 15.  
d1 =      1.23456789  
d2 =      12.3456789  
d3 =      123.456789  
d4 =      1234.56789  
d5 =      12345.6789  
  
default display  
d1 = 1.23456789  
d2 = 12.3456789  
d3 = 123.456789  
d4 = 1234.56789  
d5 = 12345.6789  
  
setprecision(8)  
fixed width display set to 10.  
d1 =  1.2345679  
d2 =  12.345679  
d3 =  123.45679  
d4 =  1234.5679  
d5 =  12345.679  
  
default display  
d1 = 1.2345679  
d2 = 12.345679  
d3 = 123.45679  
d4 = 1234.5679  
d5 = 12345.679  
  
setbase(16)  
l1 = 10  
l2 = 100  
l3 = 400  
l4 = 1000  
l5 = 10000  
  
setbase(8)  
l1 = 20  
l2 = 400  
l3 = 2000  
l4 = 10000  
l5 = 200000  
  
setbase(10)  
l1 = 16  
l2 = 256  
l3 = 1024  
l4 = 4096  
l5 = 65536  
```  
  
## <a name="see-also"></a>Zobacz też  
 [\<iomanip>](../standard-library/iomanip.md)

