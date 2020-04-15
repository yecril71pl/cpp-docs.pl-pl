---
title: basic_streambuf — Klasa
ms.date: 11/04/2016
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
ms.openlocfilehash: 0cf7b61bde86a4643836346dafd36680fb8cf302
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376740"
---
# <a name="basic_streambuf-class"></a>basic_streambuf — Klasa

W tym artykule opisano abstrakcyjną klasę podstawową dla wyprowadzania buforu strumienia, który kontroluje transmisję elementów do i z określonej reprezentacji strumienia.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_streambuf;
```

### <a name="parameters"></a>Parametry

*Elem*\
[char_type](#char_type).

*Tr*\
Znak [traits_type](#traits_type).

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje abstrakcyjną klasę podstawową do wyprowadzania buforu strumienia, który steruje transmisją elementów do i z określonej reprezentacji strumienia. Obiekt `basic_streambuf` klasy pomaga kontrolować strumień za pomocą elementów typu *Tr*, znany również jako [char_type](#char_type), których cechy charakteru są określane przez klasę [char_traits](../standard-library/char-traits-struct.md), znany również jako [traits_type](#traits_type).

Każdy bufor strumienia koncepcyjnie kontroluje dwa niezależne strumienie: jeden dla ekstrakcji (wejście) i jeden dla wstawień (wyjście). Konkretna reprezentacja może jednak sprawić, że jeden lub oba te strumienie będą niedostępne. Zazwyczaj utrzymuje pewne relacje między dwoma strumieniami. Co można wstawić do strumienia wyjściowego `Tr` [basic_stringbuf](../standard-library/basic-stringbuf-class.md)< `Elem`,> obiektu, na przykład, jest to, co później wyodrębnić z jego strumienia wejściowego. Po umieszczeniu jednego strumienia [basic_filebuf](../standard-library/basic-filebuf-class.md)< `Elem` `Tr` ,> obiektu, można umieścić drugi strumień w tandemie.

Interfejs publiczny do `basic_streambuf` szablonu klasy dostarcza operacje, które są wspólne dla wszystkich buforów strumienia, jednak wyspecjalizowane. Chroniony interfejs dostarcza operacje potrzebne do określonej reprezentacji strumienia do wykonywania swojej pracy. Chronione funkcje wirtualnego elementu członkowskiego umożliwiają dostosowanie zachowania buforu strumienia pochodnego dla określonej reprezentacji strumienia. Każdy bufor strumienia pochodnego w tej bibliotece opisuje, jak specjalizuje się zachowanie jego chronionych funkcji wirtualnego elementu członkowskiego. Domyślne zachowanie dla klasy podstawowej, która często nic nie robi, jest opisane w tym temacie.

Pozostałe chronione funkcje członkowskie kontrolują kopiowanie do i z dowolnego magazynu dostarczonego do transmisji buforu do i ze strumieni. Bufor wejściowy, na przykład, charakteryzuje się:

- [eback](#eback), wskaźnik do początku buforu.

- [gptr](#gptr), wskaźnik do następnego elementu do odczytu.

- [egptr](#egptr), wskaźnik tuż za końcem buforu.

Podobnie bufor wyjściowy charakteryzuje się:

- [pbase](#pbase), wskaźnik do początku buforu.

- [pptr](#pptr), wskaźnik do następnego elementu do zapisu.

- [epptr](#epptr), wskaźnik tuż za końcem buforu.

Dla dowolnego bufora używany jest następujący protokół:

- Jeśli następny wskaźnik ma wartość null, nie istnieje bufor. W przeciwnym razie wszystkie trzy wskaźniki wskazują na tej samej sekwencji. Można je bezpiecznie porównać na zamówienie.

- W przypadku buforu wyjściowego, jeśli następny wskaźnik porównuje mniej niż wskaźnik końcowy, można przechowywać element w pozycji zapisu wyznaczonej przez następny wskaźnik.

- W przypadku buforu wejściowego, jeśli następny wskaźnik porównuje mniej niż wskaźnik końcowy, można odczytać element w pozycji odczytu wyznaczonej przez następny wskaźnik.

- W przypadku buforu wejściowego, jeśli wskaźnik początkowy porównuje mniej niż następny wskaźnik, można umieścić z powrotem element w pozycji putback wyznaczony przez zdezwał się następny wskaźnik.

Wszelkie chronione funkcje wirtualnego elementu członkowskiego, `basic_streambuf` <  `Elem` `Tr` które piszesz dla klasy pochodzącej od> muszą współpracować przy utrzymaniu tego protokołu.

Obiekt `basic_streambuf` <  `Elem`klasy , `Tr`> przechowuje sześć wskaźników wcześniej opisane. Przechowuje również obiekt ustawień regionalnych w obiekcie [ustawień regionalnych](../standard-library/locale-class.md) typu do potencjalnego wykorzystania przez bufor strumienia pochodnego.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_streambuf](#basic_streambuf)|Konstruuje obiekt `basic_streambuf`typu .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[Char_type](#char_type)|Kojarzy nazwę typu `Elem` z parametrem szablonu.|
|[Int_type](#int_type)|Kojarzy nazwę typu `basic_streambuf` w `Elem` zakresie z parametrem szablonu.|
|[off_type](#off_type)|Kojarzy nazwę typu `basic_streambuf` w `Elem` zakresie z parametrem szablonu.|
|[pos_type](#pos_type)|Kojarzy nazwę typu `basic_streambuf` w `Elem` zakresie z parametrem szablonu.|
|[traits_type](#traits_type)|Kojarzy nazwę typu `Tr` z parametrem szablonu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[eback (eback)](#eback)|Funkcja chroniona, która zwraca wskaźnik na początku buforu wejściowego.|
|[egptr ( egptr )](#egptr)|Funkcja chroniona, która zwraca wskaźnik tuż za końcem buforu wejściowego.|
|[epptr](#epptr)|Funkcja chroniona, która zwraca wskaźnik tuż za końcem buforu wyjściowego.|
|[gbump](#gbump)|Funkcja chroniona, `count` która dodaje do następnego wskaźnika dla buforu wejściowego.|
|[getlok](#getloc)|Pobiera `basic_streambuf` ustawienia regionalne obiektu.|
|[gptr (gptr)](#gptr)|Funkcja chroniona, która zwraca wskaźnik do następnego elementu buforu wejściowego.|
|[Nasycić](#imbue)|Chroniona, wirtualna funkcja wywoływana przez [pubimbue](#pubimbue).|
|[in_avail](#in_avail)|Zwraca liczbę elementów, które są gotowe do odczytania z bufora.|
|[Przepełnienie](#overflow)|Chroniona funkcja wirtualna, która może być wywoływana po wstawieniu nowego znaku do pełnego buforu.|
|[pbackfail](#pbackfail)|Funkcja chronionego elementu członkowskiego wirtualnego, która próbuje umieścić z powrotem element do strumienia wejściowego, a następnie uczynić go bieżącym elementem (wskazywała na następny wskaźnik).|
|[Pbase](#pbase)|Funkcja chroniona, która zwraca wskaźnik na początku buforu wyjściowego.|
|[pbump](#pbump)|Funkcja chroniona, `count` która dodaje do następnego wskaźnika dla buforu wyjściowego.|
|[pptr (polski)](#pptr)|Funkcja chroniona, która zwraca wskaźnik do następnego elementu buforu wyjściowego.|
|[pubimbue ( pubimbue )](#pubimbue)|Ustawia `basic_streambuf` ustawienia regionalne obiektu.|
|[pubseekoff](#pubseekoff)|Wywołania [seekoff](#seekoff), chronionej funkcji wirtualnej, która jest zastępowana w klasie pochodnej.|
|[pubseekpos](#pubseekpos)|Wywołuje [seekpos](#seekpos), chronioną funkcję wirtualną, która jest zastępowana w klasie pochodnej i resetuje bieżącą pozycję wskaźnika.|
|[pubsetbuf](#pubsetbuf)|Wywołuje [setbuf](#setbuf), chronioną funkcję wirtualną, która jest zastępowana w klasie pochodnej.|
|[pubsync](#pubsync)|Wywołuje [sync](#sync), chronioną funkcję wirtualną, która jest zastępowana w klasie pochodnej i aktualizuje strumień zewnętrzny skojarzony z tym buforem.|
|[sbumpc (właśc.](#sbumpc)|Odczytuje i zwraca bieżący element, przesuwając wskaźnik strumienia.|
|[poszukiwanie](#seekoff)|Funkcja chronionego wirtualnego elementu członkowskiego próbuje zmienić bieżące pozycje dla kontrolowanych strumieni.|
|[seekpos](#seekpos)|Funkcja chronionego wirtualnego elementu członkowskiego próbuje zmienić bieżące pozycje dla kontrolowanych strumieni.|
|[setbuf](#setbuf)|Funkcja chronionego elementu członkowskiego wirtualnego wykonuje operację określoną dla każdego buforu strumienia pochodnego.|
|[setg ( setg )](#setg)|Funkcja chroniona, `_Gbeg` która przechowuje `_Gnext` w wskaźniku początkowym, w następnym wskaźniku i `_Gend` w wskaźniku końcowym dla buforu wejściowego.|
|[setp (setp)](#setp)|Funkcja chroniona, `_Pbeg` która przechowuje `_Pend` w wskaźniku początkowym i w wskaźniku końcowym dla buforu wyjściowego.|
|[sgetc ( sgetc )](#sgetc)|Zwraca bieżący element bez zmiany pozycji w strumieniu.|
|[sgetn (sgetn)](#sgetn)|Zwraca liczbę odczytanych elementów.|
|[showmanyc (showmanyc)](#showmanyc)|Funkcja chronionego wirtualnego elementu członkowskiego, która zwraca liczbę znaków, które mogą być wyodrębnione ze strumienia wejściowego i upewnij się, że program nie będzie podlegać nieokreślony czekać.|
|[snextc](#snextc)|Odczytuje bieżący element i zwraca następujący element.|
|[sputbackc ( sputbackc )](#sputbackc)|Umieszcza `char_type` w strumieniu.|
|[sputc ( sputc )](#sputc)|Umieszcza znak w strumieniu.|
|[sputn (sputn)](#sputn)|Umieszcza ciąg znaków w strumieniu.|
|[stossc](#stossc)|Przesuń obok bieżącego elementu w strumieniu.|
|[sungetc (sungetc)](#sungetc)|Pobiera znak ze strumienia.|
|[Wymiany](#swap)|Wymienia wartości w tym obiekcie dla `basic_streambuf` wartości w parametrze podanym obiektem.|
|[synchronizacja](#sync)|Chroniona funkcja wirtualna, która próbuje zsynchronizować kontrolowane strumienie z wszelkimi skojarzonymi strumieniami zewnętrznymi.|
|[uflow (polski)](#uflow)|Chroniona funkcja wirtualna, która wyodrębnia bieżący element ze strumienia wejściowego.|
|[Niedomiar](#underflow)|Chroniona funkcja wirtualna, która wyodrębnia bieżący element ze strumienia wejściowego.|
|[xsgetn ( xsgetn )](#xsgetn)|Chroniona funkcja wirtualna, która wyodrębnia elementy ze strumienia wejściowego.|
|[xsputn ( xsputn )](#xsputn)|Chroniona funkcja wirtualna, która wstawia elementy do strumienia wyjściowego.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje wartości tego obiektu z `basic_streambuf` innego obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<streambuf>

**Przestrzeń nazw:** std

## <a name="basic_streambufbasic_streambuf"></a><a name="basic_streambuf"></a>basic_streambuf::basic_streambuf

Konstruuje obiekt `basic_streambuf`typu .

```cpp
basic_streambuf();

basic_streambuf(const basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Odwołanie lvalue do `basic_streambuf` obiektu, który jest używany `basic_streambuf` do ustawiania wartości dla tego obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy chroniony konstruktor przechowuje wskaźnik null we wszystkich wskaźnikach sterujących buforem wejściowym i buforem wyjściowym. Przechowuje `locale::classic` również w obiekcie ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [ustawienia regionalne::classic](../standard-library/locale-class.md#classic).

Drugi chroniony konstruktor kopiuje wskaźniki i ustawienia regionalne z *prawej .*

## <a name="basic_streambufchar_type"></a><a name="char_type"></a>basic_streambuf::char_type

Kojarzy nazwę typu z parametrem szablonu **Elem.**

```cpp
typedef Elem char_type;
```

## <a name="basic_streambufeback"></a><a name="eback"></a>basic_streambuf::eback

Funkcja chroniona, która zwraca wskaźnik na początku buforu wejściowego.

```cpp
char_type *eback() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku buforu wejściowego.

## <a name="basic_streambufegptr"></a><a name="egptr"></a>basic_streambuf::egptr

Funkcja chroniona, która zwraca wskaźnik tuż za końcem buforu wejściowego.

```cpp
char_type *egptr() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik tuż za końcem buforu wejściowego.

## <a name="basic_streambufepptr"></a><a name="epptr"></a>basic_streambuf::epltr

Funkcja chroniona, która zwraca wskaźnik tuż za końcem buforu wyjściowego.

```cpp
char_type *epptr() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik tuż za końcem buforu wyjściowego.

## <a name="basic_streambufgbump"></a><a name="gbump"></a>basic_streambuf::gbump

Funkcja chroniona, która dodaje *liczbę* do następnego wskaźnika dla buforu wejściowego.

```cpp
void gbump(int count);
```

### <a name="parameters"></a>Parametry

*Liczba*\
Kwota, o którą należy przejść wskaźnik.

## <a name="basic_streambufgetloc"></a><a name="getloc"></a>basic_streambuf::getloc

Pobiera ustawienia regionalne obiektu basic_streambuf.

```cpp
locale getloc() const;
```

### <a name="return-value"></a>Wartość zwracana

Przechowywany obiekt ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje, zobacz [ios_base::getloc](../standard-library/ios-base-class.md#getloc).

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

## <a name="basic_streambufgptr"></a><a name="gptr"></a>basic_streambuf::gptr

Funkcja chroniona, która zwraca wskaźnik do następnego elementu buforu wejściowego.

```cpp
char_type *gptr() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego elementu buforu wejściowego.

## <a name="basic_streambufimbue"></a><a name="imbue"></a>basic_streambuf::imbue

Chroniona funkcja wirtualna wywoływana przez [pubimbue](#pubimbue).

```cpp
virtual void imbue(const locale& _Loc);
```

### <a name="parameters"></a>Parametry

*_Loc*\
Odwołanie do ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Domyślnym zachowaniem jest nic nie robić.

## <a name="basic_streambufin_avail"></a><a name="in_avail"></a>basic_streambuf::in_avail

Zwraca liczbę elementów, które są gotowe do odczytania z bufora.

```cpp
streamsize in_avail();
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, które są gotowe do odczytania z bufora.

### <a name="remarks"></a>Uwagi

Jeśli [pozycja odczytu](../standard-library/basic-streambuf-class.md) jest dostępna, funkcja elementu członkowskiego zwraca [egptr](#egptr) - [gptr](#gptr). W przeciwnym razie zwraca [showmanyc](#showmanyc).

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

## <a name="basic_streambufint_type"></a><a name="int_type"></a>basic_streambuf::int_type

Kojarzy nazwę typu w zakresie basic_streambuf z jednym z typów w parametrze szablonu.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_streambufoff_type"></a><a name="off_type"></a>basic_streambuf::off_type

Kojarzy nazwę typu w zakresie basic_streambuf z jednym z typów w parametrze szablonu.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_streambufoperator"></a><a name="op_eq"></a>basic_streambuf::operator=

Przypisuje wartości tego obiektu z `basic_streambuf` innego obiektu.

```cpp
basic_streambuf& operator=(const basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

*Prawo*\
Odwołanie lvalue do `basic_streambuf` obiektu, który jest używany do przypisywania wartości do tego obiektu.

### <a name="remarks"></a>Uwagi

Operator chronionego elementu członkowskiego kopiuje z *prawej* wskaźniki, które kontrolują bufor wejściowy i bufor wyjściowy. Przechowuje `right.`również [getloc()](#getloc) w `locale object`. Zwraca `*this`.

## <a name="basic_streambufoverflow"></a><a name="overflow"></a>basic_streambuf::przepełnienie

Chroniona funkcja wirtualna, która może być wywoływana po wstawieniu nowego znaku do pełnego buforu.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, który ma być wstawiany do bufora lub **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może zakończyć się pomyślnie, zwraca **traits_type::eof** lub zgłasza wyjątek. W przeciwnym razie zwraca **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*). Domyślnym zachowaniem jest zwrócenie **traits_type::eof**.

### <a name="remarks"></a>Uwagi

Jeśli * \_Meta* nie porównuje **się równa traits_type::eof**, funkcja chronionego elementu członkowskiego wirtualnego stara się wstawić element **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_Meta*) do strumienia wyjściowego. Może to zrobić na różne sposoby:

- Jeśli `write position` jest dostępny, może przechowywać element w pozycji zapisu i przyrost następnego wskaźnika dla buforu wyjściowego.

- Może udostępnić pozycję zapisu, przydzielając nowe lub dodatkowe miejsce do magazynowania buforu wyjściowego.

- Może udostępnić pozycję zapisu, zapisując do jakiegoś zewnętrznego miejsca docelowego, niektóre lub wszystkie elementy między początkiem i następnym wskaźniki dla buforu wyjściowego.

Funkcja przepełnienia wirtualnego, wraz z funkcjami [synchronizacji](#sync) i [niedopełnienia,](#underflow) definiuje właściwości klasy pochodnej streambuf. Każda klasa pochodna może implementować przepełnienie inaczej, ale interfejs z wywołaną klasą strumienia jest taka sama.

Funkcja `overflow` jest najczęściej wywoływana `streambuf` przez `sputc` funkcje publiczne, takie jak i `sputn` gdy obszar put jest `overflow` pełny, ale inne klasy, w tym klasy strumienia, można wywołać w dowolnym momencie.

Funkcja zużywa znaki w obszarze put `pbase` między `pptr` i wskaźników, a następnie ponownie inicjuje put area. Funkcja `overflow` musi również `nCh` zużywać `nCh` `EOF`(jeśli nie), lub może zdecydować się umieścić ten znak w nowym obszarze put, tak aby był zużywany przy następnym wywołaniu.

Definicja zużycia różni się w zależności od klasy pochodnej. Na przykład `filebuf` klasa zapisuje swoje znaki do `strstreambuf` pliku, podczas gdy klasa przechowuje je w buforze i (jeśli bufor jest wyznaczony jako dynamiczny) rozszerza bufor w odpowiedzi na wywołanie przepełnienia. Ekspansja ta jest osiągana poprzez uwolnienie starego bufora i zastąpienie go nowym, większym. Wskaźniki są dostosowywane w razie potrzeby.

## <a name="basic_streambufpbackfail"></a><a name="pbackfail"></a>basic_streambuf::pbackfail

Funkcja chronionego elementu członkowskiego wirtualnego, która próbuje umieścić z powrotem element do strumienia wejściowego, a następnie uczynić go bieżącym elementem (wskazywała na następny wskaźnik).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, który ma być wstawiany do bufora lub **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może zakończyć się pomyślnie, zwraca **traits_type::eof** lub zgłasza wyjątek. W przeciwnym razie zwraca inną wartość. Domyślnym zachowaniem jest zwrócenie **traits_type::eof**.

### <a name="remarks"></a>Uwagi

Jeśli * \_Meta* porównuje się równa **traits_type::eof**, element do odepchnięcia jest skutecznie ten, który jest już w strumieniu przed bieżącym elementem. W przeciwnym razie ten element jest zastępowany **przez traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_Meta*). Funkcja może umieścić z powrotem element na różne sposoby:

- Jeśli pozycja putback jest dostępna, może przechowywać element w pozycji putback i zmniejszać następny wskaźnik dla buforu wejściowego.

- Może udostępnić pozycję putback, przydzielając nowe lub dodatkowe miejsce do magazynowania dla buforu wejściowego.

- Dla buforu strumienia ze wspólnymi strumieniami wejściowymi i wyjściowymi można udostępnić pozycję putback, zapisując do jakiegoś zewnętrznego miejsca docelowego, niektóre lub wszystkie elementy między początkiem i następnym wskaźniki dla buforu wyjściowego.

## <a name="basic_streambufpbase"></a><a name="pbase"></a>basic_streambuf::pbase

Funkcja chroniona, która zwraca wskaźnik na początku buforu wyjściowego.

```cpp
char_type *pbase() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku buforu wyjściowego.

## <a name="basic_streambufpbump"></a><a name="pbump"></a>basic_streambuf::pbump

Funkcja chroniona, która dodaje *liczbę* do następnego wskaźnika buforu wyjściowego.

```cpp
void pbump(int count);
```

### <a name="parameters"></a>Parametry

*Liczba*\
Liczba znaków, o które ma przesunąć pozycję zapisu do przodu.

## <a name="basic_streambufpos_type"></a><a name="pos_type"></a>basic_streambuf::p_type

Kojarzy nazwę typu w zakresie basic_streambuf z jednym z typów w parametrze szablonu.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_streambufpptr"></a><a name="pptr"></a>basic_streambuf::pptr

Funkcja chroniona, która zwraca wskaźnik do następnego elementu buforu wyjściowego.

```cpp
char_type *pptr() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego elementu buforu wyjściowego.

## <a name="basic_streambufpubimbue"></a><a name="pubimbue"></a>basic_streambuf::puminia

Ustawia ustawienia regionalne obiektu basic_streambuf.

```cpp
locale pubimbue(const locale& _Loc);
```

### <a name="parameters"></a>Parametry

*_Loc*\
Odwołanie do ustawień regionalnych.

### <a name="return-value"></a>Wartość zwracana

Poprzednia wartość przechowywana w obiekcie ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego przechowuje _ *Loc* w obiekcie ustawień regionalnych i wywołuje [imbue](#imbue).

### <a name="example"></a>Przykład

Zobacz [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue) na przykład, który `pubimbue`używa .

## <a name="basic_streambufpubseekoff"></a><a name="pubseekoff"></a>basic_streambuf::pubseekoff

Wywołania [seekoff](#seekoff), chronionej funkcji wirtualnej, która jest zastępowana w klasie pochodnej.

```cpp
pos_type pubseekoff(off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_off*\
Stanowisko do poszukiwania w stosunku do *_Way*.

*_way*\
Punktem wyjścia dla operacji odsunięcia. Zobacz [seekdir](../standard-library/ios-base-class.md#seekdir) dla możliwych wartości.

*_Which*\
Określa tryb położenia wskaźnika. Domyślnie można zmodyfikować pozycje odczytu i zapisu.

### <a name="return-value"></a>Wartość zwracana

Zwraca nową pozycję lub nieprawidłową pozycję strumienia `_Way`( `_Which` [seekoff](#seekoff)(_ *Off*, , ), ).

### <a name="remarks"></a>Uwagi

Przesuwa wskaźnik względem *_Way*.

## <a name="basic_streambufpubseekpos"></a><a name="pubseekpos"></a>basic_streambuf::pubseekpos

Wywołuje [seekpos](#seekpos), chronioną funkcję wirtualną, która jest zastępowana w klasie pochodnej i resetuje bieżącą pozycję wskaźnika.

```cpp
pos_type pubseekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Stanowisko do poszukiwania.

*_Which*\
Określa tryb położenia wskaźnika. Domyślnie można zmodyfikować pozycje odczytu i zapisu.

### <a name="return-value"></a>Wartość zwracana

Nowa pozycja lub nieprawidłowa pozycja strumienia. Aby ustalić, czy pozycja strumienia jest `pos_type(off_type(-1))`nieprawidłowa, porównaj wartość zwracaną z programem .

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [seekpos](#seekpos)(_ *Sp*, `_Which`).

## <a name="basic_streambufpubsetbuf"></a><a name="pubsetbuf"></a>basic_streambuf::pubsetbuf

Wywołuje [setbuf](#setbuf), chronioną funkcję wirtualną, która jest zastępowana w klasie pochodnej.

```cpp
basic_streambuf<Elem, Tr> *pubsetbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*_Buffer*\
Wskaźnik do `char_type` tego wystąpienia.

*Liczba*\
Rozmiar buforu.

### <a name="return-value"></a>Wartość zwracana

Zwraca [setbuf](#setbuf)( `_Buffer`, `count`).

## <a name="basic_streambufpubsync"></a><a name="pubsync"></a>basic_streambuf::pubsync

Wywołuje [sync](#sync), chronioną funkcję wirtualną, która jest zastępowana w klasie pochodnej i aktualizuje strumień zewnętrzny skojarzony z tym buforem.

```cpp
int pubsync();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca [synchronizację](#sync) lub -1, jeśli błąd.

## <a name="basic_streambufsbumpc"></a><a name="sbumpc"></a>basic_streambuf::sbumpc

Odczytuje i zwraca bieżący element, przesuwając wskaźnik strumienia.

```cpp
int_type sbumpc();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący element.

### <a name="remarks"></a>Uwagi

Jeśli pozycja odczytu jest dostępna, funkcja elementu członkowskiego zwraca **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( <strong>\*</strong> [gptr](#gptr)) i zwiększa następny wskaźnik buforu wejściowego. W przeciwnym razie zwraca [uflow](#uflow).

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

```Input
3
```

```Output
33
51
```

## <a name="basic_streambufseekoff"></a><a name="seekoff"></a>basic_streambuf::seekoff

Funkcja chronionego elementu członkowskiego wirtualnego, która próbuje zmienić bieżące pozycje dla kontrolowanych strumieni.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_off*\
Stanowisko do poszukiwania w stosunku do *_Way*.

*_way*\
Punktem wyjścia dla operacji odsunięcia. Zobacz [seekdir](../standard-library/ios-base-class.md#seekdir) dla możliwych wartości.

*_Which*\
Określa tryb położenia wskaźnika. Domyślnie można zmodyfikować pozycje odczytu i zapisu.

### <a name="return-value"></a>Wartość zwracana

Zwraca nową pozycję lub nieprawidłową `seekoff` pozycję strumienia `_Which`( (_ *Wył.,* `_Way`, ) ).

### <a name="remarks"></a>Uwagi

Nowe stanowisko określa się w następujący sposób:

- `_Way`  == Jeśli `ios_base::beg`nowa pozycja jest początkiem strumienia plus _ *Wył.*

- `_Way`  == Jeśli `ios_base::cur`nowa pozycja jest bieżącą pozycją strumienia plus _ *Wył.*

- `_Way`  == Jeśli `ios_base::end`nowa pozycja to koniec strumienia plus _ *Wył.*

Zazwyczaj, **jeśli który & ios_base::in** jest niezerowy, dotyczy strumienia wejściowego i jeśli który & **ios_base::out** jest niezerowy, dotyczy strumienia wyjściowego. Rzeczywiste użycie tego parametru różni się jednak w zależności od buforów strumienia pochodnego.

Jeśli funkcja zakończy się powodzeniem w zmianie pozycji strumienia lub pozycji, zwraca wynikową pozycję strumienia lub jedną z wynikowych pozycji strumienia. W przeciwnym razie zwraca nieprawidłową pozycję strumienia. Domyślnym zachowaniem jest zwrócenie nieprawidłowej pozycji strumienia.

## <a name="basic_streambufseekpos"></a><a name="seekpos"></a>basic_streambuf::seekpos

Funkcja chronionego elementu członkowskiego wirtualnego, która próbuje zmienić bieżące pozycje dla kontrolowanych strumieni.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Stanowisko do poszukiwania.

*_Which*\
Określa tryb położenia wskaźnika. Domyślnie można zmodyfikować pozycje odczytu i zapisu.

### <a name="return-value"></a>Wartość zwracana

Nowa pozycja lub nieprawidłowa pozycja strumienia. Aby ustalić, czy pozycja strumienia jest `pos_type(off_type(-1))`nieprawidłowa, porównaj wartość zwracaną z programem .

### <a name="remarks"></a>Uwagi

Nowa pozycja to _ *Sp*.

Zazwyczaj, **jeśli który & ios_base::in** jest niezerowy, dotyczy strumienia wejściowego i jeśli który & **ios_base::out** jest niezerowy, dotyczy strumienia wyjściowego. Rzeczywiste użycie tego parametru różni się jednak w zależności od buforów strumienia pochodnego.

Jeśli funkcja zakończy się powodzeniem w zmianie pozycji strumienia lub pozycji, zwraca wynikową pozycję strumienia lub jedną z wynikowych pozycji strumienia. W przeciwnym razie zwraca nieprawidłową pozycję strumienia (-1). Domyślnym zachowaniem jest zwrócenie nieprawidłowej pozycji strumienia.

## <a name="basic_streambufsetbuf"></a><a name="setbuf"></a>basic_streambuf::setbuf

Funkcja chronionego elementu członkowskiego wirtualnego, która wykonuje operację określoną dla każdego buforu strumienia pochodnego.

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*_Buffer*\
Wskaźnik do buforu.

*Liczba*\
Rozmiar buforu.

### <a name="return-value"></a>Wartość zwracana

Domyślnym zachowaniem jest zwrócenie **tego**.

### <a name="remarks"></a>Uwagi

Zobacz [basic_filebuf](../standard-library/basic-filebuf-class.md). `setbuf`zapewnia obszar pamięci dla `streambuf` obiektu do użycia. Jak bufor jest używany w zdefiniowanych w klasach pochodnych.

## <a name="basic_streambufsetg"></a><a name="setg"></a>basic_streambuf::setg

Funkcja chroniona, która przechowuje _ *Gbeg* w wskaźniku początkowym, `_Gnext` w następnym wskaźniku i `_Gend` w wskaźniku końcowym dla buforu wejściowego.

```cpp
void setg(char_type* _Gbeg,
    char_type* _Gnext,
    char_type* _Gend);
```

### <a name="parameters"></a>Parametry

*_Gbeg*\
Wskaźnik do początku buforu.

*_Gnext*\
Wskaźnik do gdzieś w środku buforu.

*_Gend*\
Wskaźnik do końca buforu.

## <a name="basic_streambufsetp"></a><a name="setp"></a>basic_streambuf::setp

Funkcja chroniona, która przechowuje *_Pbeg* w wskaźniku początkowym i *_Pend* w wskaźniku końcowym dla buforu wyjściowego.

```cpp
void setp(char_type* _Pbeg, char_type* _Pend);
```

### <a name="parameters"></a>Parametry

*_Pbeg*\
Wskaźnik do początku buforu.

*_Pend*\
Wskaźnik do końca buforu.

## <a name="basic_streambufsgetc"></a><a name="sgetc"></a>basic_streambuf::sgetc

Zwraca bieżący element bez zmiany pozycji w strumieniu.

```cpp
int_type sgetc();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący element.

### <a name="remarks"></a>Uwagi

Jeśli pozycja odczytu jest dostępna, funkcja elementu członkowskiego zwraca **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*` [gptr](#gptr)). W przeciwnym razie zwraca [niedopełnienie](#underflow).

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

## <a name="basic_streambufsgetn"></a><a name="sgetn"></a>basic_streambuf::sgetn

Wyodrębnia się, aby *zliczyć* znaki z buforu wejściowego i przechowuje je w podanym *buforze ptr*.

Ta metoda jest potencjalnie niebezpieczne, ponieważ opiera się na wywołującego, aby sprawdzić, czy przekazane wartości są poprawne.

```cpp
streamsize sgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Bufor zawierający wyodrębnione znaki.

*Liczba*\
Liczba elementów do odczytania.

### <a name="return-value"></a>Wartość zwracana

Liczba odczytanych elementów. Zobacz [streamsize aby](../standard-library/ios-typedefs.md#streamsize) uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [xsgetn](#xsgetn)( `ptr`, `count`).

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

## <a name="basic_streambufshowmanyc"></a><a name="showmanyc"></a>basic_streambuf::showmanyc

Funkcja chronionego wirtualnego elementu członkowskiego, która zwraca liczbę znaków, które mogą być wyodrębnione ze strumienia wejściowego i upewnij się, że program nie będzie podlegać nieokreślony czekać.

```cpp
virtual streamsize showmanyc();
```

### <a name="return-value"></a>Wartość zwracana

Domyślnym zachowaniem jest zwrócenie zera.

## <a name="basic_streambufsnextc"></a><a name="snextc"></a>basic_streambuf::snextc

Odczytuje bieżący element i zwraca następujący element.

```cpp
int_type snextc();
```

### <a name="return-value"></a>Wartość zwracana

Następny element w strumieniu.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wywołuje [sbumpc](#sbumpc) i, jeśli ta funkcja zwraca **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), zwraca **traits_type::eof**. W przeciwnym razie zwraca [sgetc](#sgetc).

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

```Input
aa
```

```Output
aa97
```

## <a name="basic_streambufsputbackc"></a><a name="sputbackc"></a>basic_streambuf::sputbackc

Umieszcza char_type w strumieniu.

```cpp
int_type sputbackc(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_ch*\
Znak.

### <a name="return-value"></a>Wartość zwracana

Zwraca znak lub błąd.

### <a name="remarks"></a>Uwagi

Jeśli pozycja odłożenia jest dostępna, a *_Ch* porównuje się równa znakowi przechowywanej w tej pozycji, funkcja elementu członkowskiego zmniejsza następny wskaźnik `_Ch`buforu wejściowego i zwraca **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( ). W przeciwnym razie zwraca [pbackfail](#pbackfail)( `_Ch`).

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

## <a name="basic_streambufsputc"></a><a name="sputc"></a>basic_streambuf::sputc

Umieszcza znak w strumieniu.

```cpp
int_type sputc(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_ch*\
Znak.

### <a name="return-value"></a>Wartość zwracana

Zwraca znak, jeśli zakończy się pomyślnie.

### <a name="remarks"></a>Uwagi

Jeśli `write position` a jest dostępny, funkcja elementu członkowskiego przechowuje *_Ch* w pozycji zapisu, zwiększa następny wskaźnik buforu wyjściowego i `_Ch`zwraca **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( ). W przeciwnym razie zwraca `_Ch` [przepełnienie](#overflow)( ).

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

## <a name="basic_streambufsputn"></a><a name="sputn"></a>basic_streambuf::sputn

Umieszcza ciąg znaków w strumieniu.

```cpp
streamsize sputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Ciąg znaków.

*Liczba*\
Liczba znaków.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków faktycznie wstawionych do strumienia.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [xsputn](#xsputn)( `ptr`, `count`). Zobacz uwagi sekcji tego członka, aby uzyskać więcej informacji.

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

## <a name="basic_streambufstossc"></a><a name="stossc"></a>basic_streambuf::stossc

Przesuń obok bieżącego elementu w strumieniu.

```cpp
void stossc();
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego wywołuje [sbumpc](#sbumpc). Należy zauważyć, że implementacja nie jest wymagana do dostarczania tej funkcji elementu członkowskiego.

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

## <a name="basic_streambufsungetc"></a><a name="sungetc"></a>basic_streambuf::sungetc

Pobiera znak ze strumienia.

```cpp
int_type sungetc();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca znak lub błąd.

### <a name="remarks"></a>Uwagi

Jeśli pozycja odłożenia jest dostępna, funkcja elementu członkowskiego zmniejsza następny `traits_type::`wskaźnik buforu `*`wejściowego i zwraca [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( [gptr](#gptr)). Jednak nie zawsze jest możliwe określenie ostatniego odczytu znaku, tak aby można go było przechwycić w stanie bieżącego buforu. Jeśli jest to prawda, funkcja zwraca [pbackfail](#pbackfail). Aby uniknąć tej sytuacji, śledzić znak, `sputbackc(ch)`aby odłożyć i wywołać, co nie powiedzie się, pod warunkiem, że nie nazwać go na początku strumienia i nie starają się umieścić z powrotem więcej niż jeden znak.

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

## <a name="basic_streambufswap"></a><a name="swap"></a>basic_streambuf::swap

Wymienia wartości w tym obiekcie dla `basic_streambuf` wartości w podanym obiekcie.

```cpp
void swap(basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*Prawo*|Odwołanie lvalue do `basic_streambuf` obiektu, który jest używany do wymiany wartości.|

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego wymienia się z `input buffer` *odpowiednimi* wskaźnikami sterującymi i . `output buffer` Wymienia `right.`również [getloc()](#getloc) `locale` z obiektem.

## <a name="basic_streambufsync"></a><a name="sync"></a>basic_streambuf::synchronizacja

Chroniona funkcja wirtualna, która próbuje zsynchronizować kontrolowane strumienie z wszelkimi skojarzonymi strumieniami zewnętrznymi.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może zakończyć się pomyślnie, zwraca wartość -1. Domyślnym zachowaniem jest zwrócenie zera.

### <a name="remarks"></a>Uwagi

`sync`obejmuje wypisywaniu wszystkich elementów między początkiem i następnym wskaźniki dla buforu wyjściowego. Nie obejmuje odłożenie żadnych elementów między następnym i końcowym wskaźniki dla buforu wejściowego.

## <a name="basic_streambuftraits_type"></a><a name="traits_type"></a>basic_streambuf::traits_type

Kojarzy nazwę typu z parametrem szablonu **Tr.**

```cpp
typedef Tr traits_type;
```

## <a name="basic_streambufuflow"></a><a name="uflow"></a>basic_streambuf::uflow

Chroniona funkcja wirtualna, która wyodrębnia bieżący element ze strumienia wejściowego.

```cpp
virtual int_type uflow();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący element.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualnego elementu członkowskiego próbuje wyodrębnić **bieżący** element ch ze strumienia wejściowego, a następnie przejść bieżącą pozycję strumienia i zwrócić element jako **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**). Może to zrobić na różne sposoby:

- Jeśli pozycja odczytu jest dostępna, trwa **ch** jako element przechowywany w pozycji odczytu i przesuwa następny wskaźnik dla buforu wejściowego.

- Może odczytać element bezpośrednio, z jakiegoś zewnętrznego źródła i dostarczyć go jako wartość **ch**.

- Dla buforu strumienia ze wspólnymi strumieniami wejściowymi i wyjściowymi można udostępnić pozycję odczytu, zapisując do jakiegoś zewnętrznego miejsca docelowego, niektóre lub wszystkie elementy między początkiem i następnym wskaźniki dla buforu wyjściowego. Lub można przydzielić nowy lub dodatkowy magazyn dla buforu wejściowego. Funkcja następnie odczytuje w, z jakiegoś źródła zewnętrznego, jeden lub więcej elementów.

Jeśli funkcja nie może zakończyć się pomyślnie, zwraca **traits_type::**[eof](../standard-library/char-traits-struct.md#eof)lub zgłasza wyjątek. W przeciwnym razie zwraca `ch` bieżący element w strumieniu wejściowym, przekonwertowany zgodnie z powyższym i przesuwa następny wskaźnik dla buforu wejściowego. Domyślnym zachowaniem jest [wywołanie niedopełnienia,](#underflow) a jeśli ta funkcja zwraca **traits_type::eof**, aby zwrócić **traits_type::eof**. W przeciwnym razie funkcja zwraca bieżący element **ch** w strumieniu wejściowym, konwertowane zgodnie z wcześniejszym opisem i zaliczki następny wskaźnik dla buforu wejściowego.

## <a name="basic_streambufunderflow"></a><a name="underflow"></a>basic_streambuf::niedopełnienie

Chroniona, wirtualna funkcja wyodrębniania bieżącego elementu ze strumienia wejściowego.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący element.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualnego elementu członkowskiego stara się wyodrębnić bieżący element **ch** ze strumienia wejściowego, `traits_type::`bez przesuwania bieżącej pozycji strumienia i zwracać go jako [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**). Może to zrobić na różne sposoby:

- Jeśli pozycja odczytu jest dostępna, **ch** jest elementem przechowywanym w pozycji odczytu. Aby uzyskać więcej informacji na ten temat, zobacz sekcję Uwagi [klasy basic_streambuf](../standard-library/basic-streambuf-class.md).

- Można udostępnić pozycję odczytu, przydzielając nowe lub dodatkowe miejsce do magazynowania dla buforu wejściowego, a następnie odczyt, z jakiegoś źródła zewnętrznego, jeden lub więcej elementów. Aby uzyskać więcej informacji na ten temat, zobacz sekcję Uwagi [klasy basic_streambuf](../standard-library/basic-streambuf-class.md).

Jeśli funkcja nie może `traits_type::`zakończyć się pomyślnie, zwraca [eof](../standard-library/char-traits-struct.md#eof) `()` lub zgłasza wyjątek. W przeciwnym razie zwraca bieżący element w strumieniu wejściowym, przekonwertowany zgodnie z wcześniejszym opisem. Domyślnym zachowaniem `traits_type::eof()`jest zwrócenie .

Funkcja `underflow` wirtualna, z funkcjami [synchronizacji](#sync) i [przepełnienia,](#overflow) definiuje właściwości klasy pochodnej. `streambuf` Każda klasa pochodna `underflow` może implementować inaczej, ale interfejs z wywołaną klasą strumienia jest taka sama.

Funkcja `underflow` jest najczęściej wywoływana `streambuf` przez funkcje publiczne, takie jak [sgetc](#sgetc) i [sgetn,](#sgetn) gdy obszar `underflow` get jest pusty, ale inne klasy, w tym klasy strumienia, można wywołać w dowolnym momencie.

Funkcja `underflow` dostarcza get area ze znakami ze źródła wejściowego. Jeśli obszar get zawiera `underflow` znaki, zwraca pierwszy znak. Jeśli obszar get jest pusty, wypełnia obszar get i zwraca następny znak (który pozostawia w obszarze get). Jeśli nie ma więcej dostępnych `underflow` `EOF` znaków, zwraca i pozostawia obszar get pusty.

W `strstreambuf` klasie `underflow` dostosowuje wskaźnik [egptr,](#egptr) aby uzyskać dostęp do magazynu, `overflow`który został dynamicznie przydzielony przez wywołanie do .

## <a name="basic_streambufxsgetn"></a><a name="xsgetn"></a>basic_streambuf::xsgetn

Chroniona, wirtualna funkcja wyodrębniania elementów ze strumienia wejściowego.

Ta metoda jest potencjalnie niebezpieczne, ponieważ opiera się na wywołującego, aby sprawdzić, czy przekazane wartości są poprawne.

```cpp
virtual streamsize xsgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Bufor zawierający wyodrębnione znaki.

*Liczba*\
Liczba elementów do wyodrębnienia.

### <a name="return-value"></a>Wartość zwracana

Liczba wyodrębnionych elementów.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualnego elementu członkowskiego wyodrębnia się do *zliczania* elementów ze strumienia wejściowego, tak jakby przez powtarzające się wywołania [sbumpc](#sbumpc)i przechowuje je w tablicy, zaczynając od *ptr*. Zwraca liczbę elementów faktycznie wyodrębnione.

## <a name="basic_streambufxsputn"></a><a name="xsputn"></a>basic_streambuf::xsputn

Chroniona, wirtualna funkcja wstawiania elementów do strumienia wyjściowego.

```cpp
virtual streamsize xsputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Parametry

*Ptr*\
Wskaźnik do elementów do wstawienia.

*Liczba*\
Liczba elementów do wstawienia.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów faktycznie wstawionych do strumienia.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualnego elementu członkowskiego wstawia się do *zliczania* elementów do strumienia wyjściowego, tak jakby przez powtarzające się wywołania [sputc](#sputc), od tablicy rozpoczynającej się od *ptr*. Wstawianie znaków do strumienia wyjściowego zatrzymuje się po zapisaniu `traits::eof()`wszystkich znaków *zliczania* lub w przypadku zwrócenia wywołania `sputc( count)` . Zwraca liczbę faktycznie wstawionych elementów.

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
