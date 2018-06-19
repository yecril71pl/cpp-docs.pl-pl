---
title: basic_stringbuf — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6e7ec812ffeb50e83d59df764224ed9dcdaf07d8
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
ms.locfileid: "33848544"
---
# <a name="basicstringbuf-class"></a>basic_stringbuf — Klasa

W tym artykule opisano buforu strumienia, który kontroluje przekazywania elementów typu `Elem`, którego cech znaków są określane przez klasę `Tr`, do i z sekwencję elementy przechowywane w tablicy obiektów.

## <a name="syntax"></a>Składnia

```cpp
template <class Elem, class Tr = char_traits<Elem>,
    class Alloc = allocator<Elem>>
class basic_stringbuf : public basic_streambuf<Elem, Tr>
```

### <a name="parameters"></a>Parametry

`Alloc` Allocator — klasa.

`Elem` Typ podstawowy elementu ciągu.

`Tr` Specjalizowany cech znaków w elemencie podstawowe ciągu.

## <a name="remarks"></a>Uwagi

Obiekt jest przydzielona, rozszerzone i zwolniony w razie potrzeby w celu uwzględnienia zmian w sekwencji.

Obiekt basic_stringbuf — Klasa < `Elem`, `Tr`, `Alloc`> przechowuje kopię `ios_base::` [openmode](../standard-library/ios-base-class.md#openmode) argumentu z jego konstruktora jako jego `stringbuf` tryb **tryb** :

- Jeśli `mode & ios_base::in` jest różna od zera, bufor wejściowy jest niedostępny. Aby uzyskać więcej informacji, zobacz [basic_streambuf — klasa](../standard-library/basic-streambuf-class.md).

- Jeśli `mode & ios_base::out` jest różna od zera, bufor wyjściowy jest dostępny.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[basic_stringbuf](#basic_stringbuf)|Tworzy obiekt typu `basic_stringbuf`.|

### <a name="typedefs"></a>Typedefs

|Nazwa typu|Opis|
|-|-|
|[allocator_type](#allocator_type)|Typ jest synonimem parametru szablonu `Alloc`.|
|[char_type](#char_type)|Kojarzy nazwę typu z `Elem` parametru szablonu.|
|[int_type](#int_type)|Sprawia, że ten typ w `basic_filebuf`jego odpowiednikiem typu o takiej samej nazwie w zakresie `Tr` zakresu.|
|[off_type](#off_type)|Sprawia, że ten typ w `basic_filebuf`jego odpowiednikiem typu o takiej samej nazwie w zakresie `Tr` zakresu.|
|[pos_type](#pos_type)|Sprawia, że ten typ w `basic_filebuf`jego odpowiednikiem typu o takiej samej nazwie w zakresie `Tr` zakresu.|
|[traits_type](#traits_type)|Kojarzy nazwę typu z `Tr` parametru szablonu.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[overflow](#overflow)|Funkcja chroniony, wirtualny, który można wywołać po wstawieniu nowego znaku w buforze pełna.|
|[pbackfail](#pbackfail)|Chroniony element członkowski wirtualnego funkcja próbuje ponownie poddane element buforu wejściowego, następnie ułatwia bieżącego elementu (wskazywana przez wskaźnik następnej).|
|[seekoff](#seekoff)|Funkcja chronionego członka wirtualnego próbuje zmienić bieżącego położenia dla strumieni kontrolowane.|
|[seekpos](#seekpos)|Funkcja chronionego członka wirtualnego próbuje zmienić bieżącego położenia dla strumieni kontrolowane.|
|[str](#str)|Ustawia lub pobiera tekst w buforze ciągu bez zmiany pozycji zapisu.|
|swap||
|[underflow](#underflow)|Funkcja chroniony element członkowski wirtualnego można wyodrębnić bieżącego elementu ze strumienia wejściowego.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<sstream — >

**Namespace:** Standard

## <a name="allocator_type"></a>  basic_stringbuf::allocator_type

Typ jest synonimem parametru szablonu `Alloc`.

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

`_Mode` Jedno z wyliczeń w [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

`str` Obiekt typu [basic_string —](../standard-library/basic-string-class.md).

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje wskaźnika o wartości null w wszystkie wskaźniki kontrolowanie buforu wejściowego i buforu wyjściowego. Aby uzyskać więcej informacji, zobacz sekcję uwag [basic_streambuf — klasa](../standard-library/basic-streambuf-class.md). Przechowuje także `_Mode` jako tryb stringbuf. Aby uzyskać więcej informacji, zobacz sekcję uwag [basic_stringbuf — klasa](../standard-library/basic-stringbuf-class.md).

Drugi Konstruktor przydziela kopię sekwencji kontrolowane przez obiekt ciągu `str`. Jeśli `_Mode & ios_base::in` jest różna od zera, ustawia bufor wejściowy należy rozpocząć odczyt na początku sekwencji. Jeśli `_Mode & ios_base::out` jest różna od zera, ustawia bufor wyjściowy ma rozpocząć się zapis na początku sekwencji. Przechowuje także `_Mode` jako tryb stringbuf. Aby uzyskać więcej informacji, zobacz sekcję uwag [basic_stringbuf — klasa](../standard-library/basic-stringbuf-class.md).

## <a name="char_type"></a>  basic_stringbuf::char_type

Kojarzy nazwę typu z **elementu** parametru szablonu.

```cpp
typedef Elem char_type;
```

## <a name="int_type"></a>  basic_stringbuf::int_type

Sprawia, że ten typ w zakresie basic_filebuf — jego odpowiednikiem typu o takiej samej nazwie w **Tr** zakresu.

```cpp
typedef typename traits_type::int_type int_type;
```

## <a name="off_type"></a>  basic_stringbuf::off_type

Sprawia, że ten typ w zakresie basic_filebuf — jego odpowiednikiem typu o takiej samej nazwie w **Tr** zakresu.

```cpp
typedef typename traits_type::off_type off_type;
```

## <a name="overflow"></a>  basic_stringbuf::Overflow

Chronione funkcji wirtualnej można wywołać po wstawieniu nowego znaku w buforze pełna.

```cpp
virtual int_type overflow(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

`_Meta` Znak do wstawienia w buforze, lub **traits_type::eof**.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść, zwraca **traits_type::eof**. W przeciwnym razie zwraca **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Uwagi

Jeśli _ *Meta* porównuje równa **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), funkcja chroniony element członkowski wirtualnego próbuje wstawić elementu **traits_type::** [ to_char_type](../standard-library/char-traits-struct.md#to_char_type)(\_ *Meta*) do buforu wyjściowego. Go to zrobić na różne sposoby:

- Jeśli pozycja zapisu jest dostępny, można przechowywać elementu w miejscu zapisu i zwiększyć wskaźnik następnej buforu danych wyjściowych.

- Go można udostępnić pozycję zapisu przydzielając nowej lub dodatkowej pamięci masowej dla buforu danych wyjściowych. Rozszerzanie buforu wyjściowego w ten sposób rozszerzają wszystkie skojarzone buforu wejściowego.

## <a name="pbackfail"></a>  basic_stringbuf::pbackfail

Funkcja chroniony element członkowski wirtualnego próbuje ponownie poddane element buforze wejściowym, a następnie wprowadź go bieżącego elementu (wskazywana przez wskaźnik następnej).

```cpp
virtual int_type pbackfail(int_type _Meta = traits_type::eof());
```

### <a name="parameters"></a>Parametry

`_Meta` Znak do wstawienia w buforze, lub **traits_type::eof**.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść, zwraca **traits_type::eof**. W przeciwnym razie zwraca **traits_type::**[not_eof](../standard-library/char-traits-struct.md#not_eof)(_ *Meta*).

### <a name="remarks"></a>Uwagi

Jeśli `_Meta` porównuje równa **traits_type::**[eof](../standard-library/char-traits-struct.md#eof), elementu do usunięcia jest już w strumieniu przed bieżącego elementu. W przeciwnym razie ten element został zastąpiony przez **bajtów** = **traits_type::**[to_char_type](../standard-library/char-traits-struct.md#to_char_type)(_ *Meta*). Funkcja można odłożyć element na różne sposoby:

- Jeśli pozycja putback jest dostępny, a element przechowywane porównuje równa bajtów, jego zmniejszanie wskaźnik następnej dla buforu wejściowego.

- Pozycja putback jest dostępny, a sekwencji należy zmienić zezwala na tryb stringbuf ( **trybu & ios_base::out** jest różna od zera), można przechowywać bajtów w pozycji putback i zmniejszyć wskaźnik następnej dla buforu wejściowego.

## <a name="pos_type"></a>  basic_stringbuf::pos_type

Sprawia, że ten typ w zakresie basic_filebuf — jego odpowiednikiem typu o takiej samej nazwie w **Tr** zakresu.

```cpp
typedef typename traits_type::pos_type pos_type;
```

## <a name="seekoff"></a>  basic_stringbuf::seekoff

Funkcja chronionego członka wirtualnego próbuje zmienić bieżącego położenia dla strumieni kontrolowane.

```cpp
virtual pos_type seekoff(
    off_type _Off,
    ios_base::seekdir _Way,
    ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

`_Off` Położenie do wyszukania dla względem `_Way`. Aby uzyskać więcej informacji, zobacz [basic_stringbuf::off_type](#off_type).

`_Way` Punkt początkowy dla operacji przesunięcia. Zobacz [ios_base::seekdir](../standard-library/ios-base-class.md#seekdir) prawidłowych wartości.

`_Mode` Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji. Aby uzyskać więcej informacji, zobacz [ios_base::openmode](../standard-library/ios-base-class.md#openmode).

### <a name="return-value"></a>Wartość zwracana

Zwraca nowego położenia lub nieprawidłowy strumień pozycji.

### <a name="remarks"></a>Uwagi

Dla obiekt klasy `basic_stringbuf<Elem, Tr, Alloc>`, pozycji w strumieniu składa się wyłącznie z przesunięcia strumienia. Przesunięcia zero oznacza pierwszy element kontrolowanej sekwencji.

Nowa pozycja jest określane w następujący sposób:

- Jeśli `_Way`  ==  `ios_base::beg`, nowe położenie jest na początku strumienia plus `_Off`.

- Jeśli `_Way`  ==  `ios_base::cur`, nowe położenie jest bieżącej pozycji strumienia plus `_Off`.

- Jeśli `_Way`  ==  `ios_base::end`, nowe położenie jest koniec strumienia plus `_Off`.

Jeśli `_Mode & ios_base::in` jest różna od zera, funkcja zmienia pozycję dalej do odczytu w buforze wejściowym. Jeśli `_Mode & ios_base::out` jest różna od zera, funkcja zmienia dalej pozycji do zapisania w buforze danych wyjściowych. Dla strumienia, których to dotyczy musi istnieć buforu. Pozycjonowania operacja się powiodła wynikowy pozycji strumienia musi znajdować się w kontrolowanej sekwencji. Jeśli funkcja dotyczy obu pozycji strumienia `_Way` musi być `ios_base::beg` lub `ios_base::end` i obie strumieni znajdują się w tym samym elemencie. W przeciwnym razie (lub jeśli żadna pozycja ma to wpływ na) pozycjonowania kończy się niepowodzeniem.

Jeśli funkcja pomyślnie Zmienianie jednego lub obu pozycji strumienia, zwraca pozycji w strumieniu wynikowe. W przeciwnym razie nie powiedzie się i zwraca pozycję nieprawidłowy strumień.

## <a name="seekpos"></a>  basic_stringbuf::seekpos

Funkcja chronionego członka wirtualnego próbuje zmienić bieżącego położenia dla strumieni kontrolowane.

```cpp
virtual pos_type seekpos(pos_type _Sp, ios_base::openmode _Mode = ios_base::in | ios_base::out);
```

### <a name="parameters"></a>Parametry

`_Sp` Położenie do wyszukania dla.

`_Mode` Określa tryb pozycję wskaźnika. Wartość domyślna to umożliwia modyfikowanie, Odczyt i zapis pozycji.

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja pomyślnie Zmienianie jednego lub obu pozycji strumienia, zwraca pozycji w strumieniu wynikowe. W przeciwnym razie nie powiedzie się i zwraca pozycję nieprawidłowy strumień. Aby ustalić, czy pozycja strumienia jest nieprawidłowa, porównanie wartości zwracanych z `pos_type(off_type(-1))`.

### <a name="remarks"></a>Uwagi

Dla obiekt basic_stringbuf — Klasa < **elementu**, **Tr**, `Alloc`>, pozycji w strumieniu składa się wyłącznie z przesunięcia strumienia. Przesunięcia zero oznacza pierwszy element kontrolowanej sekwencji. Nowa pozycja jest określany przez _ *Sp*.

Jeśli **trybu & ios_base::in** jest różna od zera, funkcja zmienia pozycję dalej do odczytu w buforze wejściowym. Jeśli **trybu & ios_base::out** jest różna od zera, funkcja zmienia dalej pozycji do zapisania w buforze danych wyjściowych. Dla strumienia, których to dotyczy musi istnieć buforu. Pozycjonowania operacja się powiodła wynikowy pozycji strumienia musi znajdować się w kontrolowanej sekwencji. W przeciwnym razie (lub jeśli żadna pozycja ma to wpływ na) pozycjonowania kończy się niepowodzeniem.

## <a name="str"></a>  basic_stringbuf::str

Ustawia lub pobiera tekst w buforze ciągu bez zmiany pozycji zapisu.

```cpp
basic_string<Elem, Tr, Alloc> str() const;
void str(
    const basic_string<Elem, Tr, Alloc>& _Newstr);
```

### <a name="parameters"></a>Parametry

`_Newstr` Nowe parametry.

### <a name="return-value"></a>Wartość zwracana

Zwraca obiekt klasy [basic_string —](../standard-library/basic-string-class.md) \< **elementu**, **Tr**, alokacji **>,** których kontrolowanej sekwencji jest kopią Sekwencja kontrolowane przez  **\*to**.

### <a name="remarks"></a>Uwagi

Pierwszy funkcji członkowskiej zwraca obiekt basic_string — Klasa < **elementu**, **Tr**, `Alloc`>, którego kontrolowanej sekwencji jest kopią sekwencji kontrolowane przez  **\*to**. Sekwencja skopiowane zależy od trybu przechowywanych stringbuf:

- Jeśli **trybu & ios_base::out** jest różna od zera i istnieje buforu wyjściowego, sekwencja jest buforu całej danych wyjściowych ( [epptr](../standard-library/basic-streambuf-class.md#epptr) - [pbase](../standard-library/basic-streambuf-class.md#pbase) od elementów z `pbase`).

- Jeśli **trybu & ios_base::in** jest różna od zera i istnieje buforu wejściowego, sekwencja jest cały bufor wejściowy ( [egptr](../standard-library/basic-streambuf-class.md#egptr) - [eback](../standard-library/basic-streambuf-class.md#eback) elementy rozpoczynające się od `eback`).

- W przeciwnym razie sekwencja skopiowanych jest pusta.

Drugi funkcji członkowskiej zwalnia wszelkie sekwencji obecnie kontrolowane przez  **\*to**. Następnie przydziela kopię sekwencji kontrolowane przez `_Newstr`. Jeśli **trybu & ios_base::in** jest różna od zera, ustawia bufor wejściowy należy rozpocząć odczyt na początku sekwencji. Jeśli **trybu & ios_base::out** jest różna od zera, ustawia bufor wyjściowy, aby rozpocząć pisanie na początku sekwencji.

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

Kojarzy nazwę typu z **Tr** parametru szablonu.

```cpp
typedef Tr traits_type;
```

### <a name="remarks"></a>Uwagi

Typ jest synonimem parametru szablonu **Tr**.

## <a name="underflow"></a>  basic_stringbuf::underflow

Chronione funkcji wirtualnych można wyodrębnić bieżącego elementu ze strumienia wejściowego.

```cpp
virtual int_type underflow();
```

### <a name="return-value"></a>Wartość zwracana

Jeśli funkcja nie może się powieść, zwraca **traits_type::**[eof](../standard-library/char-traits-struct.md#eof). W przeciwnym razie zwraca bieżący element w strumieniu wejściowym, które są wymieniane.

### <a name="remarks"></a>Uwagi

Funkcja chroniony element członkowski wirtualnego próbuje wyodrębnić bieżącego elementu **bajtów** z buforu wejściowego wcześniejszego bieżącej pozycji strumienia i zwracać element jako **traits_type::**[do _int_type](../standard-library/char-traits-struct.md#to_int_type)( **bajtów**). Go to zrobić w jednym ze sposobów: Jeśli pozycja odczytu jest dostępny, przyjmuje **bajtów** jako element przechowywane w pozycji odczytu i przesuwa wskaźnik następnej dla buforu wejściowego.

## <a name="swap"></a>  basic_streambuf::swap

Zamienia zawartość tego buforu ciągu z innego ciągu buforu.

```cpp
void basic_stringbuf<T>::swap(basic_stringbuf& other)
```

### <a name="parameters"></a>Parametry

`other` Basic_stringbuf — których zawartość zostanie zamienione z tym basic_stringbuf —.

### <a name="remarks"></a>Uwagi

## <a name="op_eq"></a>  basic_stringbuf::operator =

Przypisuje zawartość basic_stringbuf — po prawej stronie operatora basic_stringbuf — po lewej stronie.

```cpp
basic_stringbuf& basic_stringbuf:: operator=(const basic_stringbuf& other)
```

### <a name="parameters"></a>Parametry

`other` Basic_stringbuf —, których zawartość, w tym cech ustawień regionalnych, zostanie przypisana do stringbuf po lewej stronie operatora.

### <a name="remarks"></a>Uwagi

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
