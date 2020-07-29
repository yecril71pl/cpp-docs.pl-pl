---
title: fpos — Klasa
ms.date: 03/27/2019
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
ms.openlocfilehash: 37536443455ca4ddc40568e15951b814982d4ad9
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/27/2020
ms.locfileid: "87193305"
---
# <a name="fpos-class"></a>fpos — Klasa

Szablon klasy opisuje obiekt, który może przechowywać wszystkie informacje potrzebne do przywrócenia dowolnego wskaźnika położenia pliku w ramach dowolnego strumienia. Obiekt klasy FPOS \< **St**> efektywnie przechowuje co najmniej dwa obiekty Członkowskie:

- Przesunięcie bajtowe typu [streamoff —](../standard-library/ios-typedefs.md#streamoff).

- Stan konwersji, używany przez obiekt klasy basic_filebuf typu `St` , zazwyczaj `mbstate_t` .

Może również przechowywać dowolne położenie pliku, do użytku przez obiekt klasy [basic_filebuf](../standard-library/basic-filebuf-class.md)typu `fpos_t` . Jednak w przypadku środowiska z ograniczonym rozmiarem pliku `streamoff` i `fpos_t` czasami mogą być używane zamiennie. W przypadku środowiska bez strumieni z kodowaniem zależnym od stanu `mbstate_t` mogą faktycznie być nieużywane. W związku z tym liczba przechowywanych obiektów Członkowskich może się różnić.

## <a name="syntax"></a>Składnia

```cpp
template <class Statetype>
class fpos
```

### <a name="parameters"></a>Parametry

*StateType*\
Informacje o stanie.

### <a name="constructors"></a>Konstruktory

|Konstruktor|Opis|
|-|-|
|[FPOS](#fpos)|Utwórz obiekt, który zawiera informacje o pozycji (przesunięcie) w strumieniu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[seekpos](#seekpos)|Używane wewnętrznie tylko przez standardową bibliotekę języka C++. Nie wywołuj tej metody z kodu.|
|[Państwu](#state)|Ustawia lub zwraca stan konwersji.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator! =](#op_neq)|Testuje wskaźniki położenia plików pod kątem nierówności.|
|[operator +](#op_add)|Zwiększa wskaźnik położenia pliku.|
|[operator + =](#op_add_eq)|Zwiększa wskaźnik położenia pliku.|
|[zakład](#operator-)|Zmniejsza wskaźnik położenia pliku.|
|[operator-=](#operator-_eq)|Zmniejsza wskaźnik położenia pliku.|
|[operator = =](#op_eq_eq)|Testuje wskaźniki położenia plików pod kątem równości.|
|[streamoff — operatora](#op_streamoff)|Rzutuje obiekt typu `fpos` na obiekt typu `streamoff` .|

## <a name="requirements"></a>Wymagania

**Nagłówek:**\<ios>

**Przestrzeń nazw:** std

## <a name="fposfpos"></a><a name="fpos"></a>FPOS:: FPOS

Utwórz obiekt, który zawiera informacje o pozycji (przesunięcie) w strumieniu.

```cpp
fpos(streamoff _Off = 0);

fpos(Statetype _State, fpos_t _Filepos);
```

### <a name="parameters"></a>Parametry

*_Off*\
Przesunięcie do strumienia.

*_State*\
Stan początkowy `fpos` obiektu.

*_Filepos*\
Przesunięcie do strumienia.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje *_Off*przesunięcia względem początku pliku i w stanie konwersji początkowej (jeśli ma to znaczenie). Jeśli *_Off* ma wartość-1, obiekt wyniku reprezentuje nieprawidłową pozycję strumienia.

Drugi Konstruktor przechowuje Przesunięcie zerowe i *_State*obiektu.

## <a name="fposoperator"></a><a name="op_neq"></a>FPOS:: operator! =

Testuje wskaźniki położenia plików pod kątem nierówności.

```cpp
bool operator!=(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Wskaźnik pozycji pliku, względem którego ma zostać wykonane porównanie.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wskaźniki położenia plików nie są równe, w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca wartość `!(*this == right)` .

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

## <a name="fposoperator"></a><a name="op_add"></a>FPOS:: operator +

Zwiększa wskaźnik położenia pliku.

```cpp
fpos<Statetype> operator+(streamoff _Off) const;
```

### <a name="parameters"></a>Parametry

*_Off*\
Przesunięcie, według którego ma zostać zwiększony wskaźnik położenia pliku.

### <a name="return-value"></a>Wartość zwracana

Pozycja w pliku.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca **FPOS ( \* this) + =** `_Off` .

### <a name="example"></a>Przykład

Zobacz [operator! =](#op_neq) , aby uzyskać przykład użycia `operator+` .

## <a name="fposoperator"></a><a name="op_add_eq"></a>FPOS:: operator + =

Zwiększa wskaźnik położenia pliku.

```cpp
fpos<Statetype>& operator+=(streamoff _Off);
```

### <a name="parameters"></a>Parametry

*_Off*\
Przesunięcie, według którego ma zostać zwiększony wskaźnik położenia pliku.

### <a name="return-value"></a>Wartość zwracana

Pozycja w pliku.

### <a name="remarks"></a>Uwagi

Funkcja członkowska dodaje *_Off* do przechowywanego obiektu elementu członkowskiego przesunięcia, a następnie zwraca ** \* ten**element. W przypadku pozycjonowania w pliku wynik jest zwykle prawidłowy tylko w przypadku strumieni binarnych, które nie mają kodowania zależnego od stanu.

### <a name="example"></a>Przykład

Zobacz [operator! =](#op_neq) , aby uzyskać przykład użycia `operator+=` .

## <a name="fposoperator-"></a><a name="operator-"></a>FPOS:: operator-

Zmniejsza wskaźnik położenia pliku.

```cpp
streamoff operator-(const fpos<Statetype>& right) const;

fpos<Statetype> operator-(streamoff _Off) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Położenie pliku.

*_Off*\
Przesunięcie strumienia.

### <a name="return-value"></a>Wartość zwracana

Pierwsza funkcja elementu członkowskiego zwraca `(streamoff)*this - (streamoff) right` . Druga funkcja członkowska zwraca wartość `fpos(*this) -= _Off` .

### <a name="example"></a>Przykład

Zobacz [operator! =](#op_neq) , aby uzyskać przykład użycia `operator-` .

## <a name="fposoperator-"></a><a name="operator-_eq"></a>FPOS:: operator-=

Zmniejsza wskaźnik położenia pliku.

```cpp
fpos<Statetype>& operator-=(streamoff _Off);
```

### <a name="parameters"></a>Parametry

*_Off*\
Przesunięcie strumienia.

### <a name="return-value"></a>Wartość zwracana

Funkcja członkowska zwraca wartość `fpos(*this) -= _Off` .

### <a name="remarks"></a>Uwagi

W przypadku pozycjonowania w pliku wynik jest zwykle prawidłowy tylko w przypadku strumieni binarnych, które nie mają kodowania zależnego od stanu.

### <a name="example"></a>Przykład

Zobacz [operator! =](#op_neq) , aby uzyskać przykład użycia `operator-=` .

## <a name="fposoperator"></a><a name="op_eq_eq"></a>FPOS:: operator = =

Testuje wskaźniki położenia plików pod kątem równości.

```cpp
bool operator==(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parametry

*Kliknij*\
Wskaźnik pozycji pliku, względem którego ma zostać wykonane porównanie.

### <a name="return-value"></a>Wartość zwracana

**`true`** Jeśli wskaźniki położenia plików są równe; w przeciwnym razie **`false`** .

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca wartość `(streamoff)*this == (streamoff)right` .

### <a name="example"></a>Przykład

Zobacz [operator! =](#op_neq) , aby uzyskać przykład użycia `operator+=` .

## <a name="fposoperator-streamoff"></a><a name="op_streamoff"></a>FPOS:: operator streamoff —

Rzutowanie obiektu typu `fpos` na obiekt typu `streamoff` .

```cpp
operator streamoff() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca przechowywany obiekt składowej przesunięcia i wszelkie dodatkowe przesunięcie przechowywane jako część `fpos_t` obiektu elementu członkowskiego.

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

## <a name="fposseekpos"></a><a name="seekpos"></a>FPOS:: seekpos

Ta metoda jest używana wewnętrznie tylko w standardowej bibliotece języka C++. Nie wywołuj tej metody z kodu.

```cpp
fpos_t seekpos() const;
```

## <a name="fposstate"></a><a name="state"></a>FPOS:: State

Ustawia lub zwraca stan konwersji.

```cpp
Statetype state() const;

void state(Statetype _State);
```

### <a name="parameters"></a>Parametry

*_State*\
Nowy stan konwersji.

### <a name="return-value"></a>Wartość zwracana

Stan konwersji.

### <a name="remarks"></a>Uwagi

Pierwsza funkcja członkowska zwraca wartość przechowywaną w `St` obiekcie elementu członkowskiego. Druga funkcja członkowska przechowuje *_State* w `St` obiekcie member.

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

[Bezpieczeństwo wątku w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostreams](../standard-library/iostreams-conventions.md)
