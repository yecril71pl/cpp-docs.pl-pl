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
ms.openlocfilehash: 1ed9deee46f7c99750ee3260a6b2a8de1f0f3397
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409762"
---
# <a name="basicstringbuf-class"></a>basic_stringbuf — Klasa

W tym artykule opisano buforu strumieni, który kontroluje transmisji elementów typu `Elem`, którego cech są określane przez klasę `Tr`, do i z sekwencji elementów przechowywanych w tablicy obiektów.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>,
    class Alloc = allocator<Elem>>
class basic_stringbuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Parametry

*Alokacji*<br/>
Klasa alokatora.

*Elem*<br/>
Typ elementu podstawowego ciągu.

*TR*<br/>
Cechy znaków przeznaczone specjalnie dla elementu podstawowego ciągu.

## <a name="remarks"></a>Uwagi

Obiekt jest przydzielany, rozszerzony i zwolniona zgodnie z potrzebami, aby uwzględnić zmiany w sekwencji.

Obiekt basic_stringbuf — Klasa < `Elem`, `Tr`, `Alloc`> przechowuje kopię `ios_base::` [openmode](../standard-library/ios-base-class.md#openmode) argumentu z konstruktora jako jego `stringbuf` tryb **tryb** :

- Jeśli `mode & ios_base::in` jest różna od zera, buforze wejściowym, który jest dostępny. Aby uzyskać więcej informacji, zobacz [basic_streambuf — klasa](../standard-library/basic-streambuf-class.md).

- Jeśli `mode & ios_base::out` jest różna od zera, bufor wyjściowy jest dostępny.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_stringbuf](#basic_stringbuf)|Tworzy obiekt typu `basic_stringbuf`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ jest synonimem dla parametru szablonu *alokacji*.|
|[char_type](#char_type)|Kojarzy nazwę typu z *Elem* parametru szablonu.|
|[int_type](#int_type)|Sprawia, że tego typu w ramach `basic_filebuf`firmy odpowiednikiem typu o takiej samej nazwie w zakresie *Tr* zakresu.|
|[off_type](#off_type)|Sprawia, że tego typu w ramach `basic_filebuf`firmy odpowiednikiem typu o takiej samej nazwie w zakresie *Tr* zakresu.|
|[pos_type](#pos_type)|Sprawia, że tego typu w ramach `basic_filebuf`firmy odpowiednikiem typu o takiej samej nazwie w zakresie *Tr* zakresu.|
|[traits_type](#traits_type)|Kojarzy nazwę typu z *Tr* parametru szablonu.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[overflow](#overflow)|Funkcja chronionych, wirtualnej, która może być wywoływana po wstawieniu do buforu pełnej znak nowego.|
|[pbackfail](#pbackfail)|Chroniony element członkowski wirtualnego funkcja próbuje odłożyć elementu w buforze wejściowym, następnie sprawia, że bieżący element (wskazywany przez wskaźnik następnej).|
|[seekoff](#seekoff)|Chronione wirtualna funkcja składowa próbuje alter dla strumieni kontrolowanego bieżącej pozycji.|
|[seekpos —](#seekpos)|Chronione wirtualna funkcja składowa próbuje alter dla strumieni kontrolowanego bieżącej pozycji.|
|[str](#str)|Ustawia lub pobiera tekst w buforze ciąg bez zmiany pozycji zapisu.|
|swap||
|[underflow](#underflow)|Funkcja chroniony element członkowski wirtualnego można wyodrębnić bieżącego elementu ze strumienia wejściowego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<strumienia >

**Namespace:** standardowe

## <a name="allocator_type"></a>  basic_stringbuf::allocator_type

Typ jest synonimem dla parametru szablonu *alokacji*.

```cpp
typedef Alloc allocator_type;
```

## <a name="basic_stringbuf"></a>  basic_stringbuf::basic_stringbuf

Tworzy obiekt typu `basic_stringbuf`.

```cpp
basic_stringbuf(
    ios_base::openmode _Mode = ios_base::in | ios_base::out);

basic_stringbuf(
    const basic_string<Elem, Tr, Alloc>& str,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Tryb*<br/>
Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

*str*<br/>
Obiekt typu [basic_string](../standard-library/basic-string-class.md).

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje wskaźnik zerowy wszystkie wskaźniki kontrolowanie buforu wejściowego i bufor wyjściowy. Aby uzyskać więcej informacji, zobacz sekcję Uwagi [basic_streambuf — klasa](../standard-library/basic-streambuf-class.md). Przechowuje także *_tryb* jako tryb stringbuf. Aby uzyskać więcej informacji, zobacz sekcję Uwagi [basic_stringbuf — klasa](../standard-library/basic-stringbuf-class.md).

Drugi Konstruktor przydziela kopię sekwencji kontrolowanej przez obiekt string *str*. Jeśli `_Mode & ios_base::in` jest różna od zera, ustawia buforu wejściowego, należy rozpocząć odczyt na początku sekwencji. Jeśli `_Mode & ios_base::out` jest różna od zera, ustawia bufor wyjściowy ma rozpocząć się zapis na początku sekwencji. Przechowuje także *_tryb* jako tryb stringbuf. Aby uzyskać więcej informacji, zobacz sekcję Uwagi [basic_stringbuf — klasa](../standard-library/basic-stringbuf-class.md).

## <a name="char_type"></a>  basic_stringbuf::char_type

Kojarzy nazwę typu z *Elem* parametru szablonu.

```cpp
typedef Elem char_type;
```

## <a name="int_type"></a>  basic_stringbuf::int_type

Sprawia, że tego typu w zakresie firmy basic_filebuf — odpowiednikiem typu o takiej samej nazwie w `Tr` zakresu.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>  basic_stringbuf::off_type

Sprawia, że tego typu w zakresie firmy basic_filebuf — odpowiednikiem typu o takiej samej nazwie w `Tr` zakresu.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="overflow"></a>  basic_stringbuf::Overflow

Chronione funkcja wirtualna, która może być wywoływana po wstawieniu do buforu pełnej nowego znaku.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*<br/>
Znak do wstawienia do określonego bufora lub `traits_type::eof`.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie powiedzie się, zwraca `traits_type::eof`. W przeciwnym razie zwraca **traits_type::**[not_eof —](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Uwagi

Jeśli  *\_Meta* porównuje równa **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), chronionych wirtualna funkcja składowa próbuje Wstaw element  **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(*\_Meta*) do buforu danych wyjściowych. Jego można to zrobić na różne sposoby:

- W przypadku pozycji zapisu jest dostępny, można przechowywać element w określonej pozycji zapisu i zwiększyć wskaźnik następnej dla buforu danych wyjściowych.

- Go można udostępnić pozycji zapisu, przydzielając nowej lub dodatkowej pamięci masowej dla buforu danych wyjściowych. Rozszerzanie bufora wyjściowego w ten sposób rozszerzają wszelkie skojarzone buforu wejściowego.

## <a name="pbackfail"></a>  basic_stringbuf::pbackfail

Funkcja chroniony element członkowski wirtualnego próbuje odłożyć element do buforu wejściowego, a następnie bieżącego elementu (wskazywany przez wskaźnik następnej).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

*_Meta*<br/>
Znak do wstawienia do określonego bufora lub `traits_type::eof`.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie powiedzie się, zwraca `traits_type::eof`. W przeciwnym razie zwraca **traits_type::**[not_eof —](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Uwagi

Jeśli *_Meta* porównuje równa **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), element do usunięcia jest skutecznie już w strumieniu przed bieżącego elementu. W przeciwnym razie ten element został zastąpiony **bajtów** = **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(_ *Meta*). Funkcję można odłożyć element na różne sposoby:

- Jeśli pozycja putback — jest dostępna, a element tam przechowywane w porównaniu równa bajtów, jego dekrementacja wskaźnik następnej dla buforu danych wejściowych.

- Pozycja putback — jest dostępna, a tryb stringbuf pozwala sekwencji, który ma zostać zmodyfikowana ( **trybu & ios_base::out** jest różna od zera), można przechowywać bajt na pozycji putback — i dekrementacji wskaźnik następnej dla buforu danych wejściowych.

## <a name="pos_type"></a>  basic_stringbuf::pos_type

Sprawia, że tego typu w zakresie firmy basic_filebuf — odpowiednikiem typu o takiej samej nazwie w `Tr` zakresu.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a>  basic_stringbuf::seekoff

Chronione wirtualna funkcja składowa próbuje alter dla strumieni kontrolowanego bieżącej pozycji.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Położenie do wyszukania dla względem *_Way*. Aby uzyskać więcej informacji, zobacz [basic_stringbuf::off_type](#off_type).

*_Way*<br/>
Punkt początkowy dla operacji przesunięcia. Zobacz [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) uzyskać odpowiednie wartości.

*_Tryb*<br/>
Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji. Aby uzyskać więcej informacji, zobacz [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

### <a name="return-value"></a>Wartość zwracana

Zwraca nową pozycję lub nieprawidłowy strumień pozycji.

### <a name="remarks"></a>Uwagi

Aby uzyskać obiekt klasy `basic_stringbuf<Elem, Tr, Alloc>`, pozycji strumienia, który składa się wyłącznie z przesunięciu strumienia. Przesunięcia zero wskazuje pierwszego elementu w kontrolowanej sekwencji.

Nowa pozycja jest określany w następujący sposób:

- Jeśli `_Way`  ==  `ios_base::beg`, nowe położenie jest na początku strumienia plus *_Off*.

- Jeśli `_Way`  ==  `ios_base::cur`, nowe położenie jest bieżącą pozycję w strumieniu oraz *_Off*.

- Jeśli `_Way`  ==  `ios_base::end`, nowe położenie jest koniec strumienia plus *_Off*.

Jeśli `_Mode & ios_base::in` jest różna od zera, funkcja zmienia następnej pozycji, aby odczytać w buforze wejściowym. Jeśli `_Mode & ios_base::out` jest różna od zera, funkcja zmienia następnej pozycji, aby zapisać w buforze danych wyjściowych. Strumień, których to dotyczy musi istnieć buforu. Pozycjonowania operacja została wykonana pomyślnie wynikowy pozycji strumienia musi znajdować się w kontrolowanej sekwencji. Jeśli funkcja ma wpływ na obie pozycje strumienia *_Way* musi być `ios_base::beg` lub `ios_base::end` i zarówno strumienie są umieszczane w tym samym elemencie. W przeciwnym razie (lub żadna pozycja ma wpływ) pozycjonowania operacja zakończy się niepowodzeniem.

Jeśli funkcja się powiedzie, w zmieniania jednego lub obu pozycji strumienia, zwraca położenie wynikowy strumień. W przeciwnym razie nie powiedzie się i zwraca pozycję nieprawidłowy strumień.

## <a name="seekpos"></a>  basic_stringbuf::seekpos

Chronione wirtualna funkcja składowa próbuje alter dla strumieni kontrolowanego bieżącej pozycji.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

*_Sp*<br/>
Położenie do wyszukania dla.

*_Tryb*<br/>
Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja się powiedzie, w zmieniania jednego lub obu pozycji strumienia, zwraca położenie wynikowy strumień. W przeciwnym razie nie powiedzie się i zwraca pozycję nieprawidłowy strumień. Aby określić, jeśli pozycja strumienia jest nieprawidłowa, porównaj wartość zwracaną z `pos_type(off_type(-1))`.

### <a name="remarks"></a>Uwagi

Basic_stringbuf — klasa obiektu < **Elem**, **Tr**, `Alloc`>, pozycji strumienia, który składa się wyłącznie z przesunięciu strumienia. Przesunięcia zero wskazuje pierwszego elementu w kontrolowanej sekwencji. Nowa pozycja jest określana przez _ *Sp*.

Jeśli **trybu & ios_base::in** jest różna od zera, funkcja zmienia następnej pozycji, aby odczytać w buforze wejściowym. Jeśli **trybu & ios_base::out** jest różna od zera, funkcja zmienia następnej pozycji, aby zapisać w buforze danych wyjściowych. Strumień, których to dotyczy musi istnieć buforu. Pozycjonowania operacja została wykonana pomyślnie wynikowy pozycji strumienia musi znajdować się w kontrolowanej sekwencji. W przeciwnym razie (lub żadna pozycja ma wpływ) pozycjonowania operacja zakończy się niepowodzeniem.

## <a name="str"></a>  basic_stringbuf::str

Ustawia lub pobiera tekst w buforze ciąg bez zmiany pozycji zapisu.

```cpp
basic_string<Elem, Tr, Alloc> str() const;
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

*_Newstr*<br/>
Nowy ciąg.

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt klasy [basic_string](../standard-library/basic-string-class.md) \< **Elem**, **Tr**, alokacji **>,** którego kontrolowanej sekwencji jest kopią Sekwencja wartości clientauthtrustmode  **\*to**.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zwraca obiekt basic_string — Klasa < **Elem**, **Tr**, `Alloc`>, którego kontrolowanej sekwencji jest kopię sekwencji kontrolowanej przez  **\*to**. Sekwencja skopiowane zależą od trybu przechowywanych stringbuf:

- Jeśli **trybu & ios_base::out** jest różna od zera i istnieje buforu wyjściowego, sekwencja jest bufor wszystkie dane wyjściowe ( [epptr —](../standard-library/basic-streambuf-class.md#epptr) - [pbase —](../standard-library/basic-streambuf-class.md#pbase) elementów od za pomocą `pbase`).

- Jeśli **trybu & ios_base::in** jest różna od zera i istnieje buforu wejściowego, sekwencja jest cały buforu wejściowego ( [egptr —](../standard-library/basic-streambuf-class.md#egptr) - [eback —](../standard-library/basic-streambuf-class.md#eback) elementy rozpoczynające się od `eback`).

- W przeciwnym razie skopiowany sekwencji jest pusty.

Funkcja drugiego członka powoduje cofnięcie przydziału dowolnej sekwencji aktualnie kontrolowane przez  **\*to**. Następnie przydziela kopię sekwencji kontrolowanej przez *_Newstr*. Jeśli **trybu & ios_base::in** jest różna od zera, ustawia buforu wejściowego, należy rozpocząć odczyt na początku sekwencji. Jeśli **trybu & ios_base::out** jest różna od zera, ustawia bufor wyjściowy do uruchomienia z możliwością zapisu na początku sekwencji.

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

## <a name="traits_type"></a>  basic_stringbuf::traits_type

Kojarzy nazwę typu z *Tr* parametru szablonu.

```cpp
typedef Tr traits_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem dla parametru szablonu *Tr*.

## <a name="underflow"></a>  basic_stringbuf::underflow

Chroniona funkcja wirtualna, aby wyodrębnić bieżącego elementu ze strumienia wejściowego.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie powiedzie się, zwraca **traits_type::**[eof](../standard-library/char-traits-struct.md#eof). W przeciwnym razie zwraca bieżącego elementu w strumieniu wejściowym, które są konwertowane.

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego próbuje wyodrębnić bieżącego elementu `byte` z buforu wejściowego poszerzyć bieżącą pozycję w strumieniu i zwraca element jako **traits_type::**[to_int_type](../standard-library/char-traits-struct.md#to_int_type)( **bajtów**). Jego można to zrobić w jednym ze sposobów: Jeśli pozycji odczytu jest dostępny, zajmuje `byte` elementu przechowywanego w pozycji odczytu i przesuwa wskaźnik następnej dla buforu danych wejściowych.

## <a name="swap"></a>  basic_streambuf::swap

Zamienia zawartość tego buforu ciągu z innego buforu ciągu.

```cpp
void basic_stringbuf<T>::swap(basic_stringbuf& other)
```

### <a name="parameters"></a>Parametry

*other*<br/>
Basic_stringbuf — których zawartość zostanie zamienione z tym basic_stringbuf —.

### <a name="remarks"></a>Uwagi

## <a name="op_eq"></a>  basic_stringbuf::operator =

Przypisuje zawartość basic_stringbuf — po prawej stronie operatora basic_stringbuf — z lewej strony.

```cpp
basic_stringbuf& basic_stringbuf:: operator=(const basic_stringbuf& other)
```

### <a name="parameters"></a>Parametry

*other*<br/>
Basic_stringbuf —, których zawartość, w tym cech ustawień regionalnych, które zostaną przypisane do stringbuf po lewej stronie operatora.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
