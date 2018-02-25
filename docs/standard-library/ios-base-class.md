---
title: "ios_base — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- xiosbase/std::ios_base
- ios/std::ios_base::event_callback
- xiosbase/std::ios_base::fmtflags
- xiosbase/std::ios_base::iostate
- xiosbase/std::ios_base::openmode
- xiosbase/std::ios_base::seekdir
- xiosbase/std::ios_base::event
- xiosbase/std::ios_base::adjustfield
- xiosbase/std::ios_base::app
- xiosbase/std::ios_base::ate
- xiosbase/std::ios_base::badbit
- xiosbase/std::ios_base::basefield
- xiosbase/std::ios_base::beg
- xiosbase/std::ios_base::binary
- xiosbase/std::ios_base::boolalpha
- xiosbase/std::ios_base::cur
- xiosbase/std::ios_base::dec
- xiosbase/std::ios_base::end
- xiosbase/std::ios_base::eofbit
- xiosbase/std::ios_base::failbit
- xiosbase/std::ios_base::fixed
- xiosbase/std::ios_base::floatfield
- xiosbase/std::ios_base::goodbit
- xiosbase/std::ios_base::hex
- xiosbase/std::ios_base::in
- xiosbase/std::ios_base::internal
- xiosbase/std::ios_base::left
- xiosbase/std::ios_base::oct
- xiosbase/std::ios_base::out
- xiosbase/std::ios_base::right
- xiosbase/std::ios_base::scientific
- xiosbase/std::ios_base::showbase
- xiosbase/std::ios_base::showpoint
- xiosbase/std::ios_base::showpos
- xiosbase/std::ios_base::skipws
- xiosbase/std::ios_base::trunc
- xiosbase/std::ios_base::unitbuf
- xiosbase/std::ios_base::uppercase
- xiosbase/std::ios_base::failure
- xiosbase/std::ios_base::flags
- xiosbase/std::ios_base::getloc
- xiosbase/std::ios_base::imbue
- xiosbase/std::ios_base::Init
- xiosbase/std::ios_base::iword
- xiosbase/std::ios_base::precision
- xiosbase/std::ios_base::pword
- ios/std::ios_base::register_callback
- xiosbase/std::ios_base::setf
- xiosbase/std::ios_base::sync_with_stdio
- xiosbase/std::ios_base::unsetf
- xiosbase/std::ios_base::width
- xiosbase/std::ios_base::xalloc
dev_langs:
- C++
helpviewer_keywords:
- std::ios_base [C++]
- std::ios_base [C++], event_callback
- std::ios_base [C++], fmtflags
- std::ios_base [C++], iostate
- std::ios_base [C++], openmode
- std::ios_base [C++], seekdir
- std::ios_base [C++], event
- std::ios_base [C++], adjustfield
- std::ios_base [C++], app
- std::ios_base [C++], ate
- std::ios_base [C++], badbit
- std::ios_base [C++], basefield
- std::ios_base [C++], beg
- std::ios_base [C++], binary
- std::ios_base [C++], boolalpha
- std::ios_base [C++], cur
- std::ios_base [C++], dec
- std::ios_base [C++], end
- std::ios_base [C++], eofbit
- std::ios_base [C++], failbit
- std::ios_base [C++], fixed
- std::ios_base [C++], floatfield
- std::ios_base [C++], goodbit
- std::ios_base [C++], hex
- std::ios_base [C++], in
- std::ios_base [C++], internal
- std::ios_base [C++], left
- std::ios_base [C++], oct
- std::ios_base [C++], out
- std::ios_base [C++], right
- std::ios_base [C++], scientific
- std::ios_base [C++], showbase
- std::ios_base [C++], showpoint
- std::ios_base [C++], showpos
- std::ios_base [C++], skipws
- std::ios_base [C++], trunc
- std::ios_base [C++], unitbuf
- std::ios_base [C++], uppercase
- std::ios_base [C++], failure
- std::ios_base [C++], flags
- std::ios_base [C++], getloc
- std::ios_base [C++], imbue
- std::ios_base [C++], Init
- std::ios_base [C++], iword
- std::ios_base [C++], precision
- std::ios_base [C++], pword
- std::ios_base [C++], register_callback
- std::ios_base [C++], setf
- std::ios_base [C++], sync_with_stdio
- std::ios_base [C++], unsetf
- std::ios_base [C++], width
- std::ios_base [C++], xalloc
ms.assetid: 0f9e0abc-f70f-49bc-aa1f-003859f56cfe
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8d1182cdbaf33b2ab09ecbf133df52186246fbf5
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="iosbase-class"></a>ios_base — Klasa
Klasa opisuje magazyn i funkcje Członkowskie wspólne dla wejścia i wyjścia strumieni, które nie są zależne od parametrów szablonu. (Klasy szablonu [basic_ios —](../standard-library/basic-ios-class.md) opisano, co jest typowe i jest zależna od parametrów szablonu.)  
  
 Obiekt ios_base — klasa przechowuje informacje dotyczące formatowania, która składa się z:  
  
-   Format flagi w obiekcie typu [fmtflags](#fmtflags).  
  
-   Maska wyjątek w obiekcie typu [iostate](#iostate).  
  
-   Szerokość pola w obiekcie typu `int`.  
  
-   Dokładności wyświetlania w obiekcie typu `int`.  
  
-   Obiekt ustawień regionalnych w obiekcie typu **ustawień regionalnych**.  
  
-   Dwie tablice rozszerzalny, elementami typu **długi** i `void` wskaźnika.  
  
 Obiekt ios_base — klasa przechowuje także informacje o stanie strumienia, w obiekcie typu [iostate](#iostate)i stosu wywołania zwrotnego.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[ios_base](#ios_base)|Konstruuje `ios_base` obiektów.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[event_callback](#event_callback)|W tym artykule opisano przekazany do funkcji [register_call](#register_callback).|  
|[fmtflags](#fmtflags)|Stałe, aby określić wygląd danych wyjściowych.|  
|[iostate](#iostate)|Określa stałe opisujące stan strumienia.|  
|[openmode](#openmode)|Opisuje sposób interakcji z strumienia.|  
|[seekdir](#seekdir)|Określa punkt początkowy dla operacji przesunięcia.|  
  
### <a name="enums"></a>Wyliczenia  
  
|||  
|-|-|  
|[event](#event)|Określa typy zdarzeń.|  
  
### <a name="constants"></a>Stałe  
  
|||  
|-|-|  
|[adjustfield](#fmtflags)|Maska bitowa zdefiniowany jako `internal` &#124; `left` &#124; `right`.|  
|[Aplikacji](#openmode)|Określa wyszukiwanie na koniec strumienia przed każdym wstawiania.|  
|[uj](#openmode)|Określa wyszukiwanie do końca strumienia po jego kontrolowanie obiektu najpierw.|  
|[badbit](#iostate)|Rejestruje utraty integralności buforu strumienia.|  
|[basefield](#fmtflags)|Maska bitowa zdefiniowany jako `dec` &#124; `hex` &#124; `oct`.|  
|[beg](#seekdir)|Określa wyszukiwanie względem początku sekwencji.|  
|[Binarne](#openmode)|Określa, że plik można odczytać jako strumienia binarnego, a nie jako strumień tekstu.|  
|[boolalpha](#fmtflags)|Określa, wstawiania lub wyodrębniania obiektów typu `bool` jako nazwy (takich jak `true` i `false`), a nie jako wartości liczbowe.|  
|[cur](#seekdir)|Określa wyszukiwanie względem bieżącej pozycji w sekwencji.|  
|[DEC](#fmtflags)|Określa, wstawiania lub wyodrębniania wartości całkowite w formacie dziesiętnym.|  
|[Koniec](#seekdir)|Określa wyszukiwanie względem koniec sekwencji.|  
|[eofbit](#iostate)|Rejestruje koniec pliku podczas wyodrębniania ze strumienia.|  
|[failbit](#iostate)|Rejestruje błąd wyodrębnić prawidłowym polem ze strumienia.|  
|[Stałe](#fmtflags)|Określa wstawiania wartości zmiennoprzecinkowych w formacie stałoprzecinkowe (z żadnego pola wykładnika).|  
|[floatfield](#fmtflags)|Maska bitowa zdefiniowany jako `fixed` &#124; `scientific`|  
|[goodbit](#iostate)|Wyczyść wszystkie bity stanu.|  
|[hex](#fmtflags)|Określa, wstawiania lub wyodrębniania wartości całkowite w formacie szesnastkowym.|  
|[in](#openmode)|Określa wyodrębniania ze strumienia.|  
|[internal](#fmtflags)|Konsole do szerokości pola, wstawiając znaki w punkcie wewnętrzny wygenerowanego pola liczbowego.|  
|[left](#fmtflags)|Określa wyrównania do lewej.|  
|[oct](#fmtflags)|Określa wstawiania lub wyodrębniania wartości całkowite w formacie ósemkowe.|  
|[out](#openmode)|Określa wstawiania do strumienia.|  
|[right](#fmtflags)|Określa prawej strony.|  
|[scientific](#fmtflags)|Określa wstawiania wartości zmiennoprzecinkowych formatu naukowe (z polem wykładnika).|  
|[showbase](#fmtflags)|Określa wstawiania prefiks, który ujawnia base całkowitą wygenerowanego pola.|  
|[showpoint](#fmtflags)|Określa bezwarunkowe wstawiania dziesiętnego wygenerowanego pola liczb zmiennoprzecinkowych.|  
|[showpos](#fmtflags)|Określa nieujemna wygenerowanego pola numerycznego wstawiania znak plus.|  
|[skipws](#fmtflags)|Określa, pomijanie Spacja wiodąca przed niektórych ekstrakcje.|  
|[TRUNC —](#openmode)|Określa zawartość usuwanie istniejącego pliku po utworzeniu jego kontrolowanie obiekt.|  
|[unitbuf](#fmtflags)|Powoduje, że dane wyjściowe do opróżnienia po każdym wstawiania.|  
|[wielkie litery](#fmtflags)|Określa wstawiania odpowiedniki wielkie litery, małe litery w niektórych wstawienia.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[Błąd](#failure)|Klasy członkowskiej służy jako klasa podstawowa dla wszystkich wyjątków zgłaszanych przez funkcję elementu członkowskiego [wyczyść](../standard-library/basic-ios-class.md#clear) szablonu klasy [basic_ios —](../standard-library/basic-ios-class.md).|  
|[Flagi](#flags)|Ustawia lub zwraca bieżące ustawienia flagi.|  
|[getloc](#getloc)|Zwraca obiekt przechowywanych ustawień regionalnych.|  
|[imbue](#imbue)|Zmiany ustawień regionalnych.|  
|[Init](#init)|Tworzy obiekty iostream standardowe, gdy utworzony.|  
|[iword](#iword)|Przypisuje wartość do zapisania jako `iword`.|  
|[dokładność](#precision)|Określa liczbę miejsc po przecinku do wyświetlenia w liczbie zmiennoprzecinkowej.|  
|[pword](#pword)|Przypisuje wartość do zapisania jako `pword`.|  
|[register_callback](#register_callback)|Określa funkcję wywołania zwrotnego.|  
|[SETF](#setf)|Ustawia określone flagi.|  
|[sync_with_stdio](#sync_with_stdio)|Zapewnia, że iostream i operacje biblioteki wykonawcze języka C są wykonywane w kolejności ich występowania w kodzie źródłowym.|  
|[unsetf](#unsetf)|Powoduje, że określone flagi należy wyłączyć.|  
|[width](#width)|Ustawia długość strumienia wyjściowego.|  
|[xalloc](#xalloc)|Określa, czy zmienna jest częścią strumienia.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator=](#op_eq)|Operator przypisania dla `ios_base` obiektów.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<systemu ios >  
  
 **Namespace:** Standard  
  
##  <a name="event"></a>  ios_base::Event  
 Określa typy zdarzeń.  
  
```  
enum event {
    erase_event,
    imbue_event,
    copyfmt_event};  
```  
  
### <a name="remarks"></a>Uwagi  
 Typ jest Typ wyliczany opisujący obiekt, który może przechowywać zdarzenia wywołania zwrotnego używane jako argument do funkcji zarejestrowany [register_callback](#register_callback). Wartości różnych zdarzeń są następujące:  
  
- **copyfmt_event**, aby zidentyfikować wywołanie zwrotne, które występuje pod koniec wywołania [copyfmt](../standard-library/basic-ios-class.md#copyfmt), bezpośrednio przed [maska wyjątek](../standard-library/ios-base-class.md) zostanie skopiowana.  
  
- **erase_event**, aby zidentyfikować wywołania zwrotnego, która występuje na początku wywołania [copyfmt](../standard-library/basic-ios-class.md#copyfmt), lub na początku wywołania destruktora dla  **\*to**.  
  
- **imbue_event**, aby zidentyfikować wywołania zwrotnego, która występuje na końcu wywołanie [imbue](#imbue)tak, aby funkcja zwraca wartość.  
  
### <a name="example"></a>Przykład  
  
  Zobacz [register_callback](#register_callback) przykład.  
  
##  <a name="event_callback"></a>  ios_base::event_callback  

 W tym artykule opisano przekazany do funkcji [register_call](#register_callback).  
  
```  
typedef void (__cdecl *event_callback)(
    event _E,  
    ios_base& _Base,  
    int _I);
```  
  
### <a name="parameters"></a>Parametry  
 *_E*  
 [Zdarzeń](#event).  
  
 `_Base`  
 Strumień, w którym wywołano zdarzenie.  
  
 *_I*  
 Liczba zdefiniowanych przez użytkownika.  
  
### <a name="remarks"></a>Uwagi  
  
 Typ w tym artykule opisano wskaźnik funkcji, które mogą być rejestrowane w [register_callback](#register_callback). Ten typ funkcji nie należy zgłosić wyjątek.  
  
### <a name="example"></a>Przykład  
  
  Zobacz [register_call](#register_callback) na przykład, który używa `event_callback`.  
  
##  <a name="failure"></a>  ios_base::failure  
  
 Klasa `failure` definiuje klasę podstawową dla typów obiektów wszystkie zgłaszane wyjątki, za pomocą funkcji w `iostreams` biblioteki, aby włączyć raportowanie błędów wykrytych podczas operacji buforu strumienia.  
  
```  
namespace std {  
    class failure : public system_error {  
    public:  
        explicit failure(
            const string& _Message,  
            const error_code& _Code = io_errc::stream);

        explicit failure(
            const char* str,  
            const error_code& _Code = io_errc::stream);
    };
}  
```  
  
### <a name="remarks"></a>Uwagi  

 Wartość zwrócona przez `what()` kopię `_Message`, prawdopodobnie zwiększonej testem na podstawie `_Code`. Jeśli `_Code` nie zostanie określony, wartością domyślną jest `make_error_code(io_errc::stream)`.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ios_base_failure.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main ( )  
{  
    using namespace std;  
    fstream file;  
    file.exceptions(ios::failbit);  
    try  
    {  
        file.open( "rm.txt", ios_base::in );  
        // Opens nonexistent file for reading  
    }  
    catch( ios_base::failure f )  
    {  
        cout << "Caught an exception: " << f.what() << endl;  
    }  
}  
```  
  
```Output  
Caught an exception: ios_base::failbit set  
```  
  
##  <a name="flags"></a>  ios_base::Flags  
  
 Ustawia lub zwraca bieżące ustawienia flagi.  
  
```  
fmtflags flags() const;
fmtflags flags(fmtflags fmtfl);
```  
  
### <a name="parameters"></a>Parametry  
 `fmtfl`  
 Nowe `fmtflags` ustawienie.  
  
### <a name="return-value"></a>Wartość zwracana  
  
 Poprzedniego lub bieżącego `fmtflags` ustawienie.  
  
### <a name="remarks"></a>Uwagi  
  
 Zobacz [ios_base::fmtflags](#fmtflags) listę flag.  
  
 Pierwszy element członkowski funkcja flag formatu przechowywane. Drugi magazynów funkcji Członkowskich `fmtfl` flag formatu i zwraca jego poprzedniej przechowywana wartość.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ios_base_flags.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main ( )  
{  
    using namespace std;  
    cout << cout.flags( ) << endl;  
    cout.flags( ios::dec | ios::boolalpha );  
    cout << cout.flags( );  
}    
```  
  
```Output  
513  
16896  
```  
  
##  <a name="fmtflags"></a>  ios_base::fmtflags  
  
 Stałe, aby określić wygląd danych wyjściowych.  
  
```
class ios_base {  
public:  
   typedef implementation-defined-bitmask-type fmtflags;  
   static const fmtflags boolalpha;  
   static const fmtflags dec;  
   static const fmtflags fixed;  
   static const fmtflags hex;  
   static const fmtflags internal;  
   static const fmtflags left;  
   static const fmtflags oct;  
   static const fmtflags right;  
   static const fmtflags scientific;  
   static const fmtflags showbase;  
   static const fmtflags showpoint;  
   static const fmtflags showpos;  
   static const fmtflags skipws;  
   static const fmtflags unitbuf;  
   static const fmtflags uppercase;  
   static const fmtflags adjustfield;  
   static const fmtflags basefield;  
   static const fmtflags floatfield;  
   // ...  
};  
```  
  
### <a name="remarks"></a>Uwagi  
  
 Obsługuje manipulatory w [ios](../standard-library/ios.md).  
  
 Typ jest typem maski, który opisuje obiekt, który może przechowywać flag formatu. Flagi różne wartości (elementy) są następujące:  
  
- `dec`, aby wstawić lub Wyodrębnij wartości całkowite w formacie dziesiętnym.  
  
- `hex`, aby wstawić lub Wyodrębnij wartości całkowite w formacie szesnastkowym.  
  
- `oct`, aby wstawić lub Wyodrębnij wartości całkowite w formacie ósemkowe.  
  
- `showbase`, aby wstawić prefiks, który ujawnia base całkowitą wygenerowanego pola.  
  
- `internal`, aby uzupełnić do szerokości pola odpowiednio do potrzeb Wstawianie znaków wypełnienia w punkcie wewnętrzny wygenerowanego pola liczbowego. (Aby uzyskać informacje na temat ustawiania szerokości pola, zobacz [setw](../standard-library/iomanip-functions.md#setw)).  
  
- `left`, aby uzupełnić do szerokości pola odpowiednio do potrzeb Wstawianie znaki na końcu wygenerowanego pola (wyrównania do lewej).  
  
- `right`, aby uzupełnić do szerokości pola odpowiednio do potrzeb Wstawianie znaki na początku wygenerowanego pola (prawej strony).  
  
- `boolalpha`, aby wstawić lub Wyodrębnij obiektów typu `bool` jako nazwy (takich jak `true` i `false`), a nie jako wartości liczbowe.  
  
- `fixed`, aby wstawić wartości zmiennoprzecinkowych w formacie stałoprzecinkowe (z żadnego pola wykładnika).  
  
- `scientific`, aby wstawić wartości zmiennoprzecinkowych formatu naukowe (z polem wykładnika).  
  
- `showpoint`, aby wstawić punktu dziesiętnego bezwarunkowo wygenerowanego pola liczb zmiennoprzecinkowych.  
  
- `showpos`, który będzie wprowadzany znak plus nieujemna wygenerowanego pola liczbowego.  
  
- `skipws`, aby pominąć Spacja wiodąca przed niektórych ekstrakcje.  
  
- `unitbuf`, aby opróżnić dane wyjściowe po każdym wstawiania.  
  
- `uppercase`, aby wstawić odpowiedniki wielkie litery, małe litery w niektórych wstawienia.  
  
 Ponadto kilka przydatne wartości są następujące:  
  
- `adjustfield`, maską bitów zdefiniowany jako `internal` &#124; `left` &#124; `right`  
  
- `basefield`, zdefiniowany jako `dec` &#124; `hex` &#124; `oct`  
  
- `floatfield`, zdefiniowany jako `fixed` &#124; `scientific`  
  
 Przykłady funkcji, które modyfikują te format flagi, zobacz [ \<iomanip — >](../standard-library/iomanip.md).  
  
##  <a name="getloc"></a>  ios_base::getloc  
  
 Zwraca obiekt przechowywanych ustawień regionalnych.  
  
```  
locale getloc() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
  
 Obiekt przechowywanych ustawień regionalnych.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ios_base_getlock.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    cout << cout.getloc( ).name( ).c_str( ) << endl;  
}  
```  
  
```Output  
C  
```  
  
##  <a name="imbue"></a>  ios_base::imbue  

 Zmiany ustawień regionalnych.  
  
```  
locale imbue(const locale& _Loc);
```  
  
### <a name="parameters"></a>Parametry  
 `_Loc`  
 Nowe ustawienia regionalne.  
  
### <a name="return-value"></a>Wartość zwracana  
  
 Poprzednie ustawienia regionalne.  
  
### <a name="remarks"></a>Uwagi  
  
 Magazyny funkcji Członkowskich `_Loc` w obiekcie ustawień regionalnych, a następnie zgłasza zdarzenie wywołania zwrotnego i `imbue_event`. Zwraca poprzednią wartość przechowywane.  
  
### <a name="example"></a>Przykład  
  
  Zobacz [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue) przykładowe.  
  
##  <a name="init"></a>  ios_base::init  
  
 Tworzy obiekty iostream standardowe, gdy utworzony.  
  
```  
class Init { };  
```
  
### <a name="remarks"></a>Uwagi  
  
 Zagnieżdżona klasa opisuje obiekt, którego konstrukcji gwarantuje, że obiekty standardowe iostream prawidłowo są utworzone, nawet przed wykonaniem konstruktora dla dowolnego obiektu statycznego.  
  
##  <a name="ios_base"></a>  ios_base::ios_base  
  
 Tworzy obiekty ios_base —.  
  
```  
ios_base();
```  
  
### <a name="remarks"></a>Uwagi  
  
 Konstruktor (chroniony) nie działa. Wywołanie nowsze **basic_ios —::**[init](../standard-library/basic-ios-class.md#init) przed zostać zniszczone bezpiecznie musi zainicjować obiektu. W związku z tym tylko bezpieczne użycie ios_base — klasa jest jako klasę podstawową dla klasy szablonu [basic_ios —](../standard-library/basic-ios-class.md).  
  
##  <a name="iostate"></a>  ios_base::iostate  
  
 Typ stałe opisujące stan strumienia.  
  
```  
class ios_base {  
public:  
   typedef implementation-defined-bitmask-type iostate;  
   static const iostate badbit;  
   static const iostate eofbit;  
   static const iostate failbit;  
   static const iostate goodbit;  
   // ...  
};  
```  
  
### <a name="remarks"></a>Uwagi  
  
 Typ jest typem maski, który opisuje obiekt, który może zapisać informacji o stanie strumienia. Flagi różne wartości (elementy) są następujące:  
  
- `badbit`, aby zarejestrować utraty integralności buforu strumienia.  
  
- `eofbit`, aby rekordów koniec pliku podczas wyodrębniania ze strumienia.  
  
- `failbit`, aby zarejestrować niepowodzenie wyodrębnienia prawidłowym polem ze strumienia.  
  
 Ponadto jest przydatne wartość `goodbit`, gdzie są ustawione bity wymienione wcześniej ( `goodbit` może być równy zero).  
  
##  <a name="iword"></a>  ios_base::iword  
  
 Przypisuje wartość do zapisania jako `iword`.  
  
```  
long& iword(int idx);
```  
  
### <a name="parameters"></a>Parametry  
 `idx`  
 Indeks wartości do przechowywania jako `iword`.  
  
### <a name="remarks"></a>Uwagi  
  
 Funkcja członkowska zwraca odwołanie do elementu `idx` extensible tablicy elementami typu **długi**. Wszystkie elementy są skutecznie obecne i początkowo przechowywać wartość zero. Odwołanie zwracane jest nieprawidłowy po wywołaniu dalej `iword` dla obiektu, gdy obiekt jest zmieniony przez wywołanie do **basic_ios —::**[copyfmt](../standard-library/basic-ios-class.md#copyfmt), lub gdy obiekt zostanie zniszczony.  
  
 Jeśli `idx` jest ujemny lub jeśli unikatowy magazyn jest niedostępny dla elementu, wywołuje funkcję [metoda setstate](../standard-library/basic-ios-class.md#setstate)**(badbit)** i zwraca odwołanie, które nie muszą być unikatowe.  
  
 Aby uzyskać unikatowy indeks, do użytku dla wszystkich obiektów typu `ios_base`, wywołaj [xalloc](#xalloc).  
  
### <a name="example"></a>Przykład  
  
  Zobacz [xalloc](#xalloc) przykładowy sposób użycia `iword`.  
  
##  <a name="openmode"></a>  ios_base::openmode  
  
 Opisuje sposób interakcji z strumienia.  
  
```  
class ios_base {  
public:  
   typedef implementation-defined-bitmask-type iostate;  
   static const iostate badbit;  
   static const iostate eofbit;  
   static const iostate failbit;  
   static const iostate goodbit;  
   // ...  
};  
```  
  
### <a name="remarks"></a>Uwagi  
  
 Typ jest `bitmask type` , który opisuje obiekt, który może przechowywać tryb otwarcia wielu obiektów iostream. Flagi różne wartości (elementy) są następujące:  
  
- **Aplikacja**, aby wyszukiwać na koniec strumienia przed każdym wstawiania.  
  
- **uj**, aby przejść do końca strumienia po jego kontrolowanie obiektu najpierw.  
  
- **binarny**, aby odczytać plik jako strumienia binarnego, a nie jako strumień tekstu.  
  
- **w**, aby umożliwić wyodrębniania ze strumienia.  
  
- **limit**, aby umożliwić wstawiania do strumienia.  
  
- **TRUNC**, aby usunąć zawartość z istniejącego pliku po utworzeniu jego kontrolowanie obiekt.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ios_base_openmode.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main ( )  
{  
    using namespace std;  
    fstream file;  
    file.open( "rm.txt", ios_base::out | ios_base::trunc );  
    
    file << "testing";  
}    
```  
  
##  <a name="op_eq"></a>  ios_base::operator =  

 Operator przypisania dla obiektów ios_base —.  
  
```  
ios_base& operator=(const ios_base& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Obiekt typu `ios_base`.  
  
### <a name="return-value"></a>Wartość zwracana  
  
 Obiekt jest przypisywany do.  
  
### <a name="remarks"></a>Uwagi  
  
 Operator kopiuje przechowywane informacje dotyczące formatowania, nowych kopii dowolnego extensible tablic. Następnie zwraca  **\*to**. Należy pamiętać, że stosu wywołania zwrotnego nie został skopiowany.  
  
 Ten operator jest używana tylko w klasach pochodzących od `ios_base`.  
  
##  <a name="precision"></a>  ios_base::Precision  
  
 Określa liczbę miejsc po przecinku do wyświetlenia w liczbie zmiennoprzecinkowej.  
  
```  
streamsize precision() const;
streamsize precision(streamsize _Prec);
```  
  
### <a name="parameters"></a>Parametry  
 `_Prec`  
 Liczba cyfr znaczących w celu wyświetlenia lub liczbę cyfr po punkcie dziesiętnym w notacji stałej.  
  
### <a name="return-value"></a>Wartość zwracana  
  
 Zwraca zapisana pierwszej funkcji Członkowskich [dokładność wyświetlania](../standard-library/ios-base-class.md). Drugi magazynów funkcji Członkowskich `_Prec` dokładność wyświetlania i zwraca jego poprzedniej przechowywana wartość.  
  
### <a name="remarks"></a>Uwagi  
  
 Liczby zmiennoprzecinkowe są wyświetlane w notacji stałej z [stałej](../standard-library/ios-functions.md#fixed).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// ios_base_precision.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    float i = 31.31234F;  
    
    cout.precision( 3 );  
    cout << i << endl;          // display three significant digits  
    cout << fixed << i << endl; // display three digits after decimal  
                                // point  
}  
```  
  
```Output  
31.3  
31.312  
```  
  
##  <a name="pword"></a>  ios_base::pword  
  
 Przypisuje wartość do zapisania jako `pword`.  
  
```  
void *& pword(int _Idx);
```  
  
### <a name="parameters"></a>Parametry  
 `_Idx`  
 Indeks wartości do przechowywania jako `pword`.  
  
### <a name="remarks"></a>Uwagi  
  
 Funkcja członkowska zwraca odwołanie do elementu _ *Idx* extensible tablicy elementami typu `void` wskaźnika. Wszystkie elementy są wydajnie obecne i początkowo przechowywania pustego wskaźnika. Odwołanie zwracane jest nieprawidłowy po wywołaniu dalej `pword` dla obiektu, gdy obiekt jest zmieniony przez wywołanie do **basic_ios —::**[copyfmt](../standard-library/basic-ios-class.md#copyfmt), lub gdy obiekt zostanie zniszczony.  
  
 Jeśli _ *Idx* jest ujemna, lub jeśli unikatowy magazyn jest niedostępny dla elementu, wywołuje funkcję [metoda setstate](../standard-library/basic-ios-class.md#setstate)**(badbit)** i zwraca odwołanie, które nie muszą być unikatowe.  
  
 Aby uzyskać unikatowy indeks, do użytku dla wszystkich obiektów typu `ios_base`, wywołaj [xalloc](#xalloc).  
  
### <a name="example"></a>Przykład  
  
  Zobacz [xalloc](#xalloc) przykład przy użyciu `pword`.  
  
##  <a name="register_callback"></a>  ios_base::register_callback  
  
 Określa funkcję wywołania zwrotnego.  
  
```  
void register_callback(
    event_callback pfn, int idx);
```  
  
### <a name="parameters"></a>Parametry  
 `pfn`  
 Wskaźnik do funkcji wywołania zwrotnego.  
  
 `idx`  
 Liczba zdefiniowanych przez użytkownika.  
  
### <a name="remarks"></a>Uwagi  
  
 Funkcja członkowska wypchnięcia pary `{pfn, idx}` na stosie przechowywanych wywołania zwrotnego [stosu wywołania zwrotnego](../standard-library/ios-base-class.md). Gdy zdarzenie wywołania zwrotnego **weryfikacją** jest zgłaszany, funkcje są nazywane, w kolejności odwrotnej rejestracji, przez wyrażenie `(*pfn)(ev, *this, idx)`.  
 
### <a name="example"></a>Przykład  
  
```cpp  
// ios_base_register_callback.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
using namespace std;  
  
void callback1( ios_base::event e, ios_base& stream, int arg )  
{  
    cout << "in callback1" << endl;  
    switch ( e )  
    {  
    case ios_base::erase_event:  
        cout << "an erase event" << endl;  
        break;  
    case ios_base::imbue_event:  
        cout << "an imbue event" << endl;  
        break;  
    case ios_base::copyfmt_event:  
        cout << "an copyfmt event" << endl;  
        break;  
    };  
}  
  
void callback2( ios_base::event e, ios_base& stream, int arg )  
{  
    cout << "in callback2" << endl;  
    switch ( e )  
    {  
    case ios_base::erase_event:  
        cout << "an erase event" << endl;  
        break;  
    case ios_base::imbue_event:  
        cout << "an imbue event" << endl;  
        break;  
    case ios_base::copyfmt_event:  
        cout << "an copyfmt event" << endl;  
        break;  
    };  
}  
  
int main( )  
{  
    // Make sure the imbue will not throw an exception  
    // assert( setlocale( LC_ALL, "german" )!=NULL );  
    
    cout.register_callback( callback1, 0 );  
    cin.register_callback( callback2, 0 );  
    
    try  
    {  
        // If no exception because the locale's not found,  
        // generate an imbue_event on callback1  
        cout.imbue(locale("german"));  
    }  
    catch(...)  
    {  
        cout << "exception" << endl;  
    }  
    
    // This will  
    // (1) erase_event on callback1  
    // (2) copyfmt_event on callback2  
    cout.copyfmt(cin);  
    
    // We get two erase events from callback2 at the end because  
    // both cin and cout have callback2 registered when cin and cout  
    // are destroyed at the end of program.  
}  
```  
  
```Output  
in callback1  
an imbue event  
in callback1  
an erase event  
in callback2  
an copyfmt event  
in callback2  
an erase event  
in callback2  
an erase event  
```  
 
##  <a name="seekdir"></a> ios_base::seekdir  
  
Określa punkt początkowy dla operacji przesunięcia.  
  
```  
namespace std {  
    class ios_base {  
    public:  
        typedef implementation-defined-enumerated-type seekdir;  
        static const seekdir beg;  
        static const seekdir cur;  
        static const seekdir end;  
        // ...  
    };  
}  
```  
 
### <a name="remarks"></a>Uwagi  
  
Typ jest Typ wyliczany opisujący obiekt, który może przechowywać używanym jako argument do funkcji Członkowskich w klasach iostream kilka tryb wyszukiwania. Flaga różne wartości są następujące:  
 
- **czyna**, aby wyszukiwać (alter bieżącego odczytu lub zapisu pozycji) względem na początku sekwencji (tablicy, strumienia lub pliku).  
 
- **Waluta**, aby wyszukiwać względem bieżącej pozycji w sekwencji.  
 
- **końcowy**, aby wyszukiwać względem koniec sekwencji.  
 
### <a name="example"></a>Przykład  
  
```cpp  
// ios_base_seekdir.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main ( )  
{  
    using namespace std;  
    fstream file;  
    file.open( "rm.txt", ios_base::out | ios_base::trunc );  
    
    file << "testing";  
    file.seekp( 0, ios_base::beg );  
    file << "a";  
    file.seekp( 0, ios_base::end );  
    file << "a";  
}  
```  
  
##  <a name="setf"></a> ios_base::SETF  
  
Ustawia określone flagi.  

```    
fmtflags setf(  
    fmtflags _Mask  
);  
fmtflags setf(  
    fmtflags _Mask,  
    fmtflags _Unset  
);  
```  
 
### <a name="parameters"></a>Parametry  
 `_Mask`  
    Flagi, aby włączyć funkcję.  
 
 *_Unset* flagi, które należy wyłączyć.  
 
### <a name="return-value"></a>Wartość zwracana  
    The previous format flags  
 
### <a name="remarks"></a>Uwagi  
    The first member function effectively calls [flags](#flags)(_ *Mask* &#124; \_ *Flags*) (set selected bits) and then returns the previous format flags. The second member function effectively calls **flags**(\_ *Mask* **& fmtfl, flags& ~**`_Mask`) (replace selected bits under a mask) and then returns the previous format flags.  
 
### <a name="example"></a>Przykład  
  
```cpp  
// ios_base_setf.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    int i = 10;  
    cout << i << endl;  
    
    cout.unsetf( ios_base::dec );  
    cout.setf( ios_base::hex );  
    cout << i << endl;  
    
    cout.setf( ios_base::dec );  
    cout << i << endl;  
    cout.setf( ios_base::hex, ios_base::dec );  
    cout << i << endl;  
}  
```  
 
##  <a name="sync_with_stdio"></a> ios_base::sync_with_stdio  
  
Zapewnia, że iostream i operacje biblioteki wykonawcze języka C są wykonywane w kolejności ich występowania w kodzie źródłowym.  
  
```  
static bool sync_with_stdio(  
   bool _Sync = true  
);  
```  
 
### <a name="parameters"></a>Parametry  
 `_Sync`  
    Określa, czy wszystkie strumienie są zsynchronizowane z **stdio —**.  
 
### <a name="return-value"></a>Wartość zwracana  
    Previous setting for this function.  
 
### <a name="remarks"></a>Uwagi  
    The static member function stores a **stdio** sync flag, which is initially **true**. When **true**, this flag ensures that operations on the same file are properly synchronized between the [iostreams](../standard-library/iostreams-conventions.md) functions and those defined in the C++ Standard Library. Otherwise, synchronization may or may not be guaranteed, but performance may be improved. The function stores `_Sync` in the **stdio** sync flag and returns its previous stored value. You can call it reliably only before performing any operations on the standard streams.  
 
##  <a name="unsetf"></a> ios_base::unsetf  
  
Powoduje, że określone flagi należy wyłączyć.  
  
```  
void unsetf(  
   fmtflags _Mask  
);  
```  
 
### <a name="parameters"></a>Parametry  
 `_Mask`  
    Flagi, które chcesz wyłączyć.  
 
### <a name="remarks"></a>Uwagi  
    The member function effectively calls [flags](#flags)(`~`*_Mask* **& flags**) (clear selected bits).  
 
### <a name="example"></a>Przykład  
    See [ios_base::setf](#setf) for a sample of using `unsetf`.  
 
##  <a name="width"></a> ios_base::Width  
  
Ustawia długość strumienia wyjściowego.  
  
```  
streamsize width( ) const;  
streamsize width(  
   streamsize _Wide  
);  
```  
 
### <a name="parameters"></a>Parametry  
 `_Wide`  
    Wymagany rozmiar strumienia wyjściowego.  
 
### <a name="return-value"></a>Wartość zwracana  

    The current width setting.  
 
### <a name="remarks"></a>Uwagi  

    The first member function returns the stored field width. The second member function stores `_Wide` in the field width and returns its previous stored value.  
 
### <a name="example"></a>Przykład  
  
```cpp  
// ios_base_width.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( ) {  
    using namespace std;  
    
    cout.width( 20 );  
    cout << cout.width( ) << endl;  
    cout << cout.width( ) << endl;  
}  
```  
  
```Output  
20  
0  
```  
 
##  <a name="xalloc"></a> ios_base::xalloc  
  
    Specifies that a variable is part of the stream.  
  
```  
static int xalloc( );  
```  
 
### <a name="return-value"></a>Wartość zwracana  
    The static member function returns a stored static value, which it increments on each call.  
 
### <a name="remarks"></a>Uwagi  
    You can use the return value as a unique index argument when calling the member functions [iword](#iword) or [pword](#pword).  
 
### <a name="example"></a>Przykład  
  
```cpp  
// ios_base_xalloc.cpp  
// compile with: /EHsc  
// Lets you store user-defined information.  
// iword, jword, xalloc  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    
    static const int i = ios_base::xalloc();  
    static const int j = ios_base::xalloc();  
    cout.iword( i ) = 11;  
    cin.iword( i ) = 13;  
    cin.pword( j ) = "testing";  
    cout << cout.iword( i ) << endl;  
    cout << cin.iword( i ) << endl;  
    cout << ( char * )cin.pword( j ) << endl;  
}    
```  
  
```Output  
11  
13  
testing  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream — programowanie](../standard-library/iostream-programming.md)   
 [Konwencje iostream](../standard-library/iostreams-conventions.md)
