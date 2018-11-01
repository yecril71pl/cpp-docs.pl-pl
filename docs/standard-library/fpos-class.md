---
title: fpos — Klasa
ms.date: 11/04/2016
f1_keywords:
- iosfwd/std::fpos
- iosfwd/std::fpos::seekpos
- iosfwd/std::fpos::state
- iosfwd/std::fpos::operator streamoff
helpviewer_keywords:
- std::fpos [C++]
- std::fpos [C++], seekpos
- std::fpos [C++], state
ms.assetid: ffd0827c-fa34-47f4-b10e-5cb707fcde47
ms.openlocfilehash: bf15cdf0ec4df1301b074ba2ae179dee3619d30d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564206"
---
# <a name="fpos-class"></a>fpos — Klasa

Klasa szablonu opisuje obiekt, który można przechowywać wszystkie informacje niezbędne do przywrócenia wskaźnika dowolnego położenie pliku w dowolnej usłudze stream. Obiekt fpos — klasa\< **St**> skutecznie są przechowywane co najmniej dwa obiekty Członkowskie:

- Liczbę bajtów względem typu [streamoff](../standard-library/ios-typedefs.md#streamoff).

- Stan konwersji, do użytku przez obiekt basic_filebuf — klasa, typu `St`, zazwyczaj `mbstate_t`.

Mogą być również przechowywane pozycji dowolnego pliku do użytku przez obiekt klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md), typu `fpos_t`. W środowiskach ograniczony rozmiar, jednak `streamoff` i `fpos_t` czasami mogą być używane zamiennie. W środowiskach nie strumieni, które mają zależnej od stanu kodowania `mbstate_t` rzeczywiście być nieużywane. W związku z tym liczba przechowywanych obiektów mogą się różnić.

## <a name="syntax"></a>Składnia

```cpp
template <class Statetype>
class fpos
```

### <a name="parameters"></a>Parametry

*Statetype*<br/>
Informacje o stanie.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[fpos —](#fpos)|Utwórz obiekt, który zawiera informacje o stanie (przesunięciem) w strumieniu.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja elementu członkowskiego|Opis|
|-|-|
|[seekpos —](#seekpos)|Używane przez standardowej biblioteki C++ tylko wewnętrznie. Nie wywołuj tej metody w kodzie.|
|[state](#state)|Ustawia lub zwraca stan konwersji.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](#op_neq)|Wskaźniki położenie pliku testów pod kątem nierówności.|
|[operator +](#op_add)|Zwiększa wartość wskaźnika pozycji pliku.|
|[operator+=](#op_add_eq)|Zwiększa wartość wskaźnika pozycji pliku.|
|[operator-](#operator-)|Wskaźnik zmniejsza położenie pliku.|
|[operator-=](#operator-_eq)|Wskaźnik zmniejsza położenie pliku.|
|[operator==](#op_eq_eq)|Wskaźniki położenie pliku testów pod kątem równości.|
|[streamoff — operator](#op_streamoff)|Typ obiektu rzutowania `fpos` do obiektu typu `streamoff`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<dla systemu ios >

**Namespace:** standardowe

## <a name="fpos"></a>  fpos::fpos

Utwórz obiekt, który zawiera informacje o stanie (przesunięciem) w strumieniu.

```cpp
fpos(streamoff _Off = 0);

fpos(Statetype _State, fpos_t _Filepos);
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Przesunięcie w strumieniu.

*_Stanu*<br/>
Początkowy stan `fpos` obiektu.

*_Filepos*<br/>
Przesunięcie w strumieniu.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje przesunięcie *_Off*względnych na początku pliku, a stan konwersji początkowej (jeśli ma znaczenie,). Jeśli *_Off* wynosi -1, wynikowy obiekt reprezentuje pozycji nieprawidłowy strumień.

Drugi Konstruktor przechowuje zero przesunięcie i obiekt *_stanu*.

## <a name="op_neq"></a>  fpos::operator! =

Wskaźniki położenie pliku testów pod kątem nierówności.

```cpp
bool operator!=(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parametry

*right*<br/>
Wskaźnik położenia pliku za pomocą którego chcesz porównać.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wskaźników położenia pliku nie są takie same, w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `!(*this == right)`.

### <a name="example"></a>Przykład

```cpp
// fpos_op_neq.cpp
// compile with: /EHsc
#include <fstream>
#include <iostream>

int main( )
{
   using namespace std;

   fpos<int> pos1, pos2;
   ifstream file;
   char c;

   // Compare two fpos object
   if ( pos1 != pos2 )
      cout << "File position pos1 and pos2 are not equal" << endl;
   else
      cout << "File position pos1 and pos2 are equal" << endl;

   file.open( "fpos_op_neq.txt" );
   file.seekg( 0 );   // Goes to a zero-based position in the file
   pos1 = file.tellg( );
   file.get( c);
   cout << c << endl;

   // Increment pos1
   pos1 += 1;
   file.get( c );
   cout << c << endl;

   pos1 = file.tellg( ) - fpos<int>( 2);
   file.seekg( pos1 );
   file.get( c );
   cout << c << endl;

   // Increment pos1
   pos1 = pos1 + fpos<int>( 1 );
   file.get(c);
   cout << c << endl;

   pos1 -= fpos<int>( 2 );
   file.seekg( pos1 );
   file.get( c );
   cout << c << endl;

   file.close( );
}
```

## <a name="op_add"></a>  fpos::operator +

Zwiększa wartość wskaźnika pozycji pliku.

```cpp
fpos<Statetype> operator+(streamoff _Off) const;
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Przesunięcie, według którego mają być zwiększane wskaźnik położenia pliku.

### <a name="return-value"></a>Wartość zwracana

Pozycja w pliku.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca **fpos — (\*to) +=** `_Off`.

### <a name="example"></a>Przykład

Zobacz [operator! =](#op_neq) przykład użycia `operator+`.

## <a name="op_add_eq"></a>  fpos::operator +=

Zwiększa wartość wskaźnika pozycji pliku.

```cpp
fpos<Statetype>& operator+=(streamoff _Off);
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Przesunięcie, według którego mają być zwiększane wskaźnik położenia pliku.

### <a name="return-value"></a>Wartość zwracana

Pozycja w pliku.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego dodaje *_Off* przechowywanych przesunięcia elementu członkowskiego obiektu, a następnie zwraca  **\*to**. Do pozycjonowania w pliku, wynik jest zazwyczaj prawidłowy tylko w przypadku danych binarnych strumieni, które nie mają kodowanie zależnej od stanu.

### <a name="example"></a>Przykład

Zobacz [operator! =](#op_neq) przykład użycia `operator+=`.

## <a name="fpos__operator-"></a>  fpos::operator-

Wskaźnik zmniejsza położenie pliku.

```cpp
streamoff operator-(const fpos<Statetype>& right) const;

fpos<Statetype> operator-(streamoff _Off) const;
```

### <a name="parameters"></a>Parametry

*right*<br/>
Położenie pliku.

*_Off*<br/>
Przesunięcie Stream.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja elementu członkowskiego zwraca `(streamoff)*this - (streamoff) right`. Druga funkcja elementu członkowskiego zwraca `fpos(*this) -= _Off`.

### <a name="example"></a>Przykład

Zobacz [operator! =](#op_neq) przykład użycia `operator-`.

## <a name="fpos__operator-_eq"></a>  fpos::operator-=

Wskaźnik zmniejsza położenie pliku.

```cpp
fpos<Statetype>& operator-=(streamoff _Off);
```

### <a name="parameters"></a>Parametry

*_Off*<br/>
Przesunięcie Stream.

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu członkowskiego zwraca `fpos(*this) -= _Off`.

### <a name="remarks"></a>Uwagi

Do pozycjonowania w pliku, wynik jest zazwyczaj prawidłowy tylko w przypadku danych binarnych strumieni, które nie mają kodowanie zależnej od stanu.

### <a name="example"></a>Przykład

Zobacz [operator! =](#op_neq) przykład użycia `operator-=`.

## <a name="op_eq_eq"></a>  fpos::operator ==

Wskaźniki położenie pliku testów pod kątem równości.

```cpp
bool operator==(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parametry

*right*<br/>
Wskaźnik położenia pliku za pomocą którego chcesz porównać.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wskaźników położenia pliku są równe; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca `(streamoff)*this == (streamoff)right`.

### <a name="example"></a>Przykład

Zobacz [operator! =](#op_neq) przykład użycia `operator+=`.

## <a name="op_streamoff"></a>  fpos::operator streamoff

Rzutowanie obiektu typu `fpos` do obiektu typu `streamoff`.

```cpp
operator streamoff() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca przechowywaną przesunięcia elementu członkowskiego, obiekt i wszystkie dodatkowe przesunięcie przechowywane jako część `fpos_t` elementu członkowskiego obiektu.

### <a name="example"></a>Przykład

```cpp
// fpos_op_streampos.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main( )
{
   using namespace std;
   streamoff s;
   ofstream file( "rdbuf.txt");

   fpos<mbstate_t> f = file.tellp( );
   // Is equivalent to ..
   // streampos f = file.tellp( );
   s = f;
   cout << s << endl;
}
```

```Output
0
```

## <a name="seekpos"></a>  fpos::seekpos

Ta metoda jest używana wewnętrznie przez standardowej biblioteki C++ tylko. Nie wywołuj tej metody w kodzie.

```cpp
fpos_t seekpos() const;
```

## <a name="state"></a>  fpos::State

Ustawia lub zwraca stan konwersji.

```cpp
Statetype state() const;

void state(Statetype _State);
```

### <a name="parameters"></a>Parametry

*_Stanu*<br/>
Nowy stan konwersji.

### <a name="return-value"></a>Wartość zwracana

Stan konwersji.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja elementu członkowskiego zwraca wartość przechowywaną w `St` elementu członkowskiego obiektu. Drugi magazynów funkcja elementu członkowskiego *_stanu* w `St` elementu członkowskiego obiektu.

### <a name="example"></a>Przykład

```cpp
// fpos_state.cpp
// compile with: /EHsc
#include <ios>
#include <iostream>
#include <fstream>

int main() {
   using namespace std;
   streamoff s;
   ifstream file( "fpos_state.txt" );

   fpos<mbstate_t> f = file.tellg( );
   char ch;
   while ( !file.eof( ) )
      file.get( ch );
   s = f;
   cout << f.state( ) << endl;
   f.state( 9 );
   cout << f.state( ) << endl;
}
```

## <a name="see-also"></a>Zobacz także

[Bezpieczeństwo wątku w standardowej bibliotece C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream, programowanie](../standard-library/iostream-programming.md)<br/>
[Konwencje iostream](../standard-library/iostreams-conventions.md)<br/>
