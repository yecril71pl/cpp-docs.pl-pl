---
title: basic_streambuf — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6bc4fa8da5d9fa2d15febc3c7b016622e614129a
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44100966"
---
# <a name="basicstreambuf-class"></a>basic_streambuf — Klasa

W tym artykule opisano abstrakcyjną klasę bazową dla elementu pochodnego dla buforu strumienia, który kontroluje przekazywanie elementów do i z reprezentację określonego strumienia.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>>
class basic_streambuf;
```

### <a name="parameters"></a>Parametry

*Elem*<br/>
A [char_type](#char_type).

*TR*<br/>
Znak [traits_type](#traits_type).

## <a name="remarks"></a>Uwagi

Klasa szablonu opisuje abstrakcyjną klasę bazową dla elementu pochodnego dla buforu strumienia, który kontroluje przekazywanie elementów do i z reprezentację określonego strumienia. Obiekt klasy `basic_streambuf` ułatwia kontrolowanie strumieni elementami typu *Tr*, znane również jako [char_type](#char_type), którego cech są określane przez klasę [char_traits](../standard-library/char-traits-struct.md), znane również jako [traits_type](#traits_type).

Każdy bufor strumienia koncepcyjnie kontroluje dwa niezależne strumienie: jeden dla wyodrębniania (dane wejściowe) i jeden do wstawienia (dane wyjściowe). Reprezentacja określonych może jednak wprowadzać jedną lub obie te strumienie niedostępny. On zazwyczaj zachowuje niektóre relacji między dwóch strumieni. Wstaw w strumieniu wyjściowym [basic_stringbuf —](../standard-library/basic-stringbuf-class.md)< `Elem`, `Tr`> obiektu, na przykład to, co później wyodrębniane z jego strumienia wejściowego. Gdy umieścisz jednym strumień [basic_filebuf —](../standard-library/basic-filebuf-class.md)< `Elem`, `Tr`> obiektu, umieść usługi stream w tandem.

Publiczny interfejs do szablonu klasy `basic_streambuf` dostarcza operacje, które są wspólne dla wszystkich buforów strumienia, jednak przeznaczone. Interfejs chroniony dostarcza operacje do wykonania swojej pracy służące do reprezentację określonego strumienia. Funkcje chroniony element członkowski wirtualnego pozwalają dostosować zachowanie bufor strumienia pochodnych dla reprezentację określonego strumienia. Każdy bufor strumienia pochodnych w tej bibliotece opisano, jak specjalizuje się zachowanie jego chronionych wirtualnych funkcji elementów członkowskich. Domyślne zachowanie dla klasy bazowej, co jest często, aby nic nie rób, jest opisane w tym temacie.

Pozostałe chronione kopiowanie do i z magazynu przekazana do buforu transmisji do i z strumieni kontrola funkcji elementów członkowskich. Bufor wejściowy, na przykład charakteryzuje się:

- [eback —](#eback), wskaźnik do początku bufora.

- [gptr —](#gptr), wskaźnik do następnego elementu do odczytu.

- [egptr —](#egptr), wskaźnikiem, tylko poza końcem bufor.

Podobnie bufor wyjściowy jest określony przez:

- [pbase —](#pbase), wskaźnik do początku bufora.

- [pptr —](#pptr), wskaźnik do następnego elementu do zapisania.

- [epptr —](#epptr), wskaźnikiem, tylko poza końcem bufor.

Dla dowolnego buforu jest używany protokół następujące:

- Jeśli wskaźnik następnej ma wartość null, bez buforowania nie istnieje. W przeciwnym razie wszystkie trzy wskaźniki wskazują do takiej samej kolejności. Można bezpiecznie porównywane dla zamówienia.

- Dla buforu danych wyjściowych, jeśli wskaźnik następnej porównuje mniejszą od zakończenia wskaźnika, możesz zapisać element w wyznaczonym przez wskaźnik następnej pozycji zapisu.

- Dla buforu danych wejściowych Jeśli wskaźnik następnej porównuje mniejszą od zakończenia wskaźnika, możesz przeczytać elementu pozycja odczytu wyznaczonym przez wskaźnik następnej.

- Dla buforu danych wejściowych Jeśli wskaźnik początku porównuje mniej niż wskaźnik następnej możesz umieścić ponownie element w położeniu putback — wyznaczony przez zmniejszony wskaźnik następnej.

Chronione dowolnej funkcji wirtualnych elementów członkowskich zapisu dla klasą pochodną `basic_streambuf` <  `Elem`, `Tr`> muszą współpracować przy zachowaniu tego protokołu.

Obiekt klasy `basic_streambuf` <  `Elem`, `Tr`> przechowuje sześć wskaźników, które opisano wcześniej. Przechowuje także obiekt ustawień regionalnych w obiekcie typu [ustawień regionalnych](../standard-library/locale-class.md) do potencjalnych użytku przez bufor strumienia pochodnych.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_streambuf](#basic_streambuf)|Tworzy obiekt typu `basic_streambuf`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[char_type](#char_type)|Kojarzy nazwę typu z `Elem` parametru szablonu.|
|[int_type](#int_type)|Kojarzy nazwę typu, w ramach `basic_streambuf` zakresu przy użyciu `Elem` parametru szablonu.|
|[off_type](#off_type)|Kojarzy nazwę typu, w ramach `basic_streambuf` zakresu przy użyciu `Elem` parametru szablonu.|
|[pos_type](#pos_type)|Kojarzy nazwę typu, w ramach `basic_streambuf` zakresu przy użyciu `Elem` parametru szablonu.|
|[traits_type](#traits_type)|Kojarzy nazwę typu z `Tr` parametru szablonu.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[eback](#eback)|Funkcja chronionych, która zwraca wskaźnik do początku bufora wejściowego.|
|[egptr](#egptr)|Funkcja chronionych, która zwraca wskaźnik po prostu poza końcem bufor wejściowy.|
|[epptr —](#epptr)|Funkcja chronionych, która zwraca wskaźnik po prostu poza końcem bufor wyjściowy.|
|[gbump —](#gbump)|Chronione funkcja, która dodaje `count` dalej wskaźnik do buforu wejściowego.|
|[getloc](#getloc)|Pobiera `basic_streambuf` obiektu ustawień regionalnych.|
|[gptr](#gptr)|Funkcja chronionych, która zwraca wskaźnik do następnego elementu buforu wejściowego.|
|[imbue](#imbue)|Chroniona, funkcja wirtualna wywoływana [pubimbue —](#pubimbue).|
|[in_avail](#in_avail)|Zwraca liczbę elementów, które są gotowe do odczytu z buforu.|
|[overflow](#overflow)|Chronione funkcja wirtualna, która może być wywoływana po wstawieniu do buforu pełnej nowego znaku.|
|[pbackfail](#pbackfail)|Funkcja chronionych wirtualna elementu członkowskiego, która podejmuje próbę odłożyć element do strumienia wejściowego, a następnie spraw, bieżącego elementu (wskazywany przez wskaźnik następnej).|
|[pbase](#pbase)|Funkcja chronionych, która zwraca wskaźnik do początku bufora wyjściowego.|
|[pbump —](#pbump)|Chronione funkcja, która dodaje `count` dalej wskaźnik dla buforu danych wyjściowych.|
|[pptr —](#pptr)|Funkcja chronionych, która zwraca wskaźnik do następnego elementu bufor wyjściowy.|
|[pubimbue](#pubimbue)|Zestawy `basic_streambuf` obiektu ustawień regionalnych.|
|[pubseekoff](#pubseekoff)|Wywołania [seekoff —](#seekoff), chroniona funkcja wirtualna, która została zastąpiona w klasie pochodnej.|
|[pubseekpos](#pubseekpos)|Wywołania [seekpos —](#seekpos), chroniona funkcja wirtualna, która zostanie zastąpiona w klasie pochodnej, a ponadto resetuje bieżącą pozycję wskaźnika.|
|[pubsetbuf](#pubsetbuf)|Wywołania [setbuf —](#setbuf), chroniona funkcja wirtualna, która została zastąpiona w klasie pochodnej.|
|[pubsync](#pubsync)|Wywołania [synchronizacji](#sync), chroniona funkcja wirtualna, która zostanie zastąpiona w klasie pochodnej i aktualizuje zewnętrznych strumienia, skojarzonego z tego buforu.|
|[sbumpc](#sbumpc)|Odczytuje i zwraca bieżący element, przesuwając wskaźnik strumienia.|
|[seekoff](#seekoff)|Chronione wirtualna funkcja składowa próbuje alter dla strumieni kontrolowanego bieżącej pozycji.|
|[seekpos —](#seekpos)|Chronione wirtualna funkcja składowa próbuje alter dla strumieni kontrolowanego bieżącej pozycji.|
|[setbuf](#setbuf)|Funkcja chroniony element członkowski wirtualnego wykonuje określonego operacji, aby każdy bufor strumienia pochodnej.|
|[setg —](#setg)|Chronione funkcja, która przechowuje `_Gbeg` we wskaźniku początku `_Gnext` we wskaźniku dalej i `_Gend` we wskaźniku zakończenia dla buforu danych wejściowych.|
|[setp —](#setp)|Chronione funkcja, która przechowuje `_Pbeg` we wskaźniku początku i `_Pend` we wskaźniku zakończenia dla buforu danych wyjściowych.|
|[sgetc](#sgetc)|Zwraca bieżący element bez zmiany pozycji w strumieniu.|
|[sgetn](#sgetn)|Zwraca liczbę elementów odczytu.|
|[showmanyc —](#showmanyc)|Chroniona funkcja wirtualna elementu członkowskiego, która zwraca liczbę znaków, które można wyodrębnić ze strumienia wejściowego i upewnij się, że program, nie będą poddawani uwierzytelnianiu nieograniczonego oczekiwania.|
|[snextc](#snextc)|Odczytuje bieżący element i zwraca następujący element.|
|[sputbackc](#sputbackc)|Umieszcza `char_type` w strumieniu.|
|[sputc —](#sputc)|Umieszcza znak w strumieniu.|
|[sputn](#sputn)|Umieszcza ciąg znaków do strumienia.|
|[stossc](#stossc)|Przenieś poza bieżący element w strumieniu.|
|[sungetc](#sungetc)|Pobiera znak ze strumienia.|
|[swap](#swap)|Wymienia wartości w tym obiekcie wartości w określonych `basic_streambuf` obiektu parametru.|
|[sync](#sync)|Chronione funkcja wirtualna, która podejmuje próbę synchronizował kontrolowanego strumienie skojarzone strumieni zewnętrznych.|
|[uflow](#uflow)|Chronione funkcja wirtualna, która wyodrębnia bieżącego elementu ze strumienia wejściowego.|
|[underflow](#underflow)|Chronione funkcja wirtualna, która wyodrębnia bieżącego elementu ze strumienia wejściowego.|
|[xsgetn](#xsgetn)|Chronione funkcja wirtualna, która wyodrębnia elementy ze strumienia wejściowego.|
|[xsputn](#xsputn)|Chronione funkcja wirtualna, która wstawia elementy do strumienia wyjściowego.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator=](#op_eq)|Przypisuje wartość tego obiektu z innego `basic_streambuf` obiektu.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<streambuf >

**Namespace:** standardowe

## <a name="basic_streambuf"></a>  basic_streambuf::basic_streambuf

Tworzy obiekt typu `basic_streambuf`.

```cpp
basic_streambuf();

basic_streambuf(const basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Odwołania wartościowanego lewostronnie do `basic_streambuf` obiekt, który służy do ustawiania wartości dla tego `basic_streambuf` obiektu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor chroniony przechowuje wskaźnik zerowy w wszystkie wskaźniki kontrolowanie buforu wejściowego i bufor wyjściowy. Przechowuje także `locale::classic` w obiekcie ustawień regionalnych. Aby uzyskać więcej informacji, zobacz [locale::classic](../standard-library/locale-class.md#classic).

Drugi Konstruktor chroniony kopiuje wskaźników i ustawienia regionalne *prawo*.

## <a name="char_type"></a>  basic_streambuf::char_type

Kojarzy nazwę typu z **Elem** parametru szablonu.

```cpp
typedef Elem char_type;
```

## <a name="eback"></a>  basic_streambuf::eback

Funkcja chronionych, która zwraca wskaźnik do początku bufora wejściowego.

```cpp
char_type *eback() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku bufora wejściowego.

## <a name="egptr"></a>  basic_streambuf::egptr

Funkcja chronionych, która zwraca wskaźnik po prostu poza końcem bufor wejściowy.

```cpp
char_type *egptr() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik po prostu poza końcem bufor wejściowy.

## <a name="epptr"></a>  basic_streambuf::epptr

Funkcja chronionych, która zwraca wskaźnik po prostu poza końcem bufor wyjściowy.

```cpp
char_type *epptr() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik po prostu poza końcem bufor wyjściowy.

## <a name="gbump"></a>  basic_streambuf::gbump

Chronione funkcja, która dodaje *liczba* dalej wskaźnik do buforu wejściowego.

```cpp
void gbump(int count);
```

### <a name="parameters"></a>Parametry

*Liczba*<br/>
Kwota za pomocą którego pomocnych wskaźnika.

## <a name="getloc"></a>  basic_streambuf::getloc

Pobiera obiekt basic_streambuf ustawień regionalnych.

```cpp
locale getloc() const;
```

### <a name="return-value"></a>Wartość zwracana

Obiekt przechowywanych ustawień regionalnych.

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

## <a name="gptr"></a>  basic_streambuf::gptr

Funkcja chronionych, która zwraca wskaźnik do następnego elementu buforu wejściowego.

```cpp
char_type *gptr() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego elementu buforu wejściowego.

## <a name="imbue"></a>  basic_streambuf::imbue

Chroniona funkcja wirtualna wywoływana [pubimbue —](#pubimbue).

```cpp
virtual void imbue(const locale& _Loc);
```

### <a name="parameters"></a>Parametry

*_Loc*<br/>
Odwołanie do ustawienia regionalne.

### <a name="remarks"></a>Uwagi

Domyślnym zachowaniem jest nic nie rób.

## <a name="in_avail"></a>  basic_streambuf::in_avail

Zwraca liczbę elementów, które są gotowe do odczytu z buforu.

```cpp
streamsize in_avail();
```

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, które są gotowe do odczytu z buforu.

### <a name="remarks"></a>Uwagi

Jeśli [pozycja odczytu](../standard-library/basic-streambuf-class.md) jest dostępny, funkcja elementu członkowskiego zwraca [egptr —](#egptr) - [gptr —](#gptr). W przeciwnym razie zwraca [showmanyc —](#showmanyc).

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

## <a name="int_type"></a>  basic_streambuf::int_type

Kojarzy nazwę typu w zakresie basic_streambuf przy użyciu jednego z typów w parametrze szablonu.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>  basic_streambuf::off_type

Kojarzy nazwę typu w zakresie basic_streambuf przy użyciu jednego z typów w parametrze szablonu.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="op_eq"></a>  basic_streambuf::operator =

Przypisuje wartość tego obiektu z innego `basic_streambuf` obiektu.

```cpp
basic_streambuf& operator=(const basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

*right*<br/>
Odwołania wartościowanego lewostronnie do `basic_streambuf` obiekt, który jest używany do przypisywania wartości do tego obiektu.

### <a name="remarks"></a>Uwagi

Operator chroniony element członkowski kopiuje z *prawo* wskaźników, które kontrolują buforu wejściowego i bufor wyjściowy. Przechowuje także `right.` [getloc()](#getloc) w `locale object`. Zwraca `*this`.

## <a name="overflow"></a>  basic_streambuf::Overflow

Chronione funkcja wirtualna, która może być wywoływana po wstawieniu do buforu pełnej nowego znaku.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*<br/>
Znak do wstawienia do określonego bufora lub **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie powiedzie się, zwraca **traits_type::eof** ani nie zgłasza wyjątku. W przeciwnym razie zwraca **traits_type::**[not_eof —](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*). Zachowanie domyślne ma zwracać **traits_type::eof**.

### <a name="remarks"></a>Uwagi

Jeśli _ *Meta* porównuje równa **traits_type::eof**, chronionych wirtualna funkcja składowa usiłują Wstaw element **traits_type::**[_Z char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*) do strumienia wyjściowego. Jego można to zrobić na różne sposoby:

- Jeśli `write position` jest dostępny, można przechowywać element w określonej pozycji zapisu i zwiększyć wskaźnik następnej dla buforu danych wyjściowych.

- Go można udostępnić pozycji zapisu, przydzielając nowej lub dodatkowej pamięci masowej dla buforu danych wyjściowych.

- Ją udostępnić pozycji zapisu, wskaźniki zapisywania na poziomie, aby niektóre zewnętrznego miejsca docelowego, niektóre lub wszystkie elementy od początku i dalej dla buforu danych wyjściowych.

Funkcja przepełnienie wirtualnej wraz z [synchronizacji](#sync) i [niedopełnienie](#underflow) funkcje, określa właściwości klasy pochodnej streambuf. Każda klasa pochodna może zaimplementować przepełnienie inaczej, ale interfejs z wywołującym klasa strumienia jest taka sama.

`overflow` Funkcja najczęściej jest wywoływana przez publiczną `streambuf` funkcje, takie jak `sputc` i `sputn` podczas umieszczania obszaru, ale inne klasy, w tym klasy strumieni może wywołać `overflow` porze.

Funkcja używa znaków w obszarze put między `pbase` i `pptr` wskaźników i następnie ponownie inicjuje put obszaru. `overflow` Funkcji również musi używać `nCh` (Jeśli `nCh` nie `EOF`), lub warto umieścić umieścić obszaru w znaku w nowym, dzięki czemu zostanie wchłonięta przy następnym wywołaniu.

Definicja zużywania waha się między klas pochodnych. Na przykład `filebuf` klasy zapisuje jego znaki do pliku, podczas gdy `strstreambuf` klasa przechowuje je w swoim buforze i (Jeśli bufor jest wyznaczony jako dynamiczne) rozszerza buforu w odpowiedzi na wywołanie przepełnienia. To rozwinięcie jest osiągane przy zwalnianiu bufor starego i wymiana go na nowy, większy. Wskaźniki są dostosowywane gdy jest to konieczne.

## <a name="pbackfail"></a>  basic_streambuf::pbackfail

Funkcja chronionych wirtualna elementu członkowskiego, która podejmuje próbę odłożyć element do strumienia wejściowego, a następnie spraw, bieżącego elementu (wskazywany przez wskaźnik następnej).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*<br/>
Znak do wstawienia do określonego bufora lub **traits_type::**[eof](../standard-library/char-traits-struct.md#eof).

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie powiedzie się, zwraca **traits_type::eof** ani nie zgłasza wyjątku. W przeciwnym razie zwraca inną wartość. Zachowanie domyślne ma zwracać **traits_type::eof**.

### <a name="remarks"></a>Uwagi

Jeśli _ *Meta* porównuje równa **traits_type::eof**, element do usunięcia jest skutecznie już w strumieniu przed bieżącego elementu. W przeciwnym razie ten element został zastąpiony **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*). Funkcję można odłożyć element na różne sposoby:

- Jeśli pozycja putback — jest dostępny, można przechowywać element w określonej pozycji putback — i dekrementacji wskaźnik następnej dla buforu danych wejściowych.

- Może sprawić, że pozycja putback — dostępne przez przydzielanie magazynu do nowej lub dodatkowej dla buforu danych wejściowych.

- Dla buforu strumienia z typowymi danymi wejściowymi i strumienie wyjściowe ją udostępnić pozycji putback —, wskaźniki zapisywania na poziomie, aby niektóre zewnętrznego miejsca docelowego, niektóre lub wszystkie elementy od początku i dalej dla buforu danych wyjściowych.

## <a name="pbase"></a>  basic_streambuf::pbase

Funkcja chronionych, która zwraca wskaźnik do początku bufora wyjściowego.

```cpp
char_type *pbase() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do początku bufora wyjściowego.

## <a name="pbump"></a>  basic_streambuf::pbump

Chronione funkcja, która dodaje *liczba* dalej wskaźnik dla buforu danych wyjściowych.

```cpp
void pbump(int count);
```

### <a name="parameters"></a>Parametry

*Liczba*<br/>
Liczba znaków, w ramach którego ma zostać przeniesiona do przodu pozycji zapisu.

## <a name="pos_type"></a>  basic_streambuf::pos_type

Kojarzy nazwę typu w zakresie basic_streambuf przy użyciu jednego z typów w parametrze szablonu.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="pptr"></a>  basic_streambuf::pptr

Funkcja chronionych, która zwraca wskaźnik do następnego elementu bufor wyjściowy.

```cpp
char_type *pptr() const;
```

### <a name="return-value"></a>Wartość zwracana

Wskaźnik do następnego elementu bufor wyjściowy.

## <a name="pubimbue"></a>  basic_streambuf::pubimbue

Ustawia ustawienia regionalne obiektu basic_streambuf.

```cpp
locale pubimbue(const locale& _Loc);
```

### <a name="parameters"></a>Parametry

*_Loc*<br/>
Odwołanie do ustawienia regionalne.

### <a name="return-value"></a>Wartość zwracana

Poprzednią wartość przechowywana w obiekcie ustawień regionalnych.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zapisuje _ *Loc* obiektu ustawień regionalnych i wywołania [imbue —](#imbue).

### <a name="example"></a>Przykład

Zobacz [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue) przykład, który używa `pubimbue`.

## <a name="pubseekoff"></a>  basic_streambuf::pubseekoff

Wywołania [seekoff —](#seekoff), chroniona funkcja wirtualna, która została zastąpiona w klasie pochodnej.

```cpp
pos_type pubseekoff(off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Położenie do wyszukania dla względem *_Way*.

*_Way*<br/>
Punkt początkowy dla operacji przesunięcia. Zobacz [seekdir](../standard-library/ios-base-class.md#seekdir) uzyskać odpowiednie wartości.

*_Which*<br/>
Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji.

### <a name="return-value"></a>Wartość zwracana

Zwraca nową pozycję lub nieprawidłowy strumień pozycji ( [seekoff —](#seekoff)(_ *poza*, `_Way`, `_Which`)).

### <a name="remarks"></a>Uwagi

Przesuwa wskaźnik myszy względem *_Way*.

## <a name="pubseekpos"></a>  basic_streambuf::pubseekpos

Wywołania [seekpos —](#seekpos), chroniona funkcja wirtualna, która zostanie zastąpiona w klasie pochodnej i resetuje bieżącą pozycję wskaźnika.

```cpp
pos_type pubseekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*<br/>
Położenie do wyszukania dla.

*_Which*<br/>
Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji.

### <a name="return-value"></a>Wartość zwracana

Nowa pozycja lub pozycji nieprawidłowy strumień. Aby określić, jeśli pozycja strumienia jest nieprawidłowa, porównaj wartość zwracaną z `pos_type(off_type(-1))`.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [seekpos —](#seekpos)(_ *Sp*, `_Which`).

## <a name="pubsetbuf"></a>  basic_streambuf::pubsetbuf

Wywołania [setbuf —](#setbuf), chroniona funkcja wirtualna, która została zastąpiona w klasie pochodnej.

```cpp
basic_streambuf<Elem, Tr> *pubsetbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*Właściwość _Buffer*<br/>
Wskaźnik do `char_type` dla tego wystąpienia.

*Liczba*<br/>
Rozmiar buforu.

### <a name="return-value"></a>Wartość zwracana

Zwraca [setbuf —](#setbuf)( `_Buffer`, `count`).

## <a name="pubsync"></a>  basic_streambuf::pubsync

Wywołania [synchronizacji](#sync), chroniona funkcja wirtualna, która zostanie zastąpiona w klasie pochodnej i aktualizuje zewnętrznych strumienia, skojarzonego z tego buforu.

```cpp
int pubsync();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca [synchronizacji](#sync) lub wartość-1 w przypadku awarii.

## <a name="sbumpc"></a>  basic_streambuf::sbumpc

Odczytuje i zwraca bieżący element, przesuwając wskaźnik strumienia.

```cpp
int_type sbumpc();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący element.

### <a name="remarks"></a>Uwagi

Jeśli pozycji odczytu jest dostępny, funkcja elementu członkowskiego zwraca **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( <strong>\*</strong> [gptr —](#gptr)) i zwiększa narastająco wskaźnik następnej dla buforu danych wejściowych. W przeciwnym razie zwraca [uflow —](#uflow).

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

## <a name="seekoff"></a>  basic_streambuf::seekoff

Funkcja chronionych wirtualna elementu członkowskiego, która próbuje zmienić dla strumieni kontrolowanego bieżącej pozycji.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Położenie do wyszukania dla względem *_Way*.

*_Way*<br/>
Punkt początkowy dla operacji przesunięcia. Zobacz [seekdir](../standard-library/ios-base-class.md#seekdir) uzyskać odpowiednie wartości.

*_Which*<br/>
Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji.

### <a name="return-value"></a>Wartość zwracana

Zwraca nową pozycję lub nieprawidłowy strumień pozycji ( `seekoff` (_ *poza*, `_Way`, `_Which`)).

### <a name="remarks"></a>Uwagi

Nowa pozycja jest określany w następujący sposób:

- Jeśli `_Way`  ==  `ios_base::beg`, nowe położenie jest na początku strumienia oraz _ *poza*.

- Jeśli `_Way`  ==  `ios_base::cur`, nowe położenie jest bieżącą pozycję w strumieniu oraz _ *poza*.

- Jeśli `_Way`  ==  `ios_base::end`, nowe położenie jest na końcu strumienia oraz _ *poza*.

Zazwyczaj Jeśli **jaki & ios_base::in** jest różna od zera, strumienia wejściowego zostanie objęty zmianą i, jeśli **jaki & ios_base::out** jest różna od zera, strumienia wyjściowego. ma to wpływ na. Rzeczywiste użycie tego parametru waha się między buforach strumieni pochodnej, jednak.

Jeśli funkcja się powiedzie, w zmiany pozycji strumienia lub stanowiska, zwraca wynikowy pozycji strumienia lub jeden wynikowy pozycji strumienia. W przeciwnym razie zwraca położenie nieprawidłowy strumień. Zachowanie domyślne jest zwracać pozycji nieprawidłowy strumień.

## <a name="seekpos"></a>  basic_streambuf::seekpos

Funkcja chronionych wirtualna elementu członkowskiego, która próbuje zmienić dla strumieni kontrolowanego bieżącej pozycji.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Which = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*<br/>
Położenie do wyszukania dla.

*_Which*<br/>
Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji.

### <a name="return-value"></a>Wartość zwracana

Nowa pozycja lub nieprawidłowy strumień pozycji. Aby określić, jeśli pozycja strumienia jest nieprawidłowa, porównaj wartość zwracaną z `pos_type(off_type(-1))`.

### <a name="remarks"></a>Uwagi

Nowe położenie jest _ *Sp*.

Zazwyczaj Jeśli **jaki & ios_base::in** jest różna od zera, strumienia wejściowego zostanie objęty zmianą i, jeśli **jaki & ios_base::out** jest różna od zera, strumienia wyjściowego. ma to wpływ na. Rzeczywiste użycie tego parametru waha się między buforach strumieni pochodnej, jednak.

Jeśli funkcja się powiedzie, w zmiany pozycji strumienia lub stanowiska, zwraca wynikowy pozycji strumienia lub jeden wynikowy pozycji strumienia. W przeciwnym razie zwraca położenie nieprawidłowy strumień (-1). Zachowanie domyślne jest zwracać pozycji nieprawidłowy strumień.

## <a name="setbuf"></a>  basic_streambuf::setbuf

Funkcja chronionych wirtualna elementu członkowskiego, która wykonuje określonego operacji, aby każdy bufor strumienia pochodnej.

```cpp
virtual basic_streambuf<Elem, Tr> *setbuf(
    char_type* _Buffer,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*Właściwość _Buffer*<br/>
Wskaźnik do buforu.

*Liczba*<br/>
Rozmiar buforu.

### <a name="return-value"></a>Wartość zwracana

Zachowanie domyślne ma zwracać **to**.

### <a name="remarks"></a>Uwagi

Zobacz [basic_filebuf —](../standard-library/basic-filebuf-class.md). `setbuf` zapewnia to obszar pamięci dla `streambuf` obiekt ma być używany. Jak rozmiar buforu jest używany w zdefiniowana w klasach pochodnych.

## <a name="setg"></a>  basic_streambuf::setg

Chronione funkcja, która przechowuje _ *Gbeg* we wskaźniku początku `_Gnext` we wskaźniku dalej i `_Gend` we wskaźniku zakończenia dla buforu danych wejściowych.

```cpp
void setg(char_type* _Gbeg,
    char_type* _Gnext,
    char_type* _Gend);
```

### <a name="parameters"></a>Parametry

*_Gbeg*<br/>
Wskaźnik do początku bufora.

*_Gnext*<br/>
Wskaźnik do innej lokalizacji w środku buforu.

*_Gend*<br/>
Wskaźnik na koniec buforu.

## <a name="setp"></a>  basic_streambuf::setp

Chronione funkcja, która przechowuje *_Pbeg* we wskaźniku początku i *_Pend* we wskaźniku zakończenia dla buforu danych wyjściowych.

```cpp
void setp(char_type* _Pbeg, char_type* _Pend);
```

### <a name="parameters"></a>Parametry

*_Pbeg*<br/>
Wskaźnik do początku bufora.

*_Pend*<br/>
Wskaźnik na koniec buforu.

## <a name="sgetc"></a>  basic_streambuf::sgetc

Zwraca bieżący element bez zmiany pozycji w strumieniu.

```cpp
int_type sgetc();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący element.

### <a name="remarks"></a>Uwagi

Jeśli pozycji odczytu jest dostępny, funkcja elementu członkowskiego zwraca **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*` [gptr —](#gptr)). W przeciwnym razie zwraca [niedopełnienie](#underflow).

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

## <a name="sgetn"></a>  basic_streambuf::sgetn

Wyodrębnia maksymalnie *liczba* znaków z bufora wejściowego i przechowuje je w dostarczonego buforu *ptr*.

Ta metoda jest potencjalnie niebezpieczne, ponieważ opiera się na obiekt wywołujący, aby sprawdzić, czy przekazanych wartości są poprawne.

```cpp
streamsize sgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Bufor do przechowywania wyodrębnione znaki.

*Liczba*<br/>
Liczba elementów do odczytu.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów do odczytu. Zobacz [streamsize](../standard-library/ios-typedefs.md#streamsize) Aby uzyskać więcej informacji.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [xsgetn —](#xsgetn)( `ptr`, `count`).

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

## <a name="showmanyc"></a>  basic_streambuf::showmanyc

Funkcja chronionych wirtualna elementu członkowskiego, która zwraca liczbę znaków, które można wyodrębnić ze strumienia wejściowego i upewnij się, że program, nie będą poddawani uwierzytelnianiu nieograniczonego oczekiwania.

```cpp
virtual streamsize showmanyc();
```

### <a name="return-value"></a>Wartość zwracana

Domyślnym zachowaniem jest, aby zwrócić zero.

## <a name="snextc"></a>  basic_streambuf::snextc

Odczytuje bieżący element i zwraca następujący element.

```cpp
int_type snextc();
```

### <a name="return-value"></a>Wartość zwracana

Następny element w strumieniu.

### <a name="remarks"></a>Uwagi

Wywołania funkcji elementu członkowskiego [sbumpc —](#sbumpc) i, jeśli ta funkcja zwraca **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), zwraca **traits_type::eof**. W przeciwnym razie zwraca [sgetc —](#sgetc).

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

## <a name="sputbackc"></a>  basic_streambuf::sputbackc

Umieszcza char_type w strumieniu.

```cpp
int_type sputbackc(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*<br/>
Znak.

### <a name="return-value"></a>Wartość zwracana

Zwraca znak lub niepowodzenie.

### <a name="remarks"></a>Uwagi

Jeśli pozycja putback — jest dostępna i *_Ch* porównuje równa się znak umieszczane w tym miejscu zmniejsza funkcja elementu członkowskiego wskaźnik następnej buforu wejściowego i zwraca **traits_type::** [ to_int_type —](../standard-library/char-traits-struct.md#to_int_type)( `_Ch`). W przeciwnym razie zwraca [pbackfail —](#pbackfail)( `_Ch`).

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

## <a name="sputc"></a>  basic_streambuf::sputc

Umieszcza znak w strumieniu.

```cpp
int_type sputc(char_type _Ch);
```

### <a name="parameters"></a>Parametry

*_Ch*<br/>
Znak.

### <a name="return-value"></a>Wartość zwracana

Zwraca znak, jeśli to się powiedzie.

### <a name="remarks"></a>Uwagi

Jeśli `write position` jest dostępny, magazyny funkcja elementu członkowskiego *_Ch* w pozycji zapisu zwiększa wskaźnik następnej dla buforu danych wyjściowych, a następnie zwraca **traits_type::**[to_int_type ](../standard-library/char-traits-struct.md#to_int_type)( `_Ch`). W przeciwnym razie zwraca [przepełnienie](#overflow)( `_Ch`).

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

## <a name="sputn"></a>  basic_streambuf::sputn

Umieszcza ciąg znaków do strumienia.

```cpp
streamsize sputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Ciąg znaków.

*Liczba*<br/>
Liczba znaków.

### <a name="return-value"></a>Wartość zwracana

Liczba znaków rzeczywiście włożenia do strumienia.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca [xsputn —](#xsputn)( `ptr`, `count`). Zobacz sekcję Spostrzeżenia tego elementu członkowskiego, aby uzyskać więcej informacji.

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

## <a name="stossc"></a>  basic_streambuf::stossc

Przenieś poza bieżący element w strumieniu.

```cpp
void stossc();
```

### <a name="remarks"></a>Uwagi

Wywołania funkcji elementu członkowskiego [sbumpc —](#sbumpc). Należy zauważyć, że implementacja interfejsu nie jest wymagane do dostarczania tej funkcji elementu członkowskiego.

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

## <a name="sungetc"></a>  basic_streambuf::sungetc

Pobiera znak ze strumienia.

```cpp
int_type sungetc();
```

### <a name="return-value"></a>Wartość zwracana

Zwraca znak lub niepowodzenie.

### <a name="remarks"></a>Uwagi

Jeśli pozycja putback — jest dostępna, funkcję członkowską zmniejsza wskaźnik następnej buforu wejściowego i zwraca `traits_type::` [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( `*` [gptr —](#gptr)). Jednak nie zawsze jest możliwe określenie ostatniego przeczytanego znak, dzięki czemu mogą być przechwytywane w stanie bieżącego buforu. Jeśli to PRAWDA, wówczas funkcja zwraca [pbackfail —](#pbackfail). Aby uniknąć tej sytuacji, zachować informacje o znaku odłożyć i wywoływać `sputbackc(ch)`, które nie zakończą się niepowodzeniem podana nie wywołasz ją na początku strumienia i nie próbuj ponownie umieścić więcej niż jeden znak.

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

## <a name="swap"></a>  basic_streambuf::swap

Wymienia wartości w tym obiekcie wartości w określonych `basic_streambuf` obiektu.

```cpp
void swap(basic_streambuf& right);
```

### <a name="parameters"></a>Parametry

|Parametr|Opis|
|---------------|-----------------|
|*right*|Odwołania wartościowanego lewostronnie do `basic_streambuf` obiekt, który jest używany do wymiany wartości.|

### <a name="remarks"></a>Uwagi

Chroniona funkcja elementu członkowskiego wymienia z *prawo* wszystkie wskaźniki kontrolowanie `input buffer` i `output buffer`. Również zamienia `right.` [getloc()](#getloc) z `locale` obiektu.

## <a name="sync"></a>  basic_streambuf::Sync

Chronione funkcja wirtualna, która podejmuje próbę synchronizował kontrolowanego strumienie skojarzone strumieni zewnętrznych.

```cpp
virtual int sync();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie powiedzie się, zwraca -1. Domyślnym zachowaniem jest, aby zwrócić zero.

### <a name="remarks"></a>Uwagi

`sync` obejmuje wypisywanie wszelkie elementy między początkowy i dalej wskaźniki dla buforu danych wyjściowych. Nie wymaga umieszczanie ponownie wszystkie elementy od następnego i kończyć się wskaźniki buforu wejściowego.

## <a name="traits_type"></a>  basic_streambuf::traits_type

Kojarzy nazwę typu z **Tr** parametru szablonu.

```cpp
typedef Tr traits_type;
```

## <a name="uflow"></a>  basic_streambuf::uflow

Chronione funkcja wirtualna, która wyodrębnia bieżącego elementu ze strumienia wejściowego.

```cpp
virtual int_type uflow();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący element.

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego próbuje wyodrębnić bieżącego elementu **ch** ze strumienia wejściowego, a następnie przejdź bieżącej pozycji strumienia i zwracać element jako **traits_type::** [ to_int_type —](../standard-library/char-traits-struct.md#to_int_type)( **ch**). Jego można to zrobić na różne sposoby:

- Jeśli pozycji odczytu jest dostępny, zajmuje **ch** elementu przechowywanego w pozycji odczytu i przesuwa wskaźnik następnej dla buforu danych wejściowych.

- Może odczytywać element bezpośrednio z zewnętrznego źródła i dostarczenia go jako wartość **ch**.

- Dla buforu strumienia z typowymi danymi wejściowymi i strumienie wyjściowe ją udostępnić pozycję odczytu, zapisywania na poziomie, aby niektóre zewnętrznego miejsca docelowego, niektóre lub wszystkie elementy od początku i dalej wskaźniki dla buforu danych wyjściowych. Lub jego można przydzielić nowej lub dodatkowej pamięci masowej dla buforu danych wejściowych. Funkcja następnie odczytuje, z zewnętrznego źródła, co najmniej jeden element.

Jeśli funkcja nie powiedzie się, zwraca **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), ani nie zgłasza wyjątku. W przeciwnym razie funkcja zwraca bieżący element `ch` w strumieniu wejściowym konwertowane zgodnie z powyższym opisem i przesuwa wskaźnik następnej dla buforu danych wejściowych. Domyślne zachowanie to wywołanie [niedopełnienie](#underflow) i, jeśli ta funkcja zwraca **traits_type::eof**, aby zwrócić **traits_type::eof**. W przeciwnym razie funkcja zwraca bieżący element **ch** w strumieniu wejściowym przekonwertowany, jak opisano wcześniej, a następnie przesuwa wskaźnik następnej dla buforu danych wejściowych.

## <a name="underflow"></a>  basic_streambuf::underflow

Chroniona funkcja wirtualna, aby wyodrębnić bieżącego elementu ze strumienia wejściowego.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Wartość zwracana

Bieżący element.

### <a name="remarks"></a>Uwagi

Chronione wirtualna funkcja składowa usiłują wyodrębnić bieżącego elementu **ch** ze strumienia wejściowego, bez przesuwania bieżącego przesyłanie strumieniowe pozycji i zwraca je jako `traits_type::` [to_int_type](../standard-library/char-traits-struct.md#to_int_type)() **ch**). Jego można to zrobić na różne sposoby:

- Jeśli pozycji odczytu jest dostępna, **ch** elementu przechowywanego w pozycji odczytu. Aby uzyskać więcej informacji na temat tego, zobacz sekcję Uwagi [basic_streambuf — klasa](../standard-library/basic-streambuf-class.md).

- Go można udostępnić pozycję odczytu, przydzielając nowej lub dodatkowej pamięci masowej dla buforu danych wejściowych, czytając, z zewnętrznego źródła, co najmniej jeden element. Aby uzyskać więcej informacji na temat tego, zobacz sekcję Uwagi [basic_streambuf — klasa](../standard-library/basic-streambuf-class.md).

Jeśli funkcja nie powiedzie się, zwraca `traits_type::` [eof](../standard-library/char-traits-struct.md#eof) `()` ani nie zgłasza wyjątku. W przeciwnym razie zwraca bieżącego elementu w strumieniu wejściowym przekonwertować jak opisano wcześniej. Zachowanie domyślne ma zwracać `traits_type::eof()`.

Wirtualny `underflow` funkcji, za pomocą [synchronizacji](#sync) i [przepełnienie](#overflow) funkcje, określa właściwości `streambuf`-klasy pochodnej. Każda klasa pochodna może zaimplementować `underflow` inaczej, ale interfejs z wywołującym klasa strumienia jest taka sama.

`underflow` Funkcja najczęściej jest wywoływana przez publiczną `streambuf` funkcje, takie jak [sgetc —](#sgetc) i [sgetn —](#sgetn) po obszarze get jest pusta, ale można wywoływać innych klas, w tym klasy strumieni `underflow` porze.

`underflow` Funkcja dostarcza obszar get znakami ze źródła danych wejściowych. Jeśli obszar get zawiera znaki, `underflow` zwraca pierwszy znak. Jeśli obszar get jest pusta, wypełnia obszar get i zwraca następny znak (która pozostawia w obszarze Pobierz). Jeśli brak dostępnych żadnych więcej znaków, następnie `underflow` zwraca `EOF` i pozostawienie pustego obszaru get.

W `strstreambuf` klasy `underflow` dostosowuje [egptr —](#egptr) wskaźnik uzyskać dostęp do magazynu przydzielany dynamicznie przez wywołanie `overflow`.

## <a name="xsgetn"></a>  basic_streambuf::xsgetn

Chroniona funkcja wirtualna, aby wyodrębnić elementy ze strumienia wejściowego.

Ta metoda jest potencjalnie niebezpieczne, ponieważ opiera się na obiekt wywołujący, aby sprawdzić, czy przekazanych wartości są poprawne.

```cpp
virtual streamsize xsgetn(
    char_type* ptr,
    streamsize count);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Bufor do przechowywania wyodrębnione znaki.

*Liczba*<br/>
Liczba elementów do wyodrębnienia.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów wyodrębnione.

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego wyodrębnia maksymalnie *liczba* elementy ze strumienia wejściowego, tak jak za wielokrotnego wywołania [sbumpc —](#sbumpc)i przechowuje je w tablicy, rozpoczynający się od *ptr*. Zwraca liczbę elementów, które rzeczywiście zostały wyodrębnione.

## <a name="xsputn"></a>  basic_streambuf::xsputn

Chroniona funkcja wirtualna do wstawienia elementów do strumienia wyjściowego.

```cpp
virtual streamsize xsputn(const char_type* ptr, streamsize count);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Wskaźnik elementów do wstawienia.

*Liczba*<br/>
Liczba elementów do wstawienia.

### <a name="return-value"></a>Wartość zwracana

Liczba elementów, które faktycznie włożenia do strumienia.

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego wstawia do *liczba* elementy do dane wyjściowe strumienia, tak, jakby przez wielokrotnego wywołania [sputc —](#sputc), od początku tablicy w *ptr*. Wstawianie znaków do strumienia wyjściowego po zatrzymuje wszystkie *liczba* znaków być napisane tak, czy wywołanie `sputc( count)` zwróci `traits::eof()`. Zwraca liczbę elementów, które faktycznie wstawione.

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
