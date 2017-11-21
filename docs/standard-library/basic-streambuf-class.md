---
title: "basic_streambuf — klasa | Dokumentacja firmy Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- streambuf/std::basic_streambuf
- streambuf/std::basic_streambuf::char_type
- streambuf/std::basic_streambuf::int_type
- streambuf/std::basic_streambuf::off_type
- streambuf/std::basic_streambuf::pos_type
- streambuf/std::basic_streambuf::traits_type
- streambuf/std::basic_streambuf::eback
- streambuf/std::basic_streambuf::egptr
- streambuf/std::basic_streambuf::epptr
- streambuf/std::basic_streambuf::gbump
- streambuf/std::basic_streambuf::getloc
- streambuf/std::basic_streambuf::gptr
- streambuf/std::basic_streambuf::imbue
- streambuf/std::basic_streambuf::in_avail
- streambuf/std::basic_streambuf::overflow
- streambuf/std::basic_streambuf::pbackfail
- streambuf/std::basic_streambuf::pbase
- streambuf/std::basic_streambuf::pbump
- streambuf/std::basic_streambuf::pptr
- streambuf/std::basic_streambuf::pubimbue
- streambuf/std::basic_streambuf::pubseekoff
- streambuf/std::basic_streambuf::pubseekpos
- streambuf/std::basic_streambuf::pubsetbuf
- streambuf/std::basic_streambuf::pubsync
- streambuf/std::basic_streambuf::sbumpc
- streambuf/std::basic_streambuf::seekoff
- streambuf/std::basic_streambuf::seekpos
- streambuf/std::basic_streambuf::setbuf
- streambuf/std::basic_streambuf::setg
- streambuf/std::basic_streambuf::setp
- streambuf/std::basic_streambuf::sgetc
- streambuf/std::basic_streambuf::sgetn
- streambuf/std::basic_streambuf::showmanyc
- streambuf/std::basic_streambuf::snextc
- streambuf/std::basic_streambuf::sputbackc
- streambuf/std::basic_streambuf::sputc
- streambuf/std::basic_streambuf::sputn
- streambuf/std::basic_streambuf::stossc
- streambuf/std::basic_streambuf::sungetc
- streambuf/std::basic_streambuf::swap
- streambuf/std::basic_streambuf::sync
- streambuf/std::basic_streambuf::uflow
- streambuf/std::basic_streambuf::underflow
- streambuf/std::basic_streambuf::xsgetn
- streambuf/std::basic_streambuf::xsputn
dev_langs: C++
helpviewer_keywords:
- std::basic_streambuf [C++]
- std::basic_streambuf [C++], char_type
- std::basic_streambuf [C++], int_type
- std::basic_streambuf [C++], off_type
- std::basic_streambuf [C++], pos_type
- std::basic_streambuf [C++], traits_type
- std::basic_streambuf [C++], eback
- std::basic_streambuf [C++], egptr
- std::basic_streambuf [C++], epptr
- std::basic_streambuf [C++], gbump
- std::basic_streambuf [C++], getloc
- std::basic_streambuf [C++], gptr
- std::basic_streambuf [C++], imbue
- std::basic_streambuf [C++], in_avail
- std::basic_streambuf [C++], overflow
- std::basic_streambuf [C++], pbackfail
- std::basic_streambuf [C++], pbase
- std::basic_streambuf [C++], pbump
- std::basic_streambuf [C++], pptr
- std::basic_streambuf [C++], pubimbue
- std::basic_streambuf [C++], pubseekoff
- std::basic_streambuf [C++], pubseekpos
- std::basic_streambuf [C++], pubsetbuf
- std::basic_streambuf [C++], pubsync
- std::basic_streambuf [C++], sbumpc
- std::basic_streambuf [C++], seekoff
- std::basic_streambuf [C++], seekpos
- std::basic_streambuf [C++], setbuf
- std::basic_streambuf [C++], setg
- std::basic_streambuf [C++], setp
- std::basic_streambuf [C++], sgetc
- std::basic_streambuf [C++], sgetn
- std::basic_streambuf [C++], showmanyc
- std::basic_streambuf [C++], snextc
- std::basic_streambuf [C++], sputbackc
- std::basic_streambuf [C++], sputc
- std::basic_streambuf [C++], sputn
- std::basic_streambuf [C++], stossc
- std::basic_streambuf [C++], sungetc
- std::basic_streambuf [C++], swap
- std::basic_streambuf [C++], sync
- std::basic_streambuf [C++], uflow
- std::basic_streambuf [C++], underflow
- std::basic_streambuf [C++], xsgetn
- std::basic_streambuf [C++], xsputn
ms.assetid: 136af6c3-13bf-4501-9288-b93da26efac7
caps.latest.revision: "27"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0586de707bb015e21df5c7975b98be6966cd0262
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="basicstreambuf-class"></a>basic_streambuf — Klasa
Zawiera opis abstrakcyjną klasę podstawową dla wyprowadzanie buforu strumienia, który kontroluje przesyłania elementów do i z reprezentację określonego strumienia.  
  
## <a name="syntax"></a>Składnia  
  
```  
template <class Elem, class Tr = char_traits<Elem>>  
class basic_streambuf;  
```  
  
#### <a name="parameters"></a>Parametry  
 `Elem`  
 A [char_type](#char_type).  
  
 `Tr`  
 Znak [traits_type](#traits_type).  
  
## <a name="remarks"></a>Uwagi  
 Klasy szablonów opis abstrakcyjną klasę podstawową dla wyprowadzanie buforu strumienia, który kontroluje przesyłania elementów do i z reprezentację określonego strumienia. Obiekt klasy `basic_streambuf` ułatwia kontrolowanie strumienia elementami typu `Tr`, znanej także jako [char_type](#char_type), którego cech znaków są określane przez klasę [char_traits](../standard-library/char-traits-struct.md), znanej również jako [traits_type](#traits_type).  
  
 Każdy buforu strumienia koncepcyjnie steruje dwa niezależne strumienie: jeden dla ekstrakcje (dane wejściowe) i jeden dla wstawienia (dane wyjściowe). Reprezentacja określonych mogą jednak dokonywać jednego lub obu tych strumieni niedostępny. Zazwyczaj przechowuje niektóre relacji między dwoma strumieni. Wstawianie w strumieniu wyjściowym [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`> obiekt, jest na przykład, co później wyodrębniony z jego strumień wejściowy. Po ustawieniu jednego strumienia [basic_filebuf —](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> obiekt, umieść innego strumienia w połączeniu.  
  
 Interfejs publiczny do szablonu klasy `basic_streambuf` udostępnia operacje, które są wspólne dla wszystkich bufory strumienia, jednak specjalizowany. Interfejs chroniony dostarcza potrzebnych dla reprezentację określonego obiektu strumienia, aby wykonać swoją pracę operacji. Funkcje chroniony element członkowski wirtualnego pozwalają dostosować zachowanie pochodnej strumienia buforu dla reprezentację określonego strumienia. Bufor każdego strumienia pochodnej w tej bibliotece opisano, jak specjalizuje się zachowanie jego funkcji chronionego członka wirtualnego. Domyślne zachowanie dla klasy podstawowej, która jest często, aby nic nie rób, jest opisane w tym temacie.  
  
 Pozostałe chronione kopiowania do i z dowolnego magazynu dostarczony do transmisji buforu do i z strumieni kontrola funkcje elementów członkowskich. Bufor wejściowy, na przykład charakteryzuje się:  
  
- [eback](#eback), kursor na początku buforu.  
  
- [gptr](#gptr), wskaźnik do następnego elementu do odczytu.  
  
- [egptr](#egptr), wskaźnik tylko poza koniec bufora.  
  
 Podobnie bufor wyjściowy jest określony przez:  
  
- [pbase](#pbase), kursor na początku buforu.  
  
- [pptr](#pptr), wskaźnik do następnego elementu do zapisu.  
  
- [epptr](#epptr), wskaźnik tylko poza koniec bufora.  
  
 Dla dowolnego buforu następujący protokół jest używany:  
  
-   Jeśli wskaźnik następnej ma wartość null, nie istnieje żadne buforu. W przeciwnym razie wszystkie trzy wskaźniki punktu w takiej samej kolejności. Można bezpiecznie porównywane dla zlecenia.  
  
-   Dla buforu wyjściowego Jeśli wskaźnik następnej porównuje mniejsza od zakończenia wskaźnika, można przechowywać element na pozycji zapisu wskazywany przez wskaźnik następnej.  
  
-   Dla buforu wejściowego Jeśli wskaźnik następnej porównuje mniej niż wskaźnika celu może odczytywać element z pozycji odczytu wskazywany przez wskaźnik następnej.  
  
-   Dla buforu wejściowego Jeśli wskaźnik początku porównuje mniej niż wskaźnik następnej możesz umieścić ponownie element na pozycji putback wskazywany przez wskaźnik następnej zmniejszany.  
  
 Chronione dowolnej funkcji wirtualnych elementów członkowskich należy zapisać klasą pochodną `basic_streambuf` <  `Elem`, `Tr`> musi współpracować przy zachowaniu tego protokołu.  
  
 Obiekt klasy `basic_streambuf` <  `Elem`, `Tr`> przechowuje wskaźniki sześciu opisany wcześniej. Przechowuje także obiekt ustawień regionalnych w obiekcie typu [ustawień regionalnych](../standard-library/locale-class.md) dla potencjalnych używany przez bufor pochodnej strumienia.  
  
### <a name="constructors"></a>Konstruktorów  
  
|||  
|-|-|  
|[basic_streambuf —](#basic_streambuf)|Tworzy obiekt typu `basic_streambuf`.|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|Kojarzy nazwę typu z `Elem` parametru szablonu.|  
|[int_type](#int_type)|Kojarzy nazwę typu, w ramach `basic_streambuf` zakres z `Elem` parametru szablonu.|  
|[off_type](#off_type)|Kojarzy nazwę typu, w ramach `basic_streambuf` zakres z `Elem` parametru szablonu.|  
|[pos_type](#pos_type)|Kojarzy nazwę typu, w ramach `basic_streambuf` zakres z `Elem` parametru szablonu.|  
|[traits_type](#traits_type)|Kojarzy nazwę typu z `Tr` parametru szablonu.|  
  
### <a name="member-functions"></a>Funkcje elementów członkowskich  
  
|||  
|-|-|  
|[eback](#eback)|Funkcja chronionych, która zwraca wskaźnik do początku buforu wejściowego.|  
|[egptr](#egptr)|Funkcja chronionych, która zwraca wskaźnik tylko poza koniec buforu wejściowego.|  
|[epptr](#epptr)|Funkcja chronionych, która zwraca wskaźnik tylko poza koniec buforu wyjściowego.|  
|[gbump](#gbump)|Funkcja chronionych, która dodaje `count` na wskaźnik następnej dla buforu wejściowego.|  
|[getloc](#getloc)|Pobiera `basic_streambuf` obiektu ustawień regionalnych.|  
|[gptr](#gptr)|Funkcja chronionych, która zwraca wskaźnik do następnego elementu buforu wejściowego.|  
|[imbue](#imbue)|A chroniony, wirtualny funkcja wywoływana przez [pubimbue](#pubimbue).|  
|[in_avail](#in_avail)|Zwraca liczbę elementów, które są gotowe do odczytu z buforu.|  
|[przepełnienie](#overflow)|Chronione funkcji wirtualnej można wywołać po wstawieniu nowego znaku w buforze pełna.|  
|[pbackfail](#pbackfail)|Chroniony element członkowski wirtualnego funkcję, która próbuje ponownie poddane elementu wejściowego strumienia, należy to zrobić bieżącego elementu (wskazywana przez wskaźnik następnej).|  
|[pbase](#pbase)|Funkcja chronionych, która zwraca wskaźnik do początku buforu wyjściowego.|  
|[pbump](#pbump)|Funkcja chronionych, która dodaje `count` do następnego wskaźnika buforu danych wyjściowych.|  
|[pptr](#pptr)|Funkcja chronionych, która zwraca wskaźnik do następnego elementu buforu wyjściowego.|  
|[pubimbue](#pubimbue)|Ustawia `basic_streambuf` obiektu ustawień regionalnych.|  
|[pubseekoff](#pubseekoff)|Wywołania [seekoff](#seekoff), chroniony funkcji wirtualnej, który został zastąpiony w klasie pochodnej.|  
|[pubseekpos](#pubseekpos)|Wywołania [seekpos](#seekpos), chroniony funkcji wirtualnej został zastąpiony w klasie pochodnej i resetuje bieżącą pozycję wskaźnika.|  
|[pubsetbuf](#pubsetbuf)|Wywołania [setbuf](#setbuf), chroniony funkcji wirtualnej, który został zastąpiony w klasie pochodnej.|  
|[pubsync](#pubsync)|Wywołania [synchronizacji](#sync), chroniony funkcji wirtualnej, który został zastąpiony w klasie pochodnej i aktualizuje zewnętrznego strumienia skojarzonego z tym buforu.|  
|[sbumpc](#sbumpc)|Odczytuje i zwraca bieżący element przenoszenie strumienia wskaźnika.|  
|[seekoff](#seekoff)|Funkcja chronionego członka wirtualnego próbuje zmienić bieżącego położenia dla strumieni kontrolowane.|  
|[seekpos](#seekpos)|Funkcja chronionego członka wirtualnego próbuje zmienić bieżącego położenia dla strumieni kontrolowane.|  
|[setbuf](#setbuf)|Funkcja chroniony element członkowski wirtualnego wykonuje określonego operację do każdego strumienia pochodnej buforu.|  
|[setg](#setg)|Funkcja chronionych, która przechowuje `_Gbeg` we wskaźniku początku `_Gnext` w wskaźnik następnej i `_Gend` we wskaźniku zakończenia dla buforu wejściowego.|  
|[setp](#setp)|Funkcja chronionych, która przechowuje `_Pbeg` we wskaźniku początku i `_Pend` we wskaźniku końcowego buforu danych wyjściowych.|  
|[sgetc](#sgetc)|Zwraca bieżący element bez zmiany pozycji w strumieniu.|  
|[sgetn](#sgetn)|Zwraca liczbę elementów do odczytu.|  
|[showmanyc](#showmanyc)|Chroniony element członkowski wirtualnego funkcja, która zwraca liczbę liczbę znaków, które można wyodrębnić ze strumienia wejściowego i upewnij się, że program nie będzie podlegał nieograniczonego oczekiwania.|  
|[snextc](#snextc)|Odczytuje bieżący element i zwraca następujący element.|  
|[sputbackc](#sputbackc)|Umieszcza `char_type` w strumieniu.|  
|[sputc](#sputc)|Umieszcza znak w strumieniu.|  
|[sputn](#sputn)|Umieszcza ciąg znaków w strumieniu.|  
|[stossc](#stossc)|Przenieś poza bieżący element w strumieniu.|  
|[sungetc](#sungetc)|Pobiera znak ze strumienia.|  
|[swap](#swap)|Zamienia wartości w tym obiekcie dla wartości w określonych `basic_streambuf` obiekt parametru.|  
|[synchronizacji](#sync)|Chronione funkcji wirtualnej próbuje synchronizować kontrolowane strumieni wszystkie skojarzone strumieni zewnętrznych.|  
|[uflow](#uflow)|Chronione funkcji wirtualnej wyodrębnia bieżącego elementu ze strumienia wejściowego.|  
|[niedopełnienie](#underflow)|Chronione funkcji wirtualnej wyodrębnia bieżącego elementu ze strumienia wejściowego.|  
|[xsgetn](#xsgetn)|Chronione funkcji wirtualnej wyodrębnia elementów ze strumienia wejściowego.|  
|[xsputn](#xsputn)|Chronione funkcji wirtualnej Wstawia elementy do strumienia wyjściowego.|  
  
### <a name="operators"></a>Operatory  
  
|||  
|-|-|  
|[operator =](#op_eq)|Przypisuje wartości tego obiektu z innego `basic_streambuf` obiektu.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** \<streambuf >  
  
 **Namespace:** Standard  
  
##  <a name="basic_streambuf"></a>basic_streambuf::basic_streambuf  
 Tworzy obiekt typu `basic_streambuf`.  
  
```  
basic_streambuf();

basic_streambuf(const basic_streambuf& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Odwołania do wartości do `basic_streambuf` obiekt, który służy do ustawiania wartości dla tego `basic_streambuf` obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Konstruktor chroniony pierwszy przechowuje wskaźnika o wartości null w wszystkie wskaźniki kontrolowanie buforu wejściowego i buforu wyjściowego. Przechowuje także `locale::classic` w obiekcie ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [locale::classic](../standard-library/locale-class.md#classic).  
  
 Drugi Konstruktor chroniony kopiuje wskaźników i ustawienia regionalne z `right`.  
  
##  <a name="char_type"></a>basic_streambuf::char_type  
 Kojarzy nazwę typu z **elementu** parametru szablonu.  
  
```  
typedef Elem char_type;  
```  
  
##  <a name="eback"></a>basic_streambuf::eback  
 Funkcja chronionych, która zwraca wskaźnik do początku buforu wejściowego.  
  
```  
char_type *eback() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do początku buforu wejściowego.  
  
##  <a name="egptr"></a>basic_streambuf::egptr  
 Funkcja chronionych, która zwraca wskaźnik tylko poza koniec buforu wejściowego.  
  
```  
char_type *egptr() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik tylko poza koniec buforu wejściowego.  
  
##  <a name="epptr"></a>basic_streambuf::epptr  
 Funkcja chronionych, która zwraca wskaźnik tylko poza koniec buforu wyjściowego.  
  
```  
char_type *epptr() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik tylko poza koniec buforu wyjściowego.  
  
##  <a name="gbump"></a>basic_streambuf::gbump  
 Funkcja chronionych, która dodaje `count` na wskaźnik następnej dla buforu wejściowego.  
  
```  
void gbump(int count);
```  
  
### <a name="parameters"></a>Parametry  
 `count`  
 Kwota za pomocą którego można poprawić wskaźnika.  
  
##  <a name="getloc"></a>basic_streambuf::getloc  
 Pobiera obiekt basic_streambuf — ustawień regionalnych.  
  
```  
locale getloc() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Obiekt przechowywanych ustawień regionalnych.  
  
### <a name="remarks"></a>Uwagi  
 Aby uzyskać odpowiednie informacje, zobacz [ios_base::getloc](../standard-library/ios-base-class.md#getloc).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_streambuf_getloc.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   cout << cout.rdbuf( )->getloc( ).name( ).c_str( ) << endl;  
}  
```  
  
```Output  
C  
```  
  
##  <a name="gptr"></a>basic_streambuf::gptr  
 Funkcja chronionych, która zwraca wskaźnik do następnego elementu buforu wejściowego.  
  
```  
char_type *gptr() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do następnego elementu buforu wejściowego.  
  
##  <a name="imbue"></a>basic_streambuf::imbue  
 A chronione wirtualnych funkcja wywoływana przez [pubimbue](#pubimbue).  
  
```  
virtual void imbue(const locale& _Loc);
```  
  
### <a name="parameters"></a>Parametry  
 `_Loc`  
 Odwołanie do ustawień regionalnych.  
  
### <a name="remarks"></a>Uwagi  
 Domyślnym zachowaniem jest nic nie rób.  
  
##  <a name="in_avail"></a>basic_streambuf::in_avail  
 Zwraca liczbę elementów, które są gotowe do odczytu z buforu.  
  
```  
streamsize in_avail();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów, które są gotowe do odczytu z buforu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli [pozycja odczytu](../standard-library/basic-streambuf-class.md) jest dostępna funkcja członkowska zwraca [egptr](#egptr) - [gptr](#gptr). W przeciwnym razie zwraca [showmanyc](#showmanyc).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_streambuf_in_avail.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   char c;  
   // cin's buffer is empty, in_avail will return 0  
   cout << cin.rdbuf( )->in_avail( ) << endl;  
   cin >> c;  
   cout << cin.rdbuf( )->in_avail( ) << endl;  
}  
```  
  
##  <a name="int_type"></a>basic_streambuf::int_type  
 Kojarzy nazwę typu w zakresie basic_streambuf — jednego z typów w parametrze szablonu.  
  
```  
typedef typename traits_type::int_type int_type;  
```  
  
##  <a name="off_type"></a>basic_streambuf::off_type  
 Kojarzy nazwę typu w zakresie basic_streambuf — jednego z typów w parametrze szablonu.  
  
```  
typedef typename traits_type::off_type off_type;  
```  
  
##  <a name="op_eq"></a>basic_streambuf::operator =  
 Przypisuje wartości tego obiektu z innego `basic_streambuf` obiektu.  
  
```  
basic_streambuf& operator=(const basic_streambuf& right);
```  
  
### <a name="parameters"></a>Parametry  
 `right`  
 Odwołania do wartości do `basic_streambuf` obiekt, który jest używany do przypisywania wartości do tego obiektu.  
  
### <a name="remarks"></a>Uwagi  
 Operator chroniony element członkowski kopiuje z `right` wskaźniki określające buforu wejściowego i buforu wyjściowego. Przechowuje także `right.` [getloc()](#getloc) w `locale object`. Zwraca `*this`.  
  
##  <a name="overflow"></a>basic_streambuf::Overflow  
 Chronione funkcji wirtualnej można wywołać po wstawieniu nowego znaku w buforze pełna.  
  
```  
virtual int_type overflow(int_type _Meta = traits_type::eof());
```  
  
### <a name="parameters"></a>Parametry  
 `_Meta`  
 Znak do wstawienia w buforze, lub **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja nie może się powieść, zwraca **traits_type::eof** lub zgłasza wyjątek. W przeciwnym razie zwraca **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*). Domyślnym zachowaniem jest zwracany **traits_type::eof**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli _ *Meta* porównuje równa **traits_type::eof**, funkcja chroniony element członkowski wirtualnego usiłują wstawienie elementu **traits_type::**[to_ char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*) do strumienia wyjściowego. Go to zrobić na różne sposoby:  
  
-   Jeśli `write position` jest dostępny, można przechowywać elementu w miejscu zapisu i zwiększyć wskaźnik następnej buforu danych wyjściowych.  
  
-   Go można udostępnić pozycję zapisu przydzielając nowej lub dodatkowej pamięci masowej dla buforu danych wyjściowych.  
  
-   Go można udostępnić pozycję zapisu przez wskaźniki pisania wychodzących, niektóre zewnętrznego miejsca docelowego, niektóre lub wszystkie elementy między początkiem i dalej dla buforu danych wyjściowych.  
  
 Funkcja wirtualnej przepełnienia, wraz z [synchronizacji](#sync) i [niedopełnienie](#underflow) funkcje, określa właściwości klasy pochodnej streambuf. Każda klasa pochodna może zastosować przepełnienie inaczej, ale interfejsu w klasie strumienia wywołującego jest taka sama.  
  
 `overflow` Funkcja najczęściej jest wywoływana przez publicznego `streambuf` funkcji, takich jak `sputc` i `sputn` po obszarze put jest pełny, ale inne klasy, w tym klasy strumieni można wywołać `overflow` przy każdym.  
  
 Funkcja zużywa znaków w obszarze put między `pbase` i `pptr` wskaźniki, a następnie ponownie inicjuje obszaru put. `overflow` Musi także korzystać z funkcji `nCh` (Jeśli `nCh` nie jest `EOF`), lub można umieścić tego znaku w nowym wprowadzania obszaru, dzięki czemu będą działały przy następnym wywołaniu.  
  
 Definicja consume zmienia się między klas pochodnych. Na przykład `filebuf` klasy zapisuje jego znaków do pliku, podczas gdy `strstreambuf` klasy przechowuje je w swoim buforze i (Jeśli bufor jest wyznaczony jako dynamiczny) rozszerza w odpowiedzi na wywołanie przepełnienie buforu. To rozwinięcie uzyskuje się poprzez zwalnianie bufor starego i zastępowanie jeden nowy, większy. Wskaźniki są ustawiane w razie potrzeby.  
  
##  <a name="pbackfail"></a>basic_streambuf::pbackfail  
 Chroniony element członkowski wirtualnego funkcję, która próbuje ponownie poddane elementu wejściowego strumienia, należy to zrobić bieżącego elementu (wskazywana przez wskaźnik następnej).  
  
```  
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```  
  
### <a name="parameters"></a>Parametry  
 `_Meta`  
 Znak do wstawienia w buforze, lub **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja nie może się powieść, zwraca **traits_type::eof** lub zgłasza wyjątek. W przeciwnym razie zwraca wartość. Domyślnym zachowaniem jest zwracany **traits_type::eof**.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli _ *Meta* porównuje równa **traits_type::eof**, elementu do usunięcia jest już w strumieniu przed bieżącego elementu. W przeciwnym razie ten element został zastąpiony przez **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*). Funkcja można odłożyć element na różne sposoby:  
  
-   Jeśli pozycja putback jest dostępny, można przechowywać elementu w miejscu putback i zmniejszyć wskaźnik następnej dla buforu wejściowego.  
  
-   Go można udostępnić pozycji putback przydzielając nowej lub dodatkowej pamięci masowej dla buforu wejściowego.  
  
-   Dla buforu strumienia z typowych danych wejściowych i strumienie wyjściowe go można udostępnić pozycji putback przez wskaźniki pisania wychodzących, niektóre zewnętrznego miejsca docelowego, niektóre lub wszystkie elementy między początkiem i dalej dla buforu danych wyjściowych.  
  
##  <a name="pbase"></a>basic_streambuf::pbase  
 Funkcja chronionych, która zwraca wskaźnik do początku buforu wyjściowego.  
  
```  
char_type *pbase() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do początku buforu wyjściowego.  
  
##  <a name="pbump"></a>basic_streambuf::pbump  
 Funkcja chronionych, która dodaje `count` do następnego wskaźnika buforu danych wyjściowych.  
  
```  
void pbump(int count);
```  
  
### <a name="parameters"></a>Parametry  
 `count`  
 Liczba znaków, przez którą ma zostać przeniesiony do przodu pozycję zapisu.  
  
##  <a name="pos_type"></a>basic_streambuf::pos_type  
 Kojarzy nazwę typu w zakresie basic_streambuf — jednego z typów w parametrze szablonu.  
  
```  
typedef typename traits_type::pos_type pos_type;  
```  
  
##  <a name="pptr"></a>basic_streambuf::pptr  
 Funkcja chronionych, która zwraca wskaźnik do następnego elementu buforu wyjściowego.  
  
```  
char_type *pptr() const;
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Wskaźnik do następnego elementu buforu wyjściowego.  
  
##  <a name="pubimbue"></a>basic_streambuf::pubimbue  
 Ustawia obiekt basic_streambuf — ustawień regionalnych.  
  
```  
locale pubimbue(const locale& _Loc);
```  
  
### <a name="parameters"></a>Parametry  
 `_Loc`  
 Odwołanie do ustawień regionalnych.  
  
### <a name="return-value"></a>Wartość zwracana  
 Poprzednia wartość przechowywana w obiekcie ustawień regionalnych.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska przechowuje _ *Loc* w obiekcie ustawień regionalnych i wywołania [imbue](#imbue).  
  
### <a name="example"></a>Przykład  
  Zobacz [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue) na przykład, który używa `pubimbue`.  
  
##  <a name="pubseekoff"></a>basic_streambuf::pubseekoff  
 Wywołania [seekoff](#seekoff), chroniony funkcji wirtualnej, który został zastąpiony w klasie pochodnej.  
  
```  
pos_type pubseekoff(off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Położenie do wyszukania dla względem `_Way`.  
  
 `_Way`  
 Punkt początkowy dla operacji przesunięcia. Zobacz [seekdir](../standard-library/ios-base-class.md#seekdir) prawidłowych wartości.  
  
 `_Which`  
 Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca nowego położenia lub nieprawidłowy strumień pozycji ( [seekoff](#seekoff)(_ *poza*, `_Way`, `_Which`)).  
  
### <a name="remarks"></a>Uwagi  
 Przesuwa wskaźnik względem `_Way`.  
  
##  <a name="pubseekpos"></a>basic_streambuf::pubseekpos  
 Wywołania [seekpos](#seekpos), chroniony funkcji wirtualnej został zastąpiony w klasie pochodnej i resetuje bieżącą pozycję wskaźnika.  
  
```  
pos_type pubseekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>Parametry  
 `_Sp`  
 Położenie do wyszukania dla.  
  
 `_Which`  
 Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowa pozycja lub nieprawidłowy strumień pozycji. Aby ustalić, czy pozycja strumienia jest nieprawidłowa, porównanie wartości zwracanych z `pos_type(off_type(-1))`.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca [seekpos](#seekpos)(_ *Sp*, `_Which`).  
  
##  <a name="pubsetbuf"></a>basic_streambuf::pubsetbuf  
 Wywołania [setbuf](#setbuf), chroniony funkcji wirtualnej, który został zastąpiony w klasie pochodnej.  
  
```  
basic_streambuf<Elem, Tr> *pubsetbuf(
    char_type* _Buffer,  
    streamsize count);
```  
  
### <a name="parameters"></a>Parametry  
 `_Buffer`  
 Wskaźnik do `char_type` dla tego wystąpienia.  
  
 `count`  
 Rozmiar buforu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca [setbuf](#setbuf)( `_Buffer`, `count`).  
  
##  <a name="pubsync"></a>basic_streambuf::pubsync  
 Wywołania [synchronizacji](#sync), chroniony funkcji wirtualnej został zastąpiony w klasie pochodnej, która aktualizuje zewnętrznego strumienia skojarzonego z tym buforu.  
  
```  
int pubsync();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca [synchronizacji](#sync) lub wartość-1 w przypadku awarii.  
  
##  <a name="sbumpc"></a>basic_streambuf::sbumpc  
 Odczytuje i zwraca bieżący element przenoszenie strumienia wskaźnika.  
  
```  
int_type sbumpc();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżącego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli pozycja odczytu jest dostępny, zwraca funkcja członkowska **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)(  **\***  [gptr](#gptr)) i zwiększa wskaźnik następnej dla buforu wejściowego. W przeciwnym razie zwraca [uflow](#uflow).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_streambuf_sbumpc.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )   
{  
   using namespace std;  
   int i = 0;  
   i = cin.rdbuf( )->sbumpc( );  
   cout << i << endl;  
}  
```  
  
```Output  
  
3  
  
```  
  
```Output  
  
      33  
51  
```  
  
##  <a name="seekoff"></a>basic_streambuf::seekoff  
 Funkcja chroniony element członkowski wirtualnego próbuje zmienić bieżącego położenia dla strumieni kontrolowane.  
  
```  
virtual pos_type seekoff(
    off_type _Off,  
    ios_base::seekdir _Way,  
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>Parametry  
 `_Off`  
 Położenie do wyszukania dla względem `_Way`.  
  
 `_Way`  
 Punkt początkowy dla operacji przesunięcia. Zobacz [seekdir](../standard-library/ios-base-class.md#seekdir) prawidłowych wartości.  
  
 `_Which`  
 Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca nowego położenia lub nieprawidłowy strumień pozycji ( `seekoff` (_ *poza*, `_Way`, `_Which`)).  
  
### <a name="remarks"></a>Uwagi  
 Nowa pozycja jest określane w następujący sposób:  
  
-   Jeśli `_Way`  ==  `ios_base::beg`, nowe położenie jest na początku strumienia plus _ *poza*.  
  
-   Jeśli `_Way`  ==  `ios_base::cur`, nowe położenie jest bieżącej pozycji strumienia plus _ *poza*.  
  
-   Jeśli `_Way`  ==  `ios_base::end`, nowe położenie jest koniec strumienia plus _ *poza*.  
  
 Zazwyczaj Jeśli **który & ios_base::in** jest różna od zera, strumień wejściowy jest narażony i w razie **który & ios_base::out** jest różną od zera, strumienia wyjściowego. ma to wpływ na. Rzeczywiste użycie tego parametru zmienia się między bufory pochodnej strumienia, jednak.  
  
 Jeśli funkcja pomyślnie Zmienianie pozycji w strumieniu lub stanowisk IT, zwraca wynikowy pozycji w strumieniu lub jednego z wynikowy pozycji strumienia. W przeciwnym razie zwraca wartość pozycji nieprawidłowy strumień. Domyślnym zachowaniem jest do zwrócenia pozycji nieprawidłowy strumień.  
  
##  <a name="seekpos"></a>basic_streambuf::seekpos  
 Funkcja chroniony element członkowski wirtualnego próbuje zmienić bieżącego położenia dla strumieni kontrolowane.  
  
```  
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```  
  
### <a name="parameters"></a>Parametry  
 `_Sp`  
 Położenie do wyszukania dla.  
  
 `_Which`  
 Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji.  
  
### <a name="return-value"></a>Wartość zwracana  
 Nowa pozycja lub nieprawidłowy strumień pozycji. Aby ustalić, czy pozycja strumienia jest nieprawidłowa, porównanie wartości zwracanych z `pos_type(off_type(-1))`.  
  
### <a name="remarks"></a>Uwagi  
 Nowa pozycja jest _ *Sp*.  
  
 Zazwyczaj Jeśli **który & ios_base::in** jest różna od zera, strumień wejściowy jest narażony i w razie **który & ios_base::out** jest różną od zera, strumienia wyjściowego. ma to wpływ na. Rzeczywiste użycie tego parametru zmienia się między bufory pochodnej strumienia, jednak.  
  
 Jeśli funkcja pomyślnie Zmienianie pozycji w strumieniu lub stanowisk IT, zwraca wynikowy pozycji w strumieniu lub jednego z wynikowy pozycji strumienia. W przeciwnym wypadku zwraca nieprawidłowy strumień pozycji (-1). Domyślnym zachowaniem jest do zwrócenia pozycji nieprawidłowy strumień.  
  
##  <a name="setbuf"></a>basic_streambuf::setbuf  
 Funkcja chronionego członka wirtualnego, która wykonuje określonego operację do każdego strumienia pochodnej buforu.  
  
```  
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,  
    streamsize count);
```  
  
### <a name="parameters"></a>Parametry  
 `_Buffer`  
 Wskaźnik do buforu.  
  
 `count`  
 Rozmiar buforu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślnym zachowaniem jest zwracany **to**.  
  
### <a name="remarks"></a>Uwagi  
 Zobacz [basic_filebuf —](../standard-library/basic-filebuf-class.md). `setbuf`zapewnia to obszar pamięci dla `streambuf` obiekt ma być używany. Sposób użycia buforu w zdefiniowanych w klasach pochodnych.  
  
##  <a name="setg"></a>basic_streambuf::setg  
 Funkcja chronionych, która przechowuje _ *Gbeg* we wskaźniku początku `_Gnext` w wskaźnik następnej i `_Gend` we wskaźniku zakończenia dla buforu wejściowego.  
  
```  
void setg(char_type* _Gbeg,
    char_type* _Gnext,
    char_type* _Gend);
```  
  
### <a name="parameters"></a>Parametry  
 *_Gbeg*  
 Wskaźnik do początku buforu.  
  
 `_Gnext`  
 Wskaźnik do lokalizacji środku buforu.  
  
 `_Gend`  
 Wskaźnik do końca buforu.  
  
##  <a name="setp"></a>basic_streambuf::setp  
 Funkcja chronionych, która przechowuje `_Pbeg` we wskaźniku początku i `_Pend` we wskaźniku końcowego buforu danych wyjściowych.  
  
```  
void setp(char_type* _Pbeg, char_type* _Pend);
```  
  
### <a name="parameters"></a>Parametry  
 `_Pbeg`  
 Wskaźnik do początku buforu.  
  
 `_Pend`  
 Wskaźnik do końca buforu.  
  
##  <a name="sgetc"></a>basic_streambuf::sgetc  
 Zwraca bieżący element bez zmiany pozycji w strumieniu.  
  
```  
int_type sgetc();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżącego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli pozycja odczytu jest dostępny, zwraca funkcja członkowska **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*` [gptr](#gptr)). W przeciwnym razie zwraca [niedopełnienie](#underflow).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_streambuf_sgetc.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
   ifstream myfile( "basic_streambuf_sgetc.txt", ios::in );  
  
   char i = myfile.rdbuf( )->sgetc( );  
   cout << i << endl;  
   i = myfile.rdbuf( )->sgetc( );  
   cout << i << endl;  
}  
```  
  
##  <a name="sgetn"></a>basic_streambuf::sgetn  
 Wyodrębnia do `count` znaków z buforu wejściowego i przechowuje je w buforze podana `ptr`.  
  
 Ta metoda jest potencjalnie niebezpieczne, ponieważ zależy od obiekt wywołujący, aby sprawdzić, czy przekazane wartości są poprawne.  
  
```  
streamsize sgetn(
    char_type* ptr,  
    streamsize count);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Bufor zawiera wyodrębnione znaki.  
  
 `count`  
 Liczba elementów do odczytu.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów do odczytu. Zobacz [streamsize](../standard-library/ios-typedefs.md#streamsize) Aby uzyskać więcej informacji.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca [xsgetn](#xsgetn)( `ptr`, `count`).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_streambuf_sgetn.cpp  
// compile with: /EHsc /W3  
#include <iostream>  
#include <fstream>  
  
int main()  
{  
    using namespace std;  
  
    ifstream myfile("basic_streambuf_sgetn.txt", ios::in);  
    char a[10];  
  
    // Extract 3 characters from myfile and store them in a.  
    streamsize i = myfile.rdbuf()->sgetn(&a[0], 3);  // C4996  
    a[i] = myfile.widen('\0');  
  
    // Display the size and contents of the buffer passed to sgetn.  
    cout << i << " " << a << endl;  
  
    // Display the contents of the original input buffer.  
    cout << myfile.rdbuf() << endl;  
}  
```  
  
##  <a name="showmanyc"></a>basic_streambuf::showmanyc  
 Funkcja chroniony element członkowski wirtualnego, która zwraca liczbę liczbę znaków, które można wyodrębnić ze strumienia wejściowego i upewnij się, że program nie będzie podlegał nieograniczonego oczekiwania.  
  
```  
virtual streamsize showmanyc();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Domyślnym zachowaniem jest do zwrócenia zero.  
  
##  <a name="snextc"></a>basic_streambuf::snextc  
 Odczytuje bieżący element i zwraca następujący element.  
  
```  
int_type snextc();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Następny element w strumieniu.  
  
### <a name="remarks"></a>Uwagi  
 Wywołania funkcji Członkowskich [sbumpc](#sbumpc) i, jeśli ta funkcja zwróci **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), zwraca **traits_type::eof**. W przeciwnym razie zwraca [sgetc](#sgetc).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_streambuf_snextc.cpp  
// compile with: /EHsc  
#include <iostream>  
int main( )   
{  
   using namespace std;  
   int i = 0;  
   i = cin.rdbuf( )->snextc( );  
   // cout << ( int )char_traits<char>::eof << endl;  
   cout << i << endl;  
}  
```  
  
```Output  
  
aa  
  
```  
  
```Output  
  
aa97  
```  
  
##  <a name="sputbackc"></a>basic_streambuf::sputbackc  
 Umieszcza char_type w strumieniu.  
  
```  
int_type sputbackc(char_type _Ch);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 Znak.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca znak lub niepowodzenie.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli pozycja putback jest dostępny i `_Ch` porównuje równa się znak przechowywane w tym położeniu zmniejsza funkcji Członkowskich wskaźnik następnej buforu wejściowego i zwraca **traits_type::**[to_int_ Typ](../standard-library/char-traits-struct.md#to_int_type)( `_Ch`). W przeciwnym razie zwraca [pbackfail](#pbackfail)( `_Ch`).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_streambuf_sputbackc.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )  
{  
    using namespace std;  
  
    ifstream myfile("basic_streambuf_sputbackc.txt",  
        ios::in);  
  
    int i = myfile.rdbuf()->sbumpc();  
    cout << (char)i << endl;  
    int j = myfile.rdbuf()->sputbackc('z');  
    if (j == 'z')  
    {  
        cout << "it worked" << endl;  
    }  
    i = myfile.rdbuf()->sgetc();  
    cout << (char)i << endl;  
}  
```  
  
##  <a name="sputc"></a>basic_streambuf::sputc  
 Umieszcza znak w strumieniu.  
  
```  
int_type sputc(char_type _Ch);
```  
  
### <a name="parameters"></a>Parametry  
 `_Ch`  
 Znak.  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca znak, jeśli to się powiedzie.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli `write position` jest dostępna, magazyny funkcji Członkowskich `_Ch` pozycji zapisu zwiększa wskaźnik następnej dla buforu wyjściowego i zwraca **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)() `_Ch`). W przeciwnym razie zwraca [przepełnienie](#overflow)( `_Ch`).  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_streambuf_sputc.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
  
   int i = cout.rdbuf( )->sputc( 'a' );  
   cout << endl << ( char )i << endl;  
}  
```  
  
```Output  
a  
a  
```  
  
##  <a name="sputn"></a>basic_streambuf::sputn  
 Umieszcza ciąg znaków w strumieniu.  
  
```  
streamsize sputn(const char_type* ptr, streamsize count);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Ciąg znaków.  
  
 `count`  
 Liczba znaków.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba znaków wstawiony do strumienia.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja członkowska zwraca [xsputn](#xsputn)( `ptr`, `count`). Zobacz sekcję uwag ten element członkowski, aby uzyskać więcej informacji.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_streambuf_sputn.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main()  
{  
    using namespace std;  
  
    streamsize i = cout.rdbuf()->sputn("test", 4);  
    cout << endl << i << endl;  
}  
```  
  
```Output  
test  
4  
```  
  
##  <a name="stossc"></a>basic_streambuf::stossc  
 Przenieś poza bieżący element w strumieniu.  
  
```  
void stossc();
```  
  
### <a name="remarks"></a>Uwagi  
 Wywołania funkcji Członkowskich [sbumpc](#sbumpc). Należy pamiętać, że implementacja interfejsu nie jest wymagane do dostarczania funkcji członkowskiej.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_streambuf_stossc.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
   ifstream myfile( "basic_streambuf_stossc.txt", ios::in );  
  
   myfile.rdbuf( )->stossc( );  
   char i = myfile.rdbuf( )->sgetc( );  
   cout << i << endl;  
}  
```  
  
##  <a name="sungetc"></a>basic_streambuf::sungetc  
 Pobiera znak ze strumienia.  
  
```  
int_type sungetc();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Zwraca znak lub niepowodzenie.  
  
### <a name="remarks"></a>Uwagi  
 Jeśli pozycja putback jest dostępny, funkcji członkowskiej zmniejsza wskaźnik następnej buforu wejściowego i zwraca `traits_type::` [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*` [gptr](#gptr)). Jednakże nie jest zawsze można określić ostatniego odczytu znak, dzięki czemu można przechwycić stan bieżący bufor. Jeśli to PRAWDA, funkcja zwraca [pbackfail](#pbackfail). Aby tego uniknąć, przechowywać informacje o znak odłożyć i Wywołaj `sputbackc(ch)`, które nie zostaną przełączone podana możesz nie wywołują go na początku strumienia i nie zostanie podjęta próba odłożyć więcej niż jednego znaku.  
  
### <a name="example"></a>Przykład  
  
```cpp  
// basic_streambuf_sungetc.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main( )   
{  
   using namespace std;  
  
   ifstream myfile( "basic_streambuf_sungetc.txt", ios::in );  
  
   // Read and increment  
   int i = myfile.rdbuf( )->sbumpc( );  
   cout << ( char )i << endl;  
  
   // Read and increment  
   i = myfile.rdbuf( )->sbumpc( );  
   cout << ( char )i << endl;  
  
   // Decrement, read, and do not increment  
   i = myfile.rdbuf( )->sungetc( );  
   cout << ( char )i << endl;  
  
   i = myfile.rdbuf( )->sungetc( );   
   cout << ( char )i << endl;  
  
   i = myfile.rdbuf( )->sbumpc( );  
   cout << ( char )i << endl;  
}  
```  
  
##  <a name="swap"></a>basic_streambuf::swap  
 Zamienia wartości w tym obiekcie dla wartości w określonych `basic_streambuf` obiektu.  
  
```  
void swap(basic_streambuf& right);
```  
  
### <a name="parameters"></a>Parametry  
  
|Parametr|Opis|  
|---------------|-----------------|  
|`right`|Odwołania do wartości do `basic_streambuf` obiekt, który jest używany do wymiany wartości.|  
  
### <a name="remarks"></a>Uwagi  
 Funkcja chroniony element członkowski wymiany z `right` wszystkie wskaźniki kontrolowanie `input buffer` i `output buffer`. Również wymienia `right.` [getloc()](#getloc) z `locale` obiektu.  
  
##  <a name="sync"></a>basic_streambuf::Sync  
 Chronione funkcji wirtualnej próbuje synchronizować kontrolowane strumieni wszystkie skojarzone strumieni zewnętrznych.  
  
```  
virtual int sync();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Jeśli funkcja nie może się powieść, zwraca -1. Domyślnym zachowaniem jest do zwrócenia zero.  
  
### <a name="remarks"></a>Uwagi  
 `sync`obejmuje zapisywania elementów między wskaźniki początkowe i dalej buforu wyjściowego. Nie obejmuje ponownie umieszczanie elementów między następnej i kończyć wskaźniki buforu wejściowego.  
  
##  <a name="traits_type"></a>basic_streambuf::traits_type  
 Kojarzy nazwę typu z **Tr** parametru szablonu.  
  
```  
typedef Tr traits_type;  
```  
  
##  <a name="uflow"></a>basic_streambuf::uflow  
 Chronione funkcji wirtualnej wyodrębnia bieżącego elementu ze strumienia wejściowego.  
  
```  
virtual int_type uflow();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżącego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja chroniony element członkowski wirtualnego próbuje wyodrębnić bieżącego elementu **ch** ze strumienia wejściowego, następnie poprawić bieżącej pozycji strumienia i zwracać element jako **traits_type::** [ to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**). Go to zrobić na różne sposoby:  
  
-   Jeśli pozycja odczytu jest dostępny, przyjmuje **ch** jako element przechowywane w pozycji odczytu i przesuwa wskaźnik następnej dla buforu wejściowego.  
  
-   Można odczytywać element bezpośrednio z zewnętrznego źródła i dostarcza go jako wartość **ch**.  
  
-   Dla buforu strumienia z typowych danych wejściowych i strumienie wyjściowe go można udostępnić odczytu pozycji przez wskaźniki pisania wychodzących, niektóre zewnętrznego miejsca docelowego, niektóre lub wszystkie elementy między początkiem i dalej dla buforu danych wyjściowych. Lub go przydzielić nowej lub dodatkowej pamięci masowej dla buforu wejściowego. Funkcja odczytuje go w, z niektórych źródła zewnętrznego, co najmniej jeden element.  
  
 Jeśli funkcja nie może się powieść, zwraca **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), lub zgłasza wyjątek. W przeciwnym razie zwraca bieżący element `ch` w strumieniu wejściowym przekonwertować zgodnie z powyższym opisem, a przesuwa wskaźnik następnej dla buforu wejściowego. Domyślnym zachowaniem jest wywołać [niedopełnienie](#underflow) i, jeśli ta funkcja zwróci **traits_type::eof**, aby zwrócić **traits_type::eof**. W przeciwnym razie funkcja zwraca bieżący element **ch** w strumieniu wejściowym konwertowane, jak opisano wcześniej, a przesuwa wskaźnik następnej dla buforu wejściowego.  
  
##  <a name="underflow"></a>basic_streambuf::underflow  
 Chronione funkcji wirtualnych można wyodrębnić bieżącego elementu ze strumienia wejściowego.  
  
```  
virtual int_type underflow();
```  
  
### <a name="return-value"></a>Wartość zwracana  
 Bieżącego elementu.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja chroniony element członkowski wirtualnego usiłują wyodrębnić bieżącego elementu **ch** ze strumienia wejściowego bez przesuwania bieżącej pozycji strumienia i przywrócić go jako `traits_type::` [to_int_type](../standard-library/char-traits-struct.md#to_int_type)() **ch**). Go to zrobić na różne sposoby:  
  
-   Jeśli jest dostępne, pozycja odczytu **ch** jest przechowywane w pozycji odczytu elementu. Aby uzyskać więcej informacji na ten, zobacz sekcję uwag [basic_streambuf — klasa](../standard-library/basic-streambuf-class.md).  
  
-   Go można udostępnić odczytu pozycji przydzielając nowej lub dodatkowej pamięci masowej dla buforu wejściowego, następnie odczytu, z niektórych źródła zewnętrznego, co najmniej jeden element. Aby uzyskać więcej informacji na ten, zobacz sekcję uwag [basic_streambuf — klasa](../standard-library/basic-streambuf-class.md).  
  
 Jeśli funkcja nie może się powieść, zwraca `traits_type::` [eof](../standard-library/char-traits-struct.md#eof) `()` lub zgłasza wyjątek. W przeciwnym wypadku zwraca bieżący element w strumieniu wejściowym przekonwertować opisana powyżej. Domyślnym zachowaniem jest zwracany `traits_type::eof()`.  
  
 Wirtualne `underflow` funkcji, z [synchronizacji](#sync) i [przepełnienie](#overflow) funkcje, określa właściwości `streambuf`-klasy. Każda klasa pochodna może zastosować `underflow` inaczej, ale interfejsu w klasie strumienia wywołującego jest taka sama.  
  
 `underflow` Funkcja najczęściej jest wywoływana przez publicznego `streambuf` funkcji, takich jak [sgetc](#sgetc) i [sgetn](#sgetn) po obszarze get jest pusty, ale można wywołać innych klas, w tym klasy strumieni `underflow` przy każdym.  
  
 `underflow` Funkcja dostarcza get obszaru ze znakami ze źródła danych wejściowych. Jeśli obszar get zawiera znaki, `underflow` zwraca pierwszy znak. Jeśli obszar get jest pusta, wypełnia obszar get i zwraca następny znak (co pozostawia w obszarze get). Jeśli nie dostępnych nie więcej znaków, następnie `underflow` zwraca `EOF` i opuszcza obszar get jest pusta.  
  
 W `strstreambuf` klasy `underflow` dostosowuje [egptr](#egptr) wskaźnik do dostęp do magazynu, który został dynamicznie przydzielane przez wywołanie do `overflow`.  
  
##  <a name="xsgetn"></a>basic_streambuf::xsgetn  
 Chronione funkcji wirtualnych można wyodrębnić elementów ze strumienia wejściowego.  
  
 Ta metoda jest potencjalnie niebezpieczne, ponieważ zależy od obiekt wywołujący, aby sprawdzić, czy przekazane wartości są poprawne.  
  
```  
virtual streamsize xsgetn(
    char_type* ptr,  
    streamsize count);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Bufor zawiera wyodrębnione znaki.  
  
 `count`  
 Liczba elementów do wyodrębnienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów wyodrębnione.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja chroniony element członkowski wirtualnego wyodrębnia do `count` elementy ze strumienia wejściowego funkcję Jeśli powtarzane wywołania [sbumpc](#sbumpc)i zapisuje je w tablicy, rozpoczynający się od `ptr`. Zwraca liczbę elementów faktycznie wyodrębnione.  
  
##  <a name="xsputn"></a>basic_streambuf::xsputn  
 Chronione funkcji wirtualnych do wstawienia elementów do strumienia wyjściowego.  
  
```  
virtual streamsize xsputn(const char_type* ptr, streamsize count);
```  
  
### <a name="parameters"></a>Parametry  
 `ptr`  
 Wskaźnik do elementów do wstawienia.  
  
 `count`  
 Liczba elementów do wstawienia.  
  
### <a name="return-value"></a>Wartość zwracana  
 Liczba elementów wstawiony do strumienia.  
  
### <a name="remarks"></a>Uwagi  
 Funkcja chroniony element członkowski wirtualnego wstawia do `count` strumienia elementów w danych wyjściowych, tak jakby przez powtarzane wywołania [sputc](#sputc), od początku tablicy w `ptr`. Wstawianie znaków do strumienia wyjściowego raz zatrzymuje wszystkie `count` znaków zostały zapisane, lub jeśli wywołanie `sputc( count)` zwróci `traits::eof()`. Zwraca liczbę elementów wstawiony.  
  
## <a name="see-also"></a>Zobacz też  
 [Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream — programowanie](../standard-library/iostream-programming.md)   
 [Konwencje iostream](../standard-library/iostreams-conventions.md)

