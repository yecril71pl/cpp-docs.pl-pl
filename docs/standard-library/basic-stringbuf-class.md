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
ms.openlocfilehash: 0445c2f8868fc9f2863ad4a2a12cc00261546c75
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68447841"
---
# <a name="basicstringbuf-class"></a>basic_stringbuf — Klasa

Opisuje bufor strumienia, który kontroluje przekazywanie elementów typu `Elem`, których cechy znaków są określane przez klasę `Tr`, do i z sekwencji elementów przechowywanych w obiekcie array.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>,
    class Alloc = allocator<Elem>>
class basic_stringbuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Alokacj*\
Klasa alokatora.

*Elem*\
Typ podstawowego elementu ciągu.

*Zdawczy*\
Cechy znaków wyspecjalizowane dla elementu Basic ciągu.

## <a name="remarks"></a>Uwagi

Obiekt jest przypisywany, rozszerzany i zwalniany w miarę potrzeb w celu uwzględnienia zmian w sekwencji.

Obiekt klasy `Elem`basic_stringbuf <, `Alloc` `ios_base::` [](../standard-library/ios-base-class.md#openmode) `stringbuf` , > przechowuje kopię argumentu OpenMode z jego konstruktora jako tryb trybów: `Tr`

- Jeśli `mode & ios_base::in` jest różna od zera, bufor wejściowy jest dostępny. Aby uzyskać więcej informacji, zobacz [Klasa basic_streambuf](../standard-library/basic-streambuf-class.md).

- Jeśli `mode & ios_base::out` jest różna od zera, bufor wyjściowy jest dostępny.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_stringbuf](#basic_stringbuf)|Konstruuje obiekt typu `basic_stringbuf`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ jest synonimem dla *alokacji*parametru szablonu.|
|[char_type](#char_type)|Kojarzy nazwę typu z parametrem szablonu *elem* .|
|[int_type](#int_type)|Sprawia, że ten `basic_filebuf`typ w zakresie jest odpowiednikiem typu o tej samej nazwie w zakresie *TR* .|
|[off_type](#off_type)|Sprawia, że ten `basic_filebuf`typ w zakresie jest odpowiednikiem typu o tej samej nazwie w zakresie *TR* .|
|[pos_type](#pos_type)|Sprawia, że ten `basic_filebuf`typ w zakresie jest odpowiednikiem typu o tej samej nazwie w zakresie *TR* .|
|[traits_type](#traits_type)|Kojarzy nazwę typu z parametrem szablonu *TR* .|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[overflow](#overflow)|Chroniona funkcja wirtualna, która może być wywoływana, gdy nowy znak zostanie wstawiony do pełnego buforu.|
|[pbackfail](#pbackfail)|Chroniona funkcja wirtualna elementu członkowskiego próbuje umieścić element w buforze wejściowym, a następnie staje się bieżącym elementem (wskazywanym przez następny wskaźnik).|
|[seekoff](#seekoff)|Chroniona funkcja wirtualna elementu członkowskiego próbuje zmienić bieżące położenie dla kontrolowanych strumieni.|
|[seekpos](#seekpos)|Chroniona funkcja wirtualna elementu członkowskiego próbuje zmienić bieżące położenie dla kontrolowanych strumieni.|
|[str](#str)|Ustawia lub pobiera tekst w buforze ciągów bez zmiany pozycji zapisu.|
|swap||
|[underflow](#underflow)|Chroniona funkcja wirtualna elementu członkowskiego do wyodrębnienia bieżącego elementu ze strumienia wejściowego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strumienia >

**Przestrzeń nazw:** std

## <a name="allocator_type"></a>basic_stringbuf::allocator_type

Typ jest synonimem dla *alokacji*parametru szablonu.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringbuf"></a>basic_stringbuf::basic_stringbuf

Konstruuje obiekt typu `basic_stringbuf`.

```cpp
basic_stringbuf(
    ios_base::openmode _Mode = ios_base::in | ios_base::out);

basic_stringbuf(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Mode*\
Jedno z wyliczeń w [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

*str*\
Obiekt typu [basic_string](../standard-library/basic-string-class.md).

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje wskaźnik o wartości null we wszystkich wskaźnikach kontrolujących bufor wejściowy i bufor wyjściowy. Aby uzyskać więcej informacji, zobacz sekcję Uwagi [klasy basic_streambuf](../standard-library/basic-streambuf-class.md). Przechowuje także *_Mode* jako tryb stringbuf —. Aby uzyskać więcej informacji, zobacz sekcję Uwagi [klasy basic_stringbuf](../standard-library/basic-stringbuf-class.md).

Drugi Konstruktor przydziela kopię sekwencji kontrolowanej przez obiekt String *str*. Jeśli `_Mode & ios_base::in` jest różna od zera, ustawia bufor wejściowy do rozpoczęcia odczytywania na początku sekwencji. Jeśli `_Mode & ios_base::out` jest różna od zera, ustawia bufor wyjściowy, aby rozpocząć pisanie na początku sekwencji. Przechowuje także *_Mode* jako tryb stringbuf —. Aby uzyskać więcej informacji, zobacz sekcję Uwagi [klasy basic_stringbuf](../standard-library/basic-stringbuf-class.md).

## <a name="char_type"></a>basic_stringbuf::char_type

Kojarzy nazwę typu z parametrem szablonu *elem* .

```cpp
typedef Elem char_type;
```

## <a name="int_type"></a>basic_stringbuf::int_type

Sprawia, że ten typ w zakresie basic_filebuf's jest odpowiednikiem typu o tej samej nazwie `Tr` w zakresie.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>basic_stringbuf::off_type

Sprawia, że ten typ w zakresie basic_filebuf's jest odpowiednikiem typu o tej samej nazwie `Tr` w zakresie.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="overflow"></a>basic_stringbuf:: overflow

Chroniona funkcja wirtualna, która może być wywoływana, gdy nowy znak zostanie wstawiony do pełnego buforu.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, który ma zostać wstawiony do buforu lub `traits_type::eof`.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść `traits_type::eof`, zwraca wartość. W przeciwnym razie zwraca **traits_type::** [Not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *meta*).

### <a name="remarks"></a>Uwagi

*Jeśli\_meta* nie porównano z **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof), chroniona wirtualna funkcja członkowska próbuje wstawić element **traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)( *\_meta*) do bufor wyjściowy. Można to zrobić na różne sposoby:

- Jeśli dostępna jest pozycja zapisu, może ona przechowywać element w pozycji zapisu i zwiększać następny wskaźnik dla buforu wyjściowego.

- Możliwe jest udostępnienie pozycji zapisu przez przydzielenie nowego lub dodatkowego magazynu dla buforu danych wyjściowych. Rozszerzanie buforu wyjściowego w ten sposób rozszerza również każdy skojarzony bufor wejściowy.

## <a name="pbackfail"></a>basic_stringbuf: niepowodzenie:p

Chroniona funkcja wirtualna elementu członkowskiego próbuje umieścić element w buforze wejściowym, a następnie uczynić go bieżącym elementem (wskazywanym przez następny wskaźnik).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*\
Znak, który ma zostać wstawiony do buforu lub `traits_type::eof`.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść `traits_type::eof`, zwraca wartość. W przeciwnym razie zwraca **traits_type::** [Not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *meta*).

### <a name="remarks"></a>Uwagi

Jeśli *_Meta* porównuje równe **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof), element, który ma zostać wypchnięcia, efektywnie jest już taki sam w strumieniu przed bieżącym elementem. W przeciwnym razie ten element jest zastępowany przez **bajt** = **traits_type::** [to_char_type](../standard-library/char-traits-struct.md#to_char_type)( *meta*). Funkcja może umieścić element na różne sposoby:

- Jeśli pozycja putback jest dostępna, a element przechowywany jest porównywany równo z bajtem, może zmniejszyć następny wskaźnik dla buforu wejściowego.

- Jeśli pozycja putback jest dostępna, a jeśli tryb stringbuf — zezwala na zmianę sekwencji ( **tryb & ios_base:: out** ma wartość różną od zera), może przechowywać bajt w pozycji putback i zmniejszać następny wskaźnik dla buforu wejściowego.

## <a name="pos_type"></a>basic_stringbuf::p os_type

Sprawia, że ten typ w zakresie basic_filebuf's jest odpowiednikiem typu o tej samej nazwie `Tr` w zakresie.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a>  basic_stringbuf::seekoff

Chroniona funkcja wirtualna elementu członkowskiego próbuje zmienić bieżące położenie dla kontrolowanych strumieni.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*\
Pozycja do wyszukiwania względem *_Way*. Aby uzyskać więcej informacji, zobacz [basic_stringbuf:: off_type](#off_type).

*_Way*\
Punkt początkowy dla operacji przesunięcia. Aby uzyskać możliwe wartości, zobacz [ios_base:: seekdir](../standard-library/ios-base-class.md#seekdir) .

*_Mode*\
Określa tryb dla pozycji wskaźnika. Wartość domyślna to umożliwienie modyfikacji pozycji odczytu i zapisu. Aby uzyskać więcej informacji, zobacz [ios_base:: openmode](../standard-library/ios-base-class.md#openmode).

### <a name="return-value"></a>Wartość zwracana

Zwraca nową pozycję lub nieprawidłową pozycję strumienia.

### <a name="remarks"></a>Uwagi

Dla obiektu klasy `basic_stringbuf<Elem, Tr, Alloc>`, pozycja strumienia składa się wyłącznie z przesunięcia strumienia. Przesunięcie zero oznacza pierwszy element kontrolowanej sekwencji.

Nowa pozycja jest określana w następujący sposób:

- Jeśli `_Way` Nowa == pozycjajest początkiem strumienia i *_Off.* `ios_base::beg`

- Jeśli `_Way` Nowa == pozycjajest bieżącym położeniem strumienia i _Off.  `ios_base::cur`

- Jeśli `_Way` Nowa == pozycjajest końcem strumienia i *_Off.* `ios_base::end`

Jeśli `_Mode & ios_base::in` jest różna od zera, funkcja zmienia następną pozycję do odczytu w buforze wejściowym. Jeśli `_Mode & ios_base::out` jest różna od zera, funkcja zmienia następną pozycję do zapisu w buforze wyjściowym. Aby strumień miał wartość, jego bufor musi istnieć. Aby operacja pozycjonowania zakończyła się pomyślnie, pochodząca pozycja w strumieniu musi znajdować się w kontrolowanej sekwencji. Jeśli funkcja ma wpływ na pozycje strumienia, *_Way* musi być `ios_base::beg` lub `ios_base::end` i oba strumienie są umieszczane w tym samym elemencie. W przeciwnym razie (lub jeśli nie ma takiego oddziaływania) operacja pozycjonowania zakończy się niepowodzeniem.

Jeśli funkcja się powiedzie w przypadku zmiany jednego lub obu pozycji strumienia, zwraca wynikową pozycję strumienia. W przeciwnym razie kończy się niepowodzeniem i zwraca nieprawidłową pozycję strumienia.

## <a name="seekpos"></a>basic_stringbuf:: seekpos

Chroniona funkcja wirtualna elementu członkowskiego próbuje zmienić bieżące położenie dla kontrolowanych strumieni.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*\
Pozycja do wyszukania.

*_Mode*\
Określa tryb dla pozycji wskaźnika. Wartość domyślna to umożliwienie modyfikacji pozycji odczytu i zapisu.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie w przypadku zmiany jednego lub obu pozycji strumienia, zwraca wynikową pozycję strumienia. W przeciwnym razie kończy się niepowodzeniem i zwraca nieprawidłową pozycję strumienia. Aby określić, czy pozycja strumienia jest nieprawidłowa, porównaj wartość zwracaną z `pos_type(off_type(-1))`.

### <a name="remarks"></a>Uwagi

Dla obiektu klasy basic_stringbuf < **elem**, `Alloc` **TR**>, pozycja strumienia składa się wyłącznie z przesunięcia strumienia. Przesunięcie zero oznacza pierwszy element kontrolowanej sekwencji. Nowa pozycja jest określana przez _ *SP*.

Jeśli **tryb & ios_base:: in** ma wartość różną od zera, funkcja zmienia następną pozycję do odczytu w buforze wejściowym. Jeśli **tryb & ios_base:: out** jest różna od zera, funkcja zmienia następną pozycję do zapisu w buforze wyjściowym. Aby strumień miał wartość, jego bufor musi istnieć. Aby operacja pozycjonowania zakończyła się pomyślnie, pochodząca pozycja w strumieniu musi znajdować się w kontrolowanej sekwencji. W przeciwnym razie (lub jeśli nie ma takiego oddziaływania) operacja pozycjonowania zakończy się niepowodzeniem.

## <a name="str"></a>basic_stringbuf:: str

Ustawia lub pobiera tekst w buforze ciągów bez zmiany pozycji zapisu.

```cpp
basic_string<Elem, Tr, Alloc> str() const;
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

*_Newstr*\
Nowy ciąg.

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt klasy [basic_string](../standard-library/basic-string-class.md) \< **elem**, **TR**, Alloc **>,** którego kontrolowana sekwencja jest kopią sekwencji kontrolowanej przez  **\*ten**element.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zwraca obiekt klasy basic_string `Alloc`< **elem**, **TR**>, którego kontrolowana sekwencja jest kopią sekwencji kontrolowanej przez  **\*ten**element. Kopiowana sekwencja zależy od zapisanego trybu stringbuf —:

- Jeśli **tryb & ios_base:: out** ma wartość różną od zera i istnieje bufor wyjściowy, sekwencja jest całym buforem wyjściowym ( [epptr](../standard-library/basic-streambuf-class.md#epptr) - [pbase](../standard-library/basic-streambuf-class.md#pbase) elementy, `pbase`Zaczynając od).

- Jeśli **tryb & ios_base:: in** ma wartość różną od zera i istnieje bufor wejściowy, sekwencja to cały bufor wejściowy ( [egptr](../standard-library/basic-streambuf-class.md#egptr) - elementy[eback](../standard-library/basic-streambuf-class.md#eback) rozpoczynające się `eback`od).

- W przeciwnym razie skopiowana sekwencja jest pusta.

Druga funkcja członkowska cofa alokację każdej sekwencji aktualnie kontrolowanej przez  **\*tę**funkcję. Następnie przydziela kopię sekwencji kontrolowanej przez *_Newstr*. Jeśli **tryb & ios_base:: in** ma wartość różną od zera, ustawia bufor wejściowy do rozpoczęcia odczytywania na początku sekwencji. Jeśli **tryb & ios_base:: out** ma wartość różną od zera, ustawia bufor wyjściowy na rozpoczęcie pisania na początku sekwencji.

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

## <a name="traits_type"></a>basic_stringbuf::traits_type

Kojarzy nazwę typu z parametrem szablonu *TR* .

```cpp
typedef Tr traits_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *TR*.

## <a name="underflow"></a>basic_stringbuf:: nadmiarowy

Chroniona funkcja wirtualna w celu wyodrębnienia bieżącego elementu ze strumienia wejściowego.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść, zwraca **traits_type::** [EOF](../standard-library/char-traits-struct.md#eof). W przeciwnym razie zwraca bieżący element w strumieniu wejściowym, który jest konwertowany.

### <a name="remarks"></a>Uwagi

Chroniona funkcja wirtualna elementu członkowskiego podejmuje próbę `byte` wyodrębnienia bieżącego elementu z bufora wejściowego, przechodzenie do aktualnej pozycji strumienia i zwrócenie elementu jako **traits_type::** [to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **Byte**). Można to zrobić w jeden sposób: Jeśli pozycja odczytu jest dostępna, przyjmuje `byte` się jako element zapisany w pozycji odczytu i przesuwa następny wskaźnik dla buforu wejściowego.

## <a name="swap"></a>basic_streambuf:: swap

Zamienia zawartość tego buforu ciągu z innym buforem ciągu.

```cpp
void basic_stringbuf<T>::swap(basic_stringbuf& other)
```

### <a name="parameters"></a>Parametry

*różnych*\
Basic_stringbuf, którego zawartość zostanie zamieniony na basic_stringbuf.

### <a name="remarks"></a>Uwagi

## <a name="op_eq"></a>basic_stringbuf:: operator =

Przypisuje zawartość basic_stringbuf po prawej stronie operatora do basic_stringbuf po lewej stronie.

```cpp
basic_stringbuf& basic_stringbuf:: operator=(const basic_stringbuf& other)
```

### <a name="parameters"></a>Parametry

*różnych*\
Basic_stringbuf, którego zawartość, w tym cechy ustawień regionalnych, zostanie przypisany do stringbuf — po lewej stronie operatora.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w C++ standardowej bibliotece](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
