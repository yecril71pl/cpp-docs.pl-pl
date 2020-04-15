---
title: basic_stringbuf — Klasa
ms.date: 11/04/2016
f1_keywords:
- sstream/std::basic_stringbuf
- sstream/std::basic_stringbuf::allocator_type
- sstream/std::basic_stringbuf::char_type
- sstream/std::basic_stringbuf::int_type
- sstream/std::basic_stringbuf::off_type
- sstream/std::basic_stringbuf::pos_type
- sstream/std::basic_stringbuf::traits_type
- sstream/std::basic_stringbuf::overflow
- sstream/std::basic_stringbuf::pbackfail
- sstream/std::basic_stringbuf::seekoff
- sstream/std::basic_stringbuf::seekpos
- sstream/std::basic_stringbuf::str
- sstream/std::basic_stringbuf::underflow
helpviewer_keywords:
- std::basic_stringbuf [C++]
- std::basic_stringbuf [C++], allocator_type
- std::basic_stringbuf [C++], char_type
- std::basic_stringbuf [C++], int_type
- std::basic_stringbuf [C++], off_type
- std::basic_stringbuf [C++], pos_type
- std::basic_stringbuf [C++], traits_type
- std::basic_stringbuf [C++], overflow
- std::basic_stringbuf [C++], pbackfail
- std::basic_stringbuf [C++], seekoff
- std::basic_stringbuf [C++], seekpos
- std::basic_stringbuf [C++], str
- std::basic_stringbuf [C++], underflow
ms.assetid: 40c85f9e-42a5-4a65-af5c-23c8e3bf8113
ms.openlocfilehash: 578d0e31e08f3e077a908c4344f77da5495df40d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364887"
---
# <a name="basic_stringbuf-class"></a>basic_stringbuf — Klasa

W tym artykule opisano bufor strumienia, który steruje transmisją elementów typu `Elem`, których cechy charakteru są określane przez klasę, `Tr`do i z sekwencji elementów przechowywanych w obiekcie tablicy.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>,
    class Alloc = allocator<Elem>>
class basic_stringbuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Alloc*\
Klasa alokatora.

*Elem*\
Typ elementu podstawowego ciągu.

*Tr*\
Cechy charakteru wyspecjalizowane na podstawowym elemencie ciągu.

## <a name="remarks"></a>Uwagi

Obiekt jest przydzielany, rozszerzany i zwalniany w razie potrzeby w celu uwzględnienia zmian w sekwencji.

Obiekt klasy basic_stringbuf< `Elem`, `Tr` `Alloc`> przechowuje kopię argumentu `ios_base::` [openmode](../standard-library/ios-base-class.md#openmode) z jego konstruktora `stringbuf` w **trybie:**

- Jeśli `mode & ios_base::in` jest niezerowy, bufor wejściowy jest dostępny. Aby uzyskać więcej informacji, zobacz [basic_streambuf Klasa](../standard-library/basic-streambuf-class.md).

- Jeśli `mode & ios_base::out` jest niezerowy, bufor wyjściowy jest dostępny.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Basic_stringbuf](#basic_stringbuf)|Konstruuje obiekt `basic_stringbuf`typu .|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ jest synonimem parametru szablonu *Alloc*.|
|[Char_type](#char_type)|Kojarzy nazwę typu z parametrem szablonu *Elem.*|
|[Int_type](#int_type)|Sprawia, że `basic_filebuf`ten typ w zakresie 's równoważne typ tej samej nazwy w zakresie *Tr.*|
|[off_type](#off_type)|Sprawia, że `basic_filebuf`ten typ w zakresie 's równoważne typ tej samej nazwy w zakresie *Tr.*|
|[pos_type](#pos_type)|Sprawia, że `basic_filebuf`ten typ w zakresie 's równoważne typ tej samej nazwy w zakresie *Tr.*|
|[traits_type](#traits_type)|Kojarzy nazwę typu z parametrem szablonu *Tr.*|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[Przepełnienie](#overflow)|Chroniona, wirtualna funkcja, która może być wywoływana po wstawieniu nowego znaku do pełnego buforu.|
|[pbackfail](#pbackfail)|Funkcja chronionego elementu członkowskiego wirtualnego próbuje umieścić z powrotem element do buforu wejściowego, a następnie sprawia, że bieżący element (wskazywał na następny wskaźnik).|
|[poszukiwanie](#seekoff)|Funkcja chronionego wirtualnego elementu członkowskiego próbuje zmienić bieżące pozycje dla kontrolowanych strumieni.|
|[seekpos](#seekpos)|Funkcja chronionego wirtualnego elementu członkowskiego próbuje zmienić bieżące pozycje dla kontrolowanych strumieni.|
|[Str](#str)|Ustawia lub pobiera tekst w buforze ciągu bez zmiany pozycji zapisu.|
|swap||
|[Niedomiar](#underflow)|Funkcja chronionego elementu członkowskiego wirtualnego, aby wyodrębnić bieżący element ze strumienia wejściowego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<sstream>

**Przestrzeń nazw:** std

## <a name="basic_stringbufallocator_type"></a><a name="allocator_type"></a>basic_stringbuf::allocator_type

Typ jest synonimem parametru szablonu *Alloc*.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringbufbasic_stringbuf"></a><a name="basic_stringbuf"></a>basic_stringbuf::basic_stringbuf

Konstruuje obiekt `basic_stringbuf`typu .

```cpp
basic_stringbuf(
    ios_base::openmode _Mode = ios_base::in | ios_base::out);

basic_stringbuf(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_mode*\
Jedno z wyliczenia w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*Str*\
Obiekt typu [basic_string](../standard-library/basic-string-class.md).

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor przechowuje wskaźnik null we wszystkich wskaźników sterujących buforu wejściowego i buforu wyjściowego. Aby uzyskać więcej informacji, zobacz sekcję Uwagi [klasy basic_streambuf](../standard-library/basic-streambuf-class.md). Przechowuje również *_Mode* jako tryb stringbuf. Aby uzyskać więcej informacji, zobacz sekcję Uwagi [klasy basic_stringbuf](../standard-library/basic-stringbuf-class.md).

Drugi konstruktor przydziela kopię sekwencji kontrolowanej przez obiekt ciągu *str*. Jeśli `_Mode & ios_base::in` jest niezerowy, ustawia bufor wejściowy, aby rozpocząć odczyt na początku sekwencji. Jeśli `_Mode & ios_base::out` jest niezerowy, ustawia bufor wyjściowy, aby rozpocząć pisanie na początku sekwencji. Przechowuje również *_Mode* jako tryb stringbuf. Aby uzyskać więcej informacji, zobacz sekcję Uwagi [klasy basic_stringbuf](../standard-library/basic-stringbuf-class.md).

## <a name="basic_stringbufchar_type"></a><a name="char_type"></a>basic_stringbuf::char_type

Kojarzy nazwę typu z parametrem szablonu *Elem.*

```cpp
typedef Elem char_type;
```

## <a name="basic_stringbufint_type"></a><a name="int_type"></a>basic_stringbuf::int_type

Sprawia, że ten typ w zakresie basic_filebuf jest równoważny `Tr` typ tej samej nazwy w zakresie.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="basic_stringbufoff_type"></a><a name="off_type"></a>basic_stringbuf::off_type

Sprawia, że ten typ w zakresie basic_filebuf jest równoważny `Tr` typ tej samej nazwy w zakresie.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="basic_stringbufoverflow"></a><a name="overflow"></a>basic_stringbuf::przepełnienie

Chroniona funkcja wirtualna, która może być wywoływana po wstawieniu nowego znaku do pełnego buforu.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, który ma być `traits_type::eof`wstawiany do buforu lub .

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może `traits_type::eof`zakończyć się pomyślnie, zwraca . W przeciwnym razie zwraca **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Uwagi

Jeśli * \_Meta* nie porównuje **równa traits_type::**[eof](../standard-library/char-traits-struct.md#eof), funkcja chronionego elementu członkowskiego wirtualnego próbuje wstawić element **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_Meta*) do buforu wyjściowego. Może to zrobić na różne sposoby:

- Jeśli pozycja zapisu jest dostępna, może przechowywać element w pozycji zapisu i zwiększać następny wskaźnik dla buforu wyjściowego.

- Może udostępnić pozycję zapisu, przydzielając nowe lub dodatkowe miejsce do magazynowania buforu wyjściowego. Rozszerzenie buforu wyjściowego w ten sposób rozszerza również wszelkie skojarzone buforu wejściowego.

## <a name="basic_stringbufpbackfail"></a><a name="pbackfail"></a>basic_stringbuf::pbackfail

Funkcja chronionego elementu członkowskiego wirtualnego próbuje umieścić z powrotem element do buforu wejściowego, a następnie uczynić go bieżącym elementem (wskazywał na następny wskaźnik).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, który ma być `traits_type::eof`wstawiany do buforu lub .

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może `traits_type::eof`zakończyć się pomyślnie, zwraca . W przeciwnym razie zwraca **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Uwagi

Jeśli *_Meta* porównuje **równe traits_type::**[eof](../standard-library/char-traits-struct.md#eof), element do odepchnięcia jest skutecznie ten, który jest już w strumieniu przed bieżącym elementem. W przeciwnym razie element ten jest zastępowany przez traits_type = **bajtów::** **byte**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(_ *Meta*). Funkcja może umieścić z powrotem element na różne sposoby:

- Jeśli pozycja putback jest dostępna, a element przechowywany tam porównuje równe bajtowi, może zniegować następny wskaźnik dla buforu wejściowego.

- Jeśli pozycja odłożenia jest dostępna i jeśli tryb stringbuf pozwala na zmianę sekwencji **(tryb & ios_base::out** jest niezerowy), może przechowywać bajt w pozycji odłożenia i zmniejszać następny wskaźnik dla buforu wejściowego.

## <a name="basic_stringbufpos_type"></a><a name="pos_type"></a>basic_stringbuf::p_type

Sprawia, że ten typ w zakresie basic_filebuf jest równoważny `Tr` typ tej samej nazwy w zakresie.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="basic_stringbufseekoff"></a><a name="seekoff"></a>basic_stringbuf::seekoff

Funkcja chronionego wirtualnego elementu członkowskiego próbuje zmienić bieżące pozycje dla kontrolowanych strumieni.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_off*\
Stanowisko do poszukiwania w stosunku do *_Way*. Aby uzyskać więcej informacji, zobacz [basic_stringbuf::off_type](#off_type).

*_way*\
Punktem wyjścia dla operacji odsunięcia. Zobacz [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) dla możliwych wartości.

*_mode*\
Określa tryb położenia wskaźnika. Domyślnie można zmodyfikować pozycje odczytu i zapisu. Aby uzyskać więcej informacji, zobacz [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

### <a name="return-value"></a>Wartość zwracana

Zwraca nową pozycję lub nieprawidłową pozycję strumienia.

### <a name="remarks"></a>Uwagi

Dla obiektu klasy `basic_stringbuf<Elem, Tr, Alloc>`pozycja strumienia składa się wyłącznie z odsunięcia strumienia. Offset zero wyznacza pierwszy element kontrolowanej sekwencji.

Nowe stanowisko określa się w następujący sposób:

- `_Way`  == Jeśli `ios_base::beg`nowa pozycja jest początkiem strumienia plus *_Off*.

- `_Way`  == Jeśli `ios_base::cur`nowa pozycja to bieżąca pozycja strumienia plus *_Off*.

- `_Way`  == Jeśli `ios_base::end`nowa pozycja to koniec strumienia plus *_Off*.

Jeśli `_Mode & ios_base::in` jest niezerowy, funkcja zmienia następną pozycję do odczytu w buforze wejściowym. Jeśli `_Mode & ios_base::out` jest niezerowy, funkcja zmienia następną pozycję do zapisu w buforze wyjściowym. Aby mieć wpływ na strumień, musi istnieć jego bufor. Aby operacja pozycjonowania powiodła się, wynikowa pozycja strumienia musi znajdować się w kontrolowanej sekwencji. Jeśli funkcja wpływa na obie *_Way* pozycje strumienia, `ios_base::beg` _Way `ios_base::end` musi być lub oba strumienie są umieszczone w tym samym elemencie. W przeciwnym razie (lub jeśli nie ma to wpływu na żadną pozycję), operacja pozycjonowania kończy się niepowodzeniem.

Jeśli funkcja powiedzie się w zmianie jednej lub obu pozycji strumienia, zwraca wynikową pozycję strumienia. W przeciwnym razie kończy się niepowodzeniem i zwraca nieprawidłową pozycję strumienia.

## <a name="basic_stringbufseekpos"></a><a name="seekpos"></a>basic_stringbuf::seekpos

Funkcja chronionego wirtualnego elementu członkowskiego próbuje zmienić bieżące pozycje dla kontrolowanych strumieni.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Stanowisko do poszukiwania.

*_mode*\
Określa tryb położenia wskaźnika. Domyślnie można zmodyfikować pozycje odczytu i zapisu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja powiedzie się w zmianie jednej lub obu pozycji strumienia, zwraca wynikową pozycję strumienia. W przeciwnym razie kończy się niepowodzeniem i zwraca nieprawidłową pozycję strumienia. Aby ustalić, czy pozycja strumienia jest `pos_type(off_type(-1))`nieprawidłowa, porównaj wartość zwracaną z programem .

### <a name="remarks"></a>Uwagi

Dla obiektu klasy basic_stringbuf< **Elem**, **Tr** `Alloc` ,>, pozycja strumienia składa się wyłącznie z przesunięcia strumienia. Offset zero wyznacza pierwszy element kontrolowanej sekwencji. Nową pozycję określa _ *Sp*.

Jeśli **tryb & ios_base::in** jest niezerowy, funkcja zmienia następną pozycję do odczytu w buforze wejściowym. Jeśli **tryb & ios_base::out** jest niezerowy, funkcja zmienia następną pozycję do zapisu w buforze wyjściowym. Aby mieć wpływ na strumień, musi istnieć jego bufor. Aby operacja pozycjonowania powiodła się, wynikowa pozycja strumienia musi znajdować się w kontrolowanej sekwencji. W przeciwnym razie (lub jeśli nie ma to wpływu na żadną pozycję), operacja pozycjonowania kończy się niepowodzeniem.

## <a name="basic_stringbufstr"></a><a name="str"></a>basic_stringbuf::str

Ustawia lub pobiera tekst w buforze ciągu bez zmiany pozycji zapisu.

```cpp
basic_string<Elem, Tr, Alloc> str() const;
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

*_Newstr*\
Nowy ciąg.

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt klasy [basic_string](../standard-library/basic-string-class.md) \< **Elem**, **Tr**, Alloc **>,** którego kontrolowana sekwencja jest kopią sekwencji kontrolowanej przez ** \*ten**.

### <a name="remarks"></a>Uwagi

Funkcja pierwszego elementu członkowskiego zwraca obiekt klasy basic_string< **Elem**, `Alloc` **Tr**,>, którego kontrolowana sekwencja jest kopią sekwencji kontrolowanej przez ** \*ten**plik . Sekwens skopiowany zależy od trybu przechowywanego stringbuf:

- Jeśli **tryb & ios_base::out** jest niezerowy i istnieje bufor wyjściowy, sekwencja jest całym buforem wyjściowym `pbase`( elementy bazy - [epptr,](../standard-library/basic-streambuf-class.md#pbase) począwszy od ). [epptr](../standard-library/basic-streambuf-class.md#epptr)

- Jeśli **tryb & ios_base::in** jest niezerowy i istnieje bufor wejściowy, sekwencja jest całym buforem wejściowym `eback`( [egptr](../standard-library/basic-streambuf-class.md#egptr) - [elementów eback,](../standard-library/basic-streambuf-class.md#eback) począwszy od ).

- W przeciwnym razie skopiowana sekwencja jest pusta.

Druga funkcja elementu członkowskiego przydzieli dowolną sekwencję aktualnie ** \*kontrolowaną**przez tę funkcję . Następnie przydziela kopię sekwencji kontrolowanej przez *_Newstr*. Jeśli **tryb & ios_base::in** jest niezerowy, ustawia bufor wejściowy, aby rozpocząć odczyt na początku sekwencji. Jeśli **tryb & ios_base::out** jest niezerowy, ustawia bufor wyjściowy, aby rozpocząć pisanie na początku sekwencji.

### <a name="example"></a>Przykład

```cpp
// basic_stringbuf_str.cpp
// compile with: /EHsc
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   basic_string<char> i( "test" );
   stringstream ss;

   ss.rdbuf( )->str( i );
   cout << ss.str( ) << endl;

   ss << "z";
   cout << ss.str( ) << endl;

   ss.rdbuf( )->str( "be" );
   cout << ss.str( ) << endl;
}
```

```Output
test
zest
be
```

## <a name="basic_stringbuftraits_type"></a><a name="traits_type"></a>basic_stringbuf::traits_type

Kojarzy nazwę typu z parametrem szablonu *Tr.*

```cpp
typedef Tr traits_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu *Tr*.

## <a name="basic_stringbufunderflow"></a><a name="underflow"></a>basic_stringbuf::niedopełnienie

Chroniona, wirtualna funkcja wyodrębniania bieżącego elementu ze strumienia wejściowego.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może zakończyć się pomyślnie, zwraca **traits_type::**[eof](../standard-library/char-traits-struct.md#eof). W przeciwnym razie zwraca bieżący element w strumieniu wejściowym, które są konwertowane.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualnego elementu członkowskiego `byte` próbuje wyodrębnić bieżący element z buforu wejściowego, przyspieszyć bieżącą pozycję strumienia i zwrócić element jako **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **bajt**). Można to zrobić w jeden sposób: Jeśli pozycja `byte` odczytu jest dostępna, trwa jako element przechowywany w pozycji odczytu i przesuwa następny wskaźnik dla buforu wejściowego.

## <a name="basic_streambufswap"></a><a name="swap"></a>basic_streambuf::swap

Zamienia zawartość tego buforu ciągów z innym buforem ciągu.

```cpp
void basic_stringbuf<T>::swap(basic_stringbuf& other)
```

### <a name="parameters"></a>Parametry

*Innych*\
basic_stringbuf którego zawartość zostanie zamieniona z tym basic_stringbuf.

### <a name="remarks"></a>Uwagi

## <a name="basic_stringbufoperator"></a><a name="op_eq"></a>basic_stringbuf::operator=

Przypisuje zawartość basic_stringbuf po prawej stronie operatora do basic_stringbuf po lewej stronie.

```cpp
basic_stringbuf& basic_stringbuf:: operator=(const basic_stringbuf& other)
```

### <a name="parameters"></a>Parametry

*Innych*\
Basic_stringbuf którego zawartość, w tym cechy ustawień regionalnych, zostanie przypisany do stringbuf po lewej stronie operatora.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
