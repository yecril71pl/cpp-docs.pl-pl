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
ms.openlocfilehash: 6c9a44f56e89baf32ba49241822bc4ba018f0701
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561833"
---
# <a name="basic_streambuf-class"></a>basic_streambuf — Klasa

Opisuje abstrakcyjną klasę bazową służącą do pozyskiwania buforu strumienia, która kontroluje przekazywanie elementów do i z określonej reprezentacji strumienia.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_streambuf;
```

### <a name="parameters"></a>Parametry

*Elem*\
[Char_type](#char_type).

*Zdawczy*\
Znak [traits_type](#traits_type).

## <a name="remarks"></a>Uwagi

Szablon klasy opisuje abstrakcyjną klasę bazową dla tworzenia bufora strumienia, która kontroluje przekazywanie elementów do i z określonej reprezentacji strumienia. Obiekt klasy `basic_streambuf` ułatwia sterowanie strumieniem za pomocą elementów typu *TR*, znanych także jako [char_type](#char_type), których cechy znaku są określane przez klasę [char_traits](../standard-library/char-traits-struct.md), znane także jako [traits_type](#traits_type).

Każdy bufor strumienia koncepcyjnie steruje dwoma niezależnymi strumieniami: jeden dla wyodrębniania (dane wejściowe) i jeden dla wstawek (dane wyjściowe). Określona reprezentacja może jednak spowodować, że oba te strumienie nie są dostępne. Zwykle utrzymuje pewne relacje między dwoma strumieniami. To, co jest wstawiane do strumienia danych wyjściowych [basic_stringbuf](../standard-library/basic-stringbuf-class.md) <  `Elem` , `Tr`> obiektu, na przykład, jest to, co można później wyodrębnić ze strumienia wejściowego. Gdy umieszczasz jeden strumień [basic_filebuf](../standard-library/basic-filebuf-class.md) <  `Elem` , `Tr`> obiektu, umieszczasz inny strumień wspólnie.

Interfejs publiczny do szablonu klasy `basic_streambuf` dostarcza operacje, które są wspólne dla wszystkich buforów strumieni, jednak wyspecjalizowane. Chroniony interfejs dostarcza operacje, które są konieczne do określonej reprezentacji strumienia, aby wykonać jego działanie. Chronione wirtualne funkcje członkowskie pozwalają dostosować zachowanie buforu pochodnego strumienia dla określonej reprezentacji strumienia. Każdy pochodny bufor strumienia w tej bibliotece opisuje sposób, w jaki określa zachowanie chronionych funkcji wirtualnych elementów członkowskich. Domyślne zachowanie klasy bazowej, która często nie wykonuje żadnych operacji, jest opisane w tym temacie.

Pozostałe chronione funkcje członkowskie kontrolują kopiowanie do i z dowolnego magazynu dostarczonego do przesyłanych buforów do i ze strumieni. Bufor wejściowy, na przykład, jest scharakteryzowany przez:

- [eback](#eback), wskaźnik do początku buforu.

- [GPTR](#gptr), wskaźnik do następnego elementu, który ma zostać odczytany.

- [egptr](#egptr), wskaźnik tuż poza końcem buforu.

Podobnie bufor wyjściowy jest scharakteryzowany przez:

- [pbase](#pbase), wskaźnik do początku buforu.

- [pptr](#pptr), wskaźnik do następnego elementu do zapisu.

- [epptr](#epptr), wskaźnik tuż poza końcem buforu.

W przypadku dowolnego buforu używany jest następujący protokół:

- Jeśli następny wskaźnik ma wartość null, żaden bufor nie istnieje. W przeciwnym razie wszystkie trzy wskaźniki wskazują na tę samą sekwencję. Można je bezpiecznie porównać z kolejnością.

- W przypadku bufora wyjściowego, jeśli następny wskaźnik porównuje mniej niż wskaźnik końcowy, można przechowywać element w pozycji zapisu wyoznaczonej przez następny wskaźnik.

- W przypadku bufora wejściowego, jeśli następny wskaźnik porównuje mniej niż wskaźnik końcowy, można odczytać element w pozycji odczytu wyoznaczonej przez następny wskaźnik.

- W przypadku bufora wejściowego, jeśli początkowy wskaźnik porównuje mniej niż następny wskaźnik, można umieścić element w pozycji putback Wyznaczeni przez zmniejszony następny wskaźnik.

Wszelkie chronione wirtualne funkcje członkowskie, które należy napisać dla klasy pochodzącej od `basic_streambuf` <  `Elem` , `Tr`> muszą współpracować przy utrzymywaniu tego protokołu.

Obiekt klasy `basic_streambuf` <  `Elem` , `Tr`> przechowuje sześć wcześniej opisanych wskaźników. Przechowuje również obiekt ustawień regionalnych w obiekcie typu [locale](../standard-library/locale-class.md) dla potencjalnego użycia przez pochodny bufor strumienia.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[basic_streambuf](#basic_streambuf)|Konstruuje obiekt typu `basic_streambuf` .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Kojarzy nazwę typu z `Elem` parametrem szablonu.|
|[int_type](#int_type)|Kojarzy nazwę typu w `basic_streambuf` zakresie z `Elem` parametrem szablonu.|
|[off_type](#off_type)|Kojarzy nazwę typu w `basic_streambuf` zakresie z `Elem` parametrem szablonu.|
|[pos_type](#pos_type)|Kojarzy nazwę typu w `basic_streambuf` zakresie z `Elem` parametrem szablonu.|
|[traits_type](#traits_type)|Kojarzy nazwę typu z `Tr` parametrem szablonu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[eback](#eback)|Funkcja chroniona zwracająca wskaźnik do początku buforu wejściowego.|
|[egptr](#egptr)|Funkcja chroniona zwracająca wskaźnik tuż poza końcem buforu wejściowego.|
|[epptr](#epptr)|Funkcja chroniona zwracająca wskaźnik tuż poza końcem buforu wyjściowego.|
|[gbump](#gbump)|Funkcja chroniona, która dodaje `count` do następnego wskaźnika dla buforu wejściowego.|
|[getloc](#getloc)|Pobiera `basic_streambuf` Ustawienia regionalne obiektu.|
|[gptr](#gptr)|Funkcja chroniona zwracająca wskaźnik do następnego elementu buforu wejściowego.|
|[imbue —](#imbue)|Chroniona funkcja wirtualna wywołana przez [pubimbue](#pubimbue).|
|[in_avail](#in_avail)|Zwraca liczbę elementów, które są gotowe do odczytu z bufora.|
|[przepływ](#overflow)|Chroniona funkcja wirtualna, która może być wywoływana, gdy nowy znak zostanie wstawiony do pełnego buforu.|
|[pbackfail](#pbackfail)|Chroniona funkcja wirtualna elementu członkowskiego, która próbuje umieścić element w strumieniu wejściowym, a następnie uczynić go bieżącym elementem (wskazywanym przez następny wskaźnik).|
|[pbase](#pbase)|Funkcja chroniona zwracająca wskaźnik do początku buforu wyjściowego.|
|[pbump](#pbump)|Funkcja chroniona, która dodaje `count` do następnego wskaźnika dla buforu danych wyjściowych.|
|[pptr](#pptr)|Funkcja chroniona zwracająca wskaźnik do następnego elementu buforu wyjściowego.|
|[pubimbue](#pubimbue)|Ustawia `basic_streambuf` Ustawienia regionalne obiektu.|
|[pubseekoff](#pubseekoff)|Wywołuje [seekoff](#seekoff), chronioną funkcję wirtualną, która została zastąpiona w klasie pochodnej.|
|[pubseekpos](#pubseekpos)|Wywołuje [seekpos](#seekpos), chronioną funkcję wirtualną, która została zastąpiona w klasie pochodnej i resetuje bieżącą pozycję wskaźnika.|
|[pubsetbuf](#pubsetbuf)|Wywołuje [setbuf](#setbuf), chronioną funkcję wirtualną, która została zastąpiona w klasie pochodnej.|
|[pubsync](#pubsync)|Wywołuje [synchronizację](#sync), chronioną funkcję wirtualną, która została zastąpiona w klasie pochodnej i aktualizuje zewnętrzny strumień skojarzony z tym buforem.|
|[sbumpc —](#sbumpc)|Odczytuje i zwraca bieżący element, przesuwając wskaźnik strumienia.|
|[seekoff](#seekoff)|Chroniona funkcja wirtualna elementu członkowskiego próbuje zmienić bieżące położenie dla kontrolowanych strumieni.|
|[seekpos](#seekpos)|Chroniona funkcja wirtualna elementu członkowskiego próbuje zmienić bieżące położenie dla kontrolowanych strumieni.|
|[setbuf](#setbuf)|Chroniona funkcja wirtualna elementu członkowskiego wykonuje operację konkretną dla każdego pochodnego buforu strumienia.|
|[setg](#setg)|Funkcja chroniona, która przechowuje `_Gbeg` w początkowym wskaźniku, `_Gnext` w następnym wskaźniku i `_Gend` końcowym wskaźniku dla buforu wejściowego.|
|[setp](#setp)|Funkcja chroniona, która przechowuje `_Pbeg` w początkowym wskaźniku i `_Pend` końcowy wskaźnik dla buforu wyjściowego.|
|[sgetc —](#sgetc)|Zwraca bieżący element bez zmiany pozycji w strumieniu.|
|[sgetn](#sgetn)|Zwraca liczbę odczytywanych elementów.|
|[showmanyc](#showmanyc)|Chroniona funkcja wirtualna elementu członkowskiego zwracająca liczbę znaków, które mogą zostać wyodrębnione ze strumienia wejściowego, i upewnić się, że program nie będzie podlegać nieograniczonemu czekaniu.|
|[snextc](#snextc)|Odczytuje bieżący element i zwraca następujący element.|
|[sputbackc](#sputbackc)|Umieszcza `char_type` w strumieniu.|
|[sputc](#sputc)|Umieszcza znak w strumieniu.|
|[sputn](#sputn)|Umieszcza ciąg znaków w strumieniu.|
|[stossc](#stossc)|Przenieś poza bieżący element w strumieniu.|
|[sungetc](#sungetc)|Pobiera znak ze strumienia.|
|[wymiany](#swap)|Wymienia wartości w tym obiekcie dla wartości w podanym `basic_streambuf` parametrze obiektu.|
|[synchronizacji](#sync)|Chroniona funkcja wirtualna, która próbuje zsynchronizować kontrolowane strumienie ze wszystkimi skojarzonymi strumieniami zewnętrznymi.|
|[uflow](#uflow)|Chroniona funkcja wirtualna, która wyodrębnia bieżący element ze strumienia wejściowego.|
|[miar](#underflow)|Chroniona funkcja wirtualna, która wyodrębnia bieżący element ze strumienia wejściowego.|
|[xsgetn](#xsgetn)|Chroniona funkcja wirtualna, która wyodrębnia elementy ze strumienia wejściowego.|
|[xsputn](#xsputn)|Chroniona funkcja wirtualna, która wstawia elementy do strumienia wyjściowego.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator =](#op_eq)|Przypisuje wartości tego obiektu z innego `basic_streambuf` obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<streambuf>

**Przestrzeń nazw:** std

## <a name="basic_streambufbasic_streambuf"></a><a name="basic_streambuf"></a> basic_streambuf:: basic_streambuf

Konstruuje obiekt typu `basic_streambuf` .

```cpp
basic_streambuf();

basic_streambuf(const basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Odwołanie lvalue do `basic_streambuf` obiektu, który jest używany do ustawiania wartości dla tego `basic_streambuf` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy chroniony Konstruktor przechowuje wskaźnik o wartości null we wszystkich wskaźnikach kontrolujących bufor wejściowy i bufor wyjściowy. Przechowuje również `locale::classic` w obiekcie Locals. Aby uzyskać więcej informacji, zobacz [locale:: Classic](../standard-library/locale-class.md#classic).

Drugi chroniony Konstruktor kopiuje wskaźniki i ustawienia regionalne z *prawej strony*.

## <a name="basic_streambufchar_type"></a><a name="char_type"></a> basic_streambuf:: char_type

Kojarzy nazwę typu z parametrem szablonu **elem** .

```cpp
typedef Elem char_type;
```

## <a name="basic_streambufeback"></a><a name="eback"></a> basic_streambuf:: eback

Funkcja chroniona zwracająca wskaźnik do początku buforu wejściowego.

```cpp
char_type *eback() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku buforu wejściowego.

## <a name="basic_streambufegptr"></a><a name="egptr"></a> basic_streambuf:: egptr

Funkcja chroniona zwracająca wskaźnik tuż poza końcem buforu wejściowego.

```cpp
char_type *egptr() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik tuż poza końcem buforu wejściowego.

## <a name="basic_streambufepptr"></a><a name="epptr"></a> basic_streambuf:: epptr

Funkcja chroniona zwracająca wskaźnik tuż poza końcem buforu wyjściowego.

```cpp
char_type *epptr() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik tuż poza końcem buforu wyjściowego.

## <a name="basic_streambufgbump"></a><a name="gbump"></a> basic_streambuf:: gbump

Funkcja chroniona, która dodaje *liczbę* do następnego wskaźnika dla buforu wejściowego.

```cpp
void gbump(int count);
```

### <a name="parameters"></a>Parametry

*liczbą*\
Wartość, według której ma zostać umieszczony wskaźnik.

## <a name="basic_streambufgetloc"></a><a name="getloc"></a> basic_streambuf:: getloc

Pobiera ustawienia regionalne obiektu basic_streambuf.

```cpp
locale getloc() const;
```

### <a name="return-value"></a>Wartość zwracana

Przechowywany obiekt locale.

### <a name="remarks"></a>Uwagi

Aby uzyskać powiązane informacje, zobacz [ios_base:: getloc](../standard-library/ios-base-class.md#getloc).

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

## <a name="basic_streambufgptr"></a><a name="gptr"></a> basic_streambuf:: GPTR

Funkcja chroniona zwracająca wskaźnik do następnego elementu buforu wejściowego.

```cpp
char_type *gptr() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego elementu buforu wejściowego.

## <a name="basic_streambufimbue"></a><a name="imbue"></a> basic_streambuf:: imbue —

Chroniona funkcja wirtualna wywołana przez [pubimbue](#pubimbue).

```cpp
virtual void imbue(const locale& _Loc);
```

### <a name="parameters"></a>Parametry

*_Loc*\
Odwołanie do ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Zachowanie domyślne to nic nie rób.

## <a name="basic_streambufin_avail"></a><a name="in_avail"></a> basic_streambuf:: in_avail

Zwraca liczbę elementów, które są gotowe do odczytu z bufora.

```cpp
streamsize in_avail();
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, które są gotowe do odczytu z bufora.

### <a name="remarks"></a>Uwagi

Jeśli dostępna jest [pozycja odczytu](../standard-library/basic-streambuf-class.md) , funkcja członkowska zwraca [egptr](#egptr)  -  [GPTR](#gptr). W przeciwnym razie zwraca [showmanyc](#showmanyc).

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

## <a name="basic_streambufint_type"></a><a name="int_type"></a> basic_streambuf:: int_type

Kojarzy nazwę typu w basic_streambuf zakresie z jednym z typów w parametrze szablonu.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_streambufoff_type"></a><a name="off_type"></a> basic_streambuf:: off_type

Kojarzy nazwę typu w basic_streambuf zakresie z jednym z typów w parametrze szablonu.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_streambufoperator"></a><a name="op_eq"></a> basic_streambuf:: operator =

Przypisuje wartości tego obiektu z innego `basic_streambuf` obiektu.

```cpp
basic_streambuf& operator=(const basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Odwołanie lvalue do `basic_streambuf` obiektu, który jest używany do przypisywania wartości do tego obiektu.

### <a name="remarks"></a>Uwagi

Chroniony operator członkowski kopiuje z *prawej strony* wskaźniki kontrolujące bufor wejściowy i bufor wyjściowy. Przechowuje również `right.` [getloc ()](#getloc) w `locale object` . Zwraca wartość **`*this`** .

## <a name="basic_streambufoverflow"></a><a name="overflow"></a> basic_streambuf:: overflow

Chroniona funkcja wirtualna, która może być wywoływana, gdy nowy znak zostanie wstawiony do pełnego buforu.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak do wstawienia do buforu lub **traits_type::**[EOF](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść, zwraca **traits_type:: eof** lub zgłasza wyjątek. W przeciwnym razie zwraca **traits_type::**[Not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *meta*). Domyślnym zachowaniem jest zwrócenie **traits_type:: eof**.

### <a name="remarks"></a>Uwagi

Jeśli * \_ meta* nie porównano równe **traits_type:: EOF**, chroniona wirtualna funkcja członkowska przedsięwzięciach do wstawienia elementu **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(* \_ meta*) do strumienia wyjściowego. Można to zrobić na różne sposoby:

- Jeśli `write position` jest dostępny, można zapisać element w pozycji zapisu i zwiększyć następny wskaźnik dla buforu wyjściowego.

- Możliwe jest udostępnienie pozycji zapisu przez przydzielenie nowego lub dodatkowego magazynu dla buforu danych wyjściowych.

- Umożliwia zapisanie pozycji zapisu, do niektórych zewnętrznych miejsc docelowych, niektórych lub wszystkich elementów między wskaźnikiem początkowym i następnym dla buforu wyjściowego.

Wirtualna funkcja przepełnienia, wraz z funkcjami [synchronizacji](#sync) i [niedomiaru](#underflow) , definiuje cechy klasy pochodnej streambuf. Każda klasa pochodna może zaimplementować przepełnienie w inny sposób, ale interfejs z klasą strumienia wywołującego jest taki sam.

`overflow`Funkcja jest najczęściej wywoływana przez `streambuf` funkcje publiczne, takie jak `sputc` i `sputn` Kiedy obszar umieszczenia jest pełny, ale inne klasy, w tym klasy strumienia, mogą wywołać w `overflow` dowolnym czasie.

Funkcja zużywa znaki w obszarze Put między `pbase` `pptr` wskaźnikami i, a następnie ponownie inicjuje miejsce umieszczenia. `overflow`Funkcja musi również używać `nCh` (Jeśli `nCh` nie `EOF` ) lub może umieścić ten znak w nowym obszarze umieszczania, tak aby był użyty przy następnym wywołaniu.

Definicja użycia różni się między klasami pochodnymi. Na przykład `filebuf` Klasa zapisuje swoje znaki do pliku, podczas gdy `strstreambuf` Klasa przechowuje je w buforze i (Jeśli bufor jest wyznaczono jako dynamiczny), rozszerza bufor w odpowiedzi na wywołanie przepełnienia. To rozszerzenie jest osiągane przez zwolnienie starego buforu i zastąpienie go nowym, większym. Wskaźniki są dostosowywane w razie potrzeby.

## <a name="basic_streambufpbackfail"></a><a name="pbackfail"></a> basic_streambuf::p nie powiodło się

Chroniona funkcja wirtualna elementu członkowskiego, która próbuje umieścić element w strumieniu wejściowym, a następnie uczynić go bieżącym elementem (wskazywanym przez następny wskaźnik).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak do wstawienia do buforu lub **traits_type::**[EOF](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść, zwraca **traits_type:: eof** lub zgłasza wyjątek. W przeciwnym razie zwraca inną wartość. Domyślnym zachowaniem jest zwrócenie **traits_type:: eof**.

### <a name="remarks"></a>Uwagi

Jeśli * \_ meta* porównuje równe **traits_type:: EOF**, element do wypchnięcia jest skutecznym obiektem już w strumieniu przed bieżącym elementem. W przeciwnym razie ten element jest zastępowany przez **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(* \_ meta*). Funkcja może umieścić element na różne sposoby:

- Jeśli pozycja putback jest dostępna, może ona przechowywać element w pozycji putback i zmniejszać następny wskaźnik dla buforu wejściowego.

- Możliwe jest udostępnienie pozycji putback przez przydzielenie nowego lub dodatkowego magazynu dla buforu wejściowego.

- W przypadku bufora strumienia ze wspólnymi strumieniami wejściowymi i wyjściowymi można ustawić pozycję putback, aby uzyskać dostęp do niektórych zewnętrznych miejsc docelowych, niektórych lub wszystkich elementów między wskaźnikiem początkowym i następnym dla buforu wyjściowego.

## <a name="basic_streambufpbase"></a><a name="pbase"></a> basic_streambuf::p Base

Funkcja chroniona zwracająca wskaźnik do początku buforu wyjściowego.

```cpp
char_type *pbase() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku buforu wyjściowego.

## <a name="basic_streambufpbump"></a><a name="pbump"></a> basic_streambuf::p nierówności

Funkcja chroniona, która dodaje *liczbę* do następnego wskaźnika dla buforu danych wyjściowych.

```cpp
void pbump(int count);
```

### <a name="parameters"></a>Parametry

*liczbą*\
Liczba znaków, przez jaką należy przenieść pozycję zapisu do przodu.

## <a name="basic_streambufpos_type"></a><a name="pos_type"></a> basic_streambuf::p os_type

Kojarzy nazwę typu w basic_streambuf zakresie z jednym z typów w parametrze szablonu.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_streambufpptr"></a><a name="pptr"></a> basic_streambuf::p PTR

Funkcja chroniona zwracająca wskaźnik do następnego elementu buforu wyjściowego.

```cpp
char_type *pptr() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego elementu buforu wyjściowego.

## <a name="basic_streambufpubimbue"></a><a name="pubimbue"></a> basic_streambuf::p ubimbue

Ustawia ustawienia regionalne obiektu basic_streambuf.

```cpp
locale pubimbue(const locale& _Loc);
```

### <a name="parameters"></a>Parametry

*_Loc*\
Odwołanie do ustawień regionalnych.

### <a name="return-value"></a>Wartość zwracana

Poprzednia wartość przechowywana w obiekcie locale.

### <a name="remarks"></a>Uwagi

Funkcja członkowska przechowuje wartość _ *Loc* w obiekcie Locals i wywołuje [imbue —](#imbue).

### <a name="example"></a>Przykład

Zapoznaj się z przykładem [basic_ios:: imbue —](../standard-library/basic-ios-class.md#imbue) `pubimbue` .

## <a name="basic_streambufpubseekoff"></a><a name="pubseekoff"></a> basic_streambuf::p ubseekoff

Wywołuje [seekoff](#seekoff), chronioną funkcję wirtualną, która została zastąpiona w klasie pochodnej.

```cpp
pos_type pubseekoff(off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*\
Pozycja do wyszukiwania względem *_Way*.

*_Way*\
Punkt początkowy dla operacji przesunięcia. Zobacz [seekdir](../standard-library/ios-base-class.md#seekdir) , aby uzyskać możliwe wartości.

*_Which*\
Określa tryb dla pozycji wskaźnika. Wartość domyślna to umożliwienie modyfikacji pozycji odczytu i zapisu.

### <a name="return-value"></a>Wartość zwracana

Zwraca nową pozycję lub nieprawidłową pozycję strumienia ( [seekoff](#seekoff)( *off*, `_Way` , `_Which` )).

### <a name="remarks"></a>Uwagi

Przesuwa wskaźnik względem *_Way*.

## <a name="basic_streambufpubseekpos"></a><a name="pubseekpos"></a> basic_streambuf::p ubseekpos

Wywołuje [seekpos](#seekpos), chronioną funkcję wirtualną, która została zastąpiona w klasie pochodnej i resetuje bieżącą pozycję wskaźnika.

```cpp
pos_type pubseekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Pozycja do wyszukania.

*_Which*\
Określa tryb dla pozycji wskaźnika. Wartość domyślna to umożliwienie modyfikacji pozycji odczytu i zapisu.

### <a name="return-value"></a>Wartość zwracana

Nowa pozycja lub nieprawidłowa pozycja strumienia. Aby określić, czy pozycja strumienia jest nieprawidłowa, porównaj wartość zwracaną z `pos_type(off_type(-1))` .

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [seekpos](#seekpos)(_ *SP*, `_Which` ).

## <a name="basic_streambufpubsetbuf"></a><a name="pubsetbuf"></a> basic_streambuf::p ubsetbuf

Wywołuje [setbuf](#setbuf), chronioną funkcję wirtualną, która została zastąpiona w klasie pochodnej.

```cpp
basic_streambuf<Elem, Tr> *pubsetbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*_Buffer*\
Wskaźnik do `char_type` dla tego wystąpienia.

*liczbą*\
Rozmiar buforu.

### <a name="return-value"></a>Wartość zwracana

Zwraca [setbuf](#setbuf)( `_Buffer` , `count` ).

## <a name="basic_streambufpubsync"></a><a name="pubsync"></a> basic_streambuf::p ubsync

Wywołuje [synchronizację](#sync), chronioną funkcję wirtualną, która jest zastępowana w klasie pochodnej, i aktualizuje zewnętrzny strumień skojarzony z tym buforem.

```cpp
int pubsync();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca wartość [Sync](#sync) lub-1, jeśli wystąpi błąd.

## <a name="basic_streambufsbumpc"></a><a name="sbumpc"></a> basic_streambuf:: sbumpc —

Odczytuje i zwraca bieżący element, przesuwając wskaźnik strumienia.

```cpp
int_type sbumpc();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący element.

### <a name="remarks"></a>Uwagi

Jeśli pozycja odczytu jest dostępna, funkcja członkowska zwraca **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( <strong>\*</strong> [GPTR](#gptr)) i zwiększa następny wskaźnik dla buforu wejściowego. W przeciwnym razie zwraca [uflow](#uflow).

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

## <a name="basic_streambufseekoff"></a><a name="seekoff"></a> basic_streambuf:: seekoff

Chroniona funkcja wirtualna elementu członkowskiego, która próbuje zmienić bieżące położenie dla kontrolowanych strumieni.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*\
Pozycja do wyszukiwania względem *_Way*.

*_Way*\
Punkt początkowy dla operacji przesunięcia. Zobacz [seekdir](../standard-library/ios-base-class.md#seekdir) , aby uzyskać możliwe wartości.

*_Which*\
Określa tryb dla pozycji wskaźnika. Wartość domyślna to umożliwienie modyfikacji pozycji odczytu i zapisu.

### <a name="return-value"></a>Wartość zwracana

Zwraca nową pozycję lub nieprawidłową pozycję strumienia ( `seekoff` ( *off*, `_Way` , `_Which` )).

### <a name="remarks"></a>Uwagi

Nowa pozycja jest określana w następujący sposób:

- Jeśli `_Way`  ==  `ios_base::beg` Nowa pozycja jest początkiem strumienia i jest *wyłączona*.

- Jeśli `_Way`  ==  `ios_base::cur` Nowa pozycja jest bieżącą pozycją strumienia i jest *wyłączona*.

- Jeśli `_Way`  ==  `ios_base::end` Nowa pozycja jest końcem strumienia i jest *wyłączona*.

Zwykle, jeśli **& ios_base:: w** ma wartość różną od zera, wpłynie to na strumień wejściowy, a jeśli **& ios_base:: out** ma wartość różną od zera, wpłynie to na strumień danych wyjściowych. Jednak rzeczywiste użycie tego parametru różni się między pochodnymi buforami strumienia.

Jeśli funkcja się powiedzie w przypadku zmiany położenia lub położenia strumienia, zwraca wynikową pozycję strumienia lub jedną z wynikowych pozycji strumienia. W przeciwnym razie zwraca nieprawidłową pozycję strumienia. Domyślnym zachowaniem jest zwrócenie nieprawidłowej pozycji strumienia.

## <a name="basic_streambufseekpos"></a><a name="seekpos"></a> basic_streambuf:: seekpos

Chroniona funkcja wirtualna elementu członkowskiego, która próbuje zmienić bieżące położenie dla kontrolowanych strumieni.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Pozycja do wyszukania.

*_Which*\
Określa tryb dla pozycji wskaźnika. Wartość domyślna to umożliwienie modyfikacji pozycji odczytu i zapisu.

### <a name="return-value"></a>Wartość zwracana

Nowa pozycja lub niepoprawna pozycja strumienia. Aby określić, czy pozycja strumienia jest nieprawidłowa, porównaj wartość zwracaną z `pos_type(off_type(-1))` .

### <a name="remarks"></a>Uwagi

Nowa pozycja to _ *SP*.

Zwykle, jeśli **& ios_base:: w** ma wartość różną od zera, wpłynie to na strumień wejściowy, a jeśli **& ios_base:: out** ma wartość różną od zera, wpłynie to na strumień danych wyjściowych. Jednak rzeczywiste użycie tego parametru różni się między pochodnymi buforami strumienia.

Jeśli funkcja się powiedzie w przypadku zmiany położenia lub położenia strumienia, zwraca wynikową pozycję strumienia lub jedną z wynikowych pozycji strumienia. W przeciwnym razie zwraca nieprawidłową pozycję strumienia (-1). Domyślnym zachowaniem jest zwrócenie nieprawidłowej pozycji strumienia.

## <a name="basic_streambufsetbuf"></a><a name="setbuf"></a> basic_streambuf:: setbuf

Chroniona funkcja wirtualna elementu członkowskiego, która wykonuje operację konkretną dla każdego pochodnego buforu strumienia.

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*_Buffer*\
Wskaźnik do buforu.

*liczbą*\
Rozmiar buforu.

### <a name="return-value"></a>Wartość zwracana

Domyślne zachowanie to Return **`this`** .

### <a name="remarks"></a>Uwagi

Zobacz [basic_filebuf](../standard-library/basic-filebuf-class.md). `setbuf` zapewnia obszar pamięci, `streambuf` który ma być używany przez obiekt. Sposób użycia bufora zdefiniowanego w klasach pochodnych.

## <a name="basic_streambufsetg"></a><a name="setg"></a> basic_streambuf:: setg

Funkcja chroniona, która przechowuje _ *Gbeg* w wskaźniku początkowym, `_Gnext` w następnym wskaźniku i `_Gend` w końcowym wskaźniku dla buforu wejściowego.

```cpp
void setg(char_type* _Gbeg,
    char_type* _Gnext,
    char_type* _Gend);
```

### <a name="parameters"></a>Parametry

*_Gbeg*\
Wskaźnik do początku buforu.

*_Gnext*\
Wskaźnik do dowolnego miejsca w środku buforu.

*_Gend*\
Wskaźnik do końca buforu.

## <a name="basic_streambufsetp"></a><a name="setp"></a> basic_streambuf:: setp

Funkcja chroniona, która przechowuje *_Pbeg* na początkowym wskaźniku i *_Pend* w końcowym wskaźniku dla buforu wyjściowego.

```cpp
void setp(char_type* _Pbeg, char_type* _Pend);
```

### <a name="parameters"></a>Parametry

*_Pbeg*\
Wskaźnik do początku buforu.

*_Pend*\
Wskaźnik do końca buforu.

## <a name="basic_streambufsgetc"></a><a name="sgetc"></a> basic_streambuf:: sgetc —

Zwraca bieżący element bez zmiany pozycji w strumieniu.

```cpp
int_type sgetc();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący element.

### <a name="remarks"></a>Uwagi

Jeśli pozycja odczytu jest dostępna, funkcja członkowska zwraca **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*` [GPTR](#gptr)). W przeciwnym [razie zwraca](#underflow)niedopełnienie.

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

## <a name="basic_streambufsgetn"></a><a name="sgetn"></a> basic_streambuf:: sgetn

Wyodrębnia do *liczby* znaków z buforu wejściowego i przechowuje je w udostępnionym buforze *PTR*.

Ta metoda jest potencjalnie niebezpieczna, ponieważ polega na wywołującym, aby sprawdzić, czy przeszukane wartości są poprawne.

```cpp
streamsize sgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*PTR*\
Bufor zawierający wyodrębnione znaki.

*liczbą*\
Liczba elementów, które mają zostać odczytane.

### <a name="return-value"></a>Wartość zwracana

Liczba odczytanych elementów. Aby uzyskać więcej informacji, zobacz [dane StreamSize](../standard-library/ios-typedefs.md#streamsize) .

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [xsgetn](#xsgetn)( `ptr` , `count` ).

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

## <a name="basic_streambufshowmanyc"></a><a name="showmanyc"></a> basic_streambuf:: showmanyc

Chroniona funkcja wirtualna elementu członkowskiego zwracająca liczbę znaków, które mogą zostać wyodrębnione ze strumienia wejściowego, i upewnić się, że program nie będzie podlegać nieograniczonemu czekaniu.

```cpp
virtual streamsize showmanyc();
```

### <a name="return-value"></a>Wartość zwracana

Domyślne zachowanie ma zwrócić wartość zero.

## <a name="basic_streambufsnextc"></a><a name="snextc"></a> basic_streambuf:: snextc

Odczytuje bieżący element i zwraca następujący element.

```cpp
int_type snextc();
```

### <a name="return-value"></a>Wartość zwracana

Następny element w strumieniu.

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [sbumpc —](#sbumpc) i, jeśli ta funkcja zwraca **traits_type::**[EOF](../standard-library/char-traits-struct.md#eof), zwraca **traits_type:: EOF**. W przeciwnym razie zwraca [sgetc —](#sgetc).

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

## <a name="basic_streambufsputbackc"></a><a name="sputbackc"></a> basic_streambuf:: sputbackc

Umieszcza char_type w strumieniu.

```cpp
int_type sputbackc(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*\
Znak.

### <a name="return-value"></a>Wartość zwracana

Zwraca znak lub niepowodzenie.

### <a name="remarks"></a>Uwagi

Jeśli pozycja putback jest dostępna i *_Ch* porównuje ją z znakiem przechowywanym w tej pozycji, funkcja członkowska zmniejsza następny wskaźnik dla buforu wejściowego i zwraca **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `_Ch` ). W przeciwnym razie zwraca [pbackfail](#pbackfail)( `_Ch` ).

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

## <a name="basic_streambufsputc"></a><a name="sputc"></a> basic_streambuf:: sputc

Umieszcza znak w strumieniu.

```cpp
int_type sputc(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*\
Znak.

### <a name="return-value"></a>Wartość zwracana

Zwraca znak, jeśli powodzenie.

### <a name="remarks"></a>Uwagi

Jeśli `write position` jest dostępny, funkcja członkowska przechowuje *_Ch* w pozycji zapisu, zwiększa następny wskaźnik dla buforu wyjściowego i zwraca **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `_Ch` ). W przeciwnym razie zwraca [przepełnienie](#overflow)( `_Ch` ).

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

## <a name="basic_streambufsputn"></a><a name="sputn"></a> basic_streambuf:: sputn

Umieszcza ciąg znaków w strumieniu.

```cpp
streamsize sputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Parametry

*PTR*\
Ciąg znaków.

*liczbą*\
Liczba znaków.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków faktycznie wstawianych do strumienia.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca [xsputn](#xsputn)( `ptr` , `count` ). Aby uzyskać więcej informacji, zobacz sekcję Uwagi tego elementu członkowskiego.

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

## <a name="basic_streambufstossc"></a><a name="stossc"></a> basic_streambuf:: stossc

Przenieś poza bieżący element w strumieniu.

```cpp
void stossc();
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska wywołuje [sbumpc —](#sbumpc). Należy zauważyć, że implementacja nie jest wymagana do dostarczania tej funkcji elementu członkowskiego.

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

## <a name="basic_streambufsungetc"></a><a name="sungetc"></a> basic_streambuf:: sungetc

Pobiera znak ze strumienia.

```cpp
int_type sungetc();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca znak lub błąd.

### <a name="remarks"></a>Uwagi

Jeśli pozycja putback jest dostępna, funkcja członkowska zmniejsza następny wskaźnik dla buforu wejściowego i zwraca `traits_type::` [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*` [GPTR](#gptr)). Jednak nie zawsze jest możliwe określenie ostatniego odczytu znaku, aby można było go przechwycić w stanie bieżącego buforu. Jeśli ta wartość jest równa true, funkcja zwraca [pbackfail](#pbackfail). Aby uniknąć tej sytuacji, Śledź znak do odłożenia i wywołania `sputbackc(ch)` , co nie powiedzie się, na początku którego nie można wywołać, i nie próbujesz umieścić więcej niż jednego znaku.

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

## <a name="basic_streambufswap"></a><a name="swap"></a> basic_streambuf:: swap

Wymienia wartości w tym obiekcie dla wartości z podanego `basic_streambuf` obiektu.

```cpp
void swap(basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Odwołanie lvalue do `basic_streambuf` obiektu, który jest używany do wymiany wartości.

### <a name="remarks"></a>Uwagi

Funkcja chronionego elementu członkowskiego *wymienia wszystkie wskaźniki* kontrolujące `input buffer` i `output buffer` . Wymienia również `right.` [getloc ()](#getloc) z `locale` obiektem.

## <a name="basic_streambufsync"></a><a name="sync"></a> basic_streambuf:: Sync

Chroniona funkcja wirtualna, która próbuje zsynchronizować kontrolowane strumienie ze wszystkimi skojarzonymi strumieniami zewnętrznymi.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść, zwraca wartość-1. Domyślne zachowanie ma zwrócić wartość zero.

### <a name="remarks"></a>Uwagi

`sync` polega na zapisywaniu wszelkich elementów między wskaźnikiem początkowym i następnym dla buforu danych wyjściowych. Nie obejmuje umieszczania żadnych elementów między następnymi i końcowymi wskaźnikami dla buforu wejściowego.

## <a name="basic_streambuftraits_type"></a><a name="traits_type"></a> basic_streambuf:: traits_type

Kojarzy nazwę typu z parametrem szablonu **TR** .

```cpp
typedef Tr traits_type;
```

## <a name="basic_streambufuflow"></a><a name="uflow"></a> basic_streambuf:: uflow

Chroniona funkcja wirtualna, która wyodrębnia bieżący element ze strumienia wejściowego.

```cpp
virtual int_type uflow();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący element.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualna elementu członkowskiego próbuje wyodrębnić bieżący element **ch** ze strumienia wejściowego, a następnie przejść do pozycji bieżąca pozycja strumienia i zwrócić element jako **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**). Można to zrobić na różne sposoby:

- Jeśli pozycja odczytu jest dostępna, przyjmuje wartość **ch** jako element zapisany w pozycji odczytu i przesuwa następny wskaźnik dla buforu wejściowego.

- Może odczytywać element bezpośrednio z zewnętrznego źródła i dostarczać go jako wartość **ch**.

- W przypadku bufora strumienia ze wspólnymi strumieniami wejściowymi i wyjściowymi można ustawić pozycję do odczytu, aby uzyskać dostęp do niektórych zewnętrznych miejsc docelowych, niektórych lub wszystkich elementów między wskaźnikiem początkowym i następnym dla buforu wyjściowego. Może też przydzielić nowy lub dodatkowy magazyn dla buforu wejściowego. Następnie funkcja odczytuje w, z zewnętrznego źródła, co najmniej jeden element.

Jeśli funkcja nie może się powieść, zwraca **traits_type::**[EOF](../standard-library/char-traits-struct.md#eof)lub zgłasza wyjątek. W przeciwnym razie zwraca bieżący element `ch` w strumieniu wejściowym, przekonwertowany zgodnie z powyższym opisem, i postępuje następnym wskaźnikiem dla buforu wejściowego. Domyślnym zachowaniem [jest wywołanie](#underflow) niedopełnienia i, jeśli ta funkcja zwraca **traits_type:: EOF**, aby zwrócić **traits_type:: EOF**. W przeciwnym razie funkcja zwraca bieżący element **ch** w strumieniu wejściowym, przekonwertowany w opisany wcześniej sposób i postępuje zgodnie z kolejnymi wskaźnikami dla buforu wejściowego.

## <a name="basic_streambufunderflow"></a><a name="underflow"></a> basic_streambuf:: niedopełnienie

Chroniona funkcja wirtualna w celu wyodrębnienia bieżącego elementu ze strumienia wejściowego.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący element.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualna elementu członkowskiego przedsięwzięciach do wyodrębnienia bieżącego elementu **ch** ze strumienia wejściowego, bez przesuwania bieżącej pozycji strumienia i zwracania go jako `traits_type::` [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **ch**). Można to zrobić na różne sposoby:

- Jeśli pozycja odczytu jest dostępna, **ch** jest elementem przechowywanym w pozycji odczytu. Aby uzyskać więcej informacji na ten temat, zobacz sekcję Uwagi [klasy basic_streambuf](../standard-library/basic-streambuf-class.md).

- Możliwe jest udostępnienie pozycji odczytu przez przydzielenie nowego lub dodatkowego magazynu dla buforu wejściowego, a następnie odczytanie w, od pewnego źródła zewnętrznego, co najmniej jednego elementu. Aby uzyskać więcej informacji na ten temat, zobacz sekcję Uwagi [klasy basic_streambuf](../standard-library/basic-streambuf-class.md).

Jeśli funkcja nie może się powieść, zwraca `traits_type::` [znacznik EOF](../standard-library/char-traits-struct.md#eof) `()` lub zgłosi wyjątek. W przeciwnym razie zwraca bieżący element w strumieniu wejściowym, przekonwertowany zgodnie z wcześniejszym opisem. Domyślne zachowanie to Return `traits_type::eof()` .

Funkcja wirtualna `underflow` , z funkcjami [synchronizacji](#sync) i [przepełniania](#overflow) , definiuje cechy `streambuf` klasy pochodnej. Każda klasa pochodna może zaimplementować się `underflow` inaczej, ale interfejs z klasą strumienia wywołującego jest taki sam.

`underflow`Funkcja jest najczęściej wywoływana przez `streambuf` funkcje publiczne, takie jak [sgetc —](#sgetc) i [sgetn](#sgetn) , gdy obszar pobierania jest pusty, ale inne klasy, w tym klasy strumienia, mogą wywołać w `underflow` dowolnym czasie.

`underflow`Funkcja dostarcza obszar pobierania ze znakami ze źródła danych wejściowych. Jeśli pole Pobierz zawiera znaki, `underflow` zwraca pierwszy znak. Jeśli obszar pobierania jest pusty, wypełnia obszar Pobierz i zwraca następny znak (który opuszcza obszar pobierania). Jeśli nie ma więcej dostępnych znaków, `underflow` Funkcja zwraca `EOF` i pozostawia pusty obszar pobierania.

W `strstreambuf` klasie `underflow` dostosowuje wskaźnik [egptr](#egptr) , aby uzyskać dostęp do magazynu, który został dynamicznie przydzielony przez wywołanie `overflow` .

## <a name="basic_streambufxsgetn"></a><a name="xsgetn"></a> basic_streambuf:: xsgetn

Chroniona funkcja wirtualna w celu wyodrębnienia elementów ze strumienia wejściowego.

Ta metoda jest potencjalnie niebezpieczna, ponieważ polega na wywołującym, aby sprawdzić, czy przeszukane wartości są poprawne.

```cpp
virtual streamsize xsgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*PTR*\
Bufor zawierający wyodrębnione znaki.

*liczbą*\
Liczba elementów do wyodrębnienia.

### <a name="return-value"></a>Wartość zwracana

Liczba wyodrębnionych elementów.

### <a name="remarks"></a>Uwagi

Chroniona wirtualna funkcja członkowska wyodrębnia do *liczby* elementów ze strumienia wejściowego, tak jak gdyby powtarzające się wywołania [sbumpc —](#sbumpc)i zapisuje je w tablicy rozpoczynającej się od *PTR*. Zwraca liczbę elementów, które faktycznie zostały wyodrębnione.

## <a name="basic_streambufxsputn"></a><a name="xsputn"></a> basic_streambuf:: xsputn

Chroniona funkcja wirtualna, która umożliwia wstawianie elementów do strumienia wyjściowego.

```cpp
virtual streamsize xsputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Parametry

*PTR*\
Wskaźnik do elementów do wstawienia.

*liczbą*\
Liczba elementów do wstawienia.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów rzeczywiście wstawionych do strumienia.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualna elementu członkowskiego wstawia do *liczby* elementów w strumieniu danych wyjściowych, tak jak gdyby przez powtarzające się wywołania [sputc](#sputc), od tablicy rozpoczynającej się o *PTR*. Wstawianie znaków do strumienia wyjściowego zostaje zatrzymane po zapisaniu wszystkich znaków *Count* lub wywołania `sputc( count)` zostałyby zwrócone `traits::eof()` . Zwraca liczbę elementów, które faktycznie wstawiono.

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostreams](../standard-library/iostreams-conventions.md)
