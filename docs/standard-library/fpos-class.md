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
ms.openlocfilehash: 7d60a31e69e8a1ad82086f715cac6dde064d1fac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/14/2020
ms.locfileid: "81359199"
---
# <a name="fpos-class"></a>fpos — Klasa

Szablon klasy opisuje obiekt, który może przechowywać wszystkie informacje potrzebne do przywrócenia dowolnego wskaźnika położenia pliku w dowolnym strumieniu. Obiekt klasy fpos\< **St**> skutecznie przechowuje co najmniej dwa obiekty członkowskie:

- Przesunięcie bajtów typu [streamoff](../standard-library/ios-typedefs.md#streamoff).

- Stan konwersji, do użytku przez obiekt klasy basic_filebuf, `St`typu `mbstate_t`, zazwyczaj .

Może również przechowywać dowolną pozycję pliku, do użytku [basic_filebuf](../standard-library/basic-filebuf-class.md)przez obiekt klasy `fpos_t`basic_filebuf typu . Jednak w przypadku środowiska o `streamoff` ograniczonym rozmiarze pliku i `fpos_t` czasami mogą być używane zamiennie. W środowisku bez strumieni, które mają kodowanie `mbstate_t` zależne od stanu, może być faktycznie nieużywane. W związku z tym liczba przechowywanych obiektów członkowskich może się różnić.

## <a name="syntax"></a>Składnia

```cpp
template <class Statetype>
class fpos
```

### <a name="parameters"></a>Parametry

*Rodzaj stanu*\
informacje o stanie.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[Fpos](#fpos)|Utwórz obiekt zawierający informacje o położeniu (przesunięcie) w strumieniu.|

### <a name="member-functions"></a>Funkcje członkowskie

|Funkcja członkowce|Opis|
|-|-|
|[seekpos](#seekpos)|Używane wewnętrznie tylko przez standardową bibliotekę języka C++. Nie należy wywoływać tej metody z kodu.|
|[Państwa](#state)|Ustawia lub zwraca stan konwersji.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](#op_neq)|Testy wskaźników położenia plików pod kątem nierówności.|
|[operator+](#op_add)|Zwiększa wskaźnik położenia pliku.|
|[operator+=](#op_add_eq)|Zwiększa wskaźnik położenia pliku.|
|[operator-](#operator-)|Zmniejsza wskaźnik położenia pliku.|
|[operator-=](#operator-_eq)|Zmniejsza wskaźnik położenia pliku.|
|[operator==](#op_eq_eq)|Testy wskaźników pozycjonu pliku dla równości.|
|[streamoff operatora](#op_streamoff)|Rzutuje obiekt `fpos` typu na `streamoff`obiekt typu .|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<ios>

**Przestrzeń nazw:** std

## <a name="fposfpos"></a><a name="fpos"></a>fpos::fpos

Utwórz obiekt zawierający informacje o położeniu (przesunięcie) w strumieniu.

```cpp
fpos(streamoff _Off = 0);

fpos(Statetype _State, fpos_t _Filepos);
```

### <a name="parameters"></a>Parametry

*_off*\
Przesunięcie do strumienia.

*_state*\
Stan początkowy `fpos` obiektu.

*_Filepos*\
Przesunięcie do strumienia.

### <a name="remarks"></a>Uwagi

Pierwszy konstruktor przechowuje *_Off*odsunięcia względem początku pliku i w początkowym stanie konwersji (jeśli to ma znaczenie). Jeśli *_Off* jest -1, wynikowy obiekt reprezentuje nieprawidłową pozycję strumienia.

Drugi konstruktor przechowuje przesunięcie zerowe, a obiekt *_State*.

## <a name="fposoperator"></a><a name="op_neq"></a>fpos::operator!=

Testy wskaźników położenia plików pod kątem nierówności.

```cpp
bool operator!=(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parametry

*Prawo*\
Wskaźnik położenia pliku, względem którego można porównać.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli wskaźniki położenia pliku nie są równe, w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Funkcja elementu `!(*this == right)`członkowskiego zwraca .

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

## <a name="fposoperator"></a><a name="op_add"></a>fpos::operator+

Zwiększa wskaźnik położenia pliku.

```cpp
fpos<Statetype> operator+(streamoff _Off) const;
```

### <a name="parameters"></a>Parametry

*_off*\
Przesunięcie, o które chcesz zwiększać wskaźnik położenia pliku.

### <a name="return-value"></a>Wartość zwracana

Pozycja w pliku.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca **fpos(\*this) +=** `_Off`.

### <a name="example"></a>Przykład

Zobacz [operator!=](#op_neq) dla próbki `operator+`za pomocą .

## <a name="fposoperator"></a><a name="op_add_eq"></a>fpos::operator+=

Zwiększa wskaźnik położenia pliku.

```cpp
fpos<Statetype>& operator+=(streamoff _Off);
```

### <a name="parameters"></a>Parametry

*_off*\
Przesunięcie, o które chcesz zwiększać wskaźnik położenia pliku.

### <a name="return-value"></a>Wartość zwracana

Pozycja w pliku.

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego dodaje *_Off* do przechowywanego obiektu elementu członkowskiego odsunięcia, a następnie zwraca ** \*ten**plik . W przypadku pozycjonowania w pliku wynik jest zazwyczaj prawidłowy tylko dla strumieni binarnych, które nie mają kodowania zależnego od stanu.

### <a name="example"></a>Przykład

Zobacz [operator!=](#op_neq) dla próbki `operator+=`za pomocą .

## <a name="fposoperator-"></a><a name="operator-"></a>fpos::operator-

Zmniejsza wskaźnik położenia pliku.

```cpp
streamoff operator-(const fpos<Statetype>& right) const;

fpos<Statetype> operator-(streamoff _Off) const;
```

### <a name="parameters"></a>Parametry

*Prawo*\
Pozycja pliku.

*_off*\
Przesunięcie strumienia.

### <a name="return-value"></a>Wartość zwracana

Zwraca pierwszą `(streamoff)*this - (streamoff) right`funkcję elementu członkowskiego . Druga funkcja elementu `fpos(*this) -= _Off`członkowskiego zwraca .

### <a name="example"></a>Przykład

Zobacz [operator!=](#op_neq) dla próbki `operator-`za pomocą .

## <a name="fposoperator-"></a><a name="operator-_eq"></a>fpos::operator-=

Zmniejsza wskaźnik położenia pliku.

```cpp
fpos<Statetype>& operator-=(streamoff _Off);
```

### <a name="parameters"></a>Parametry

*_off*\
Przesunięcie strumienia.

### <a name="return-value"></a>Wartość zwracana

Funkcja elementu `fpos(*this) -= _Off`członkowskiego zwraca .

### <a name="remarks"></a>Uwagi

W przypadku pozycjonowania w pliku wynik jest zazwyczaj prawidłowy tylko dla strumieni binarnych, które nie mają kodowania zależnego od stanu.

### <a name="example"></a>Przykład

Zobacz [operator!=](#op_neq) dla próbki `operator-=`za pomocą .

## <a name="fposoperator"></a><a name="op_eq_eq"></a>fpos::operator==

Testy wskaźników pozycjonu pliku dla równości.

```cpp
bool operator==(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parametry

*Prawo*\
Wskaźnik położenia pliku, względem którego można porównać.

### <a name="return-value"></a>Wartość zwracana

**true,** jeśli wskaźniki położenia pliku są równe; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Funkcja elementu `(streamoff)*this == (streamoff)right`członkowskiego zwraca .

### <a name="example"></a>Przykład

Zobacz [operator!=](#op_neq) dla próbki `operator+=`za pomocą .

## <a name="fposoperator-streamoff"></a><a name="op_streamoff"></a>fpos::streamoff operatora

Rzut obiektu `fpos` typu do `streamoff`obiektu typu .

```cpp
operator streamoff() const;
```

### <a name="remarks"></a>Uwagi

Funkcja elementu członkowskiego zwraca przechowywany obiekt elementu członkowskiego odsunięcia i wszelkie dodatkowe przesunięcie przechowywane jako część obiektu `fpos_t` członkowskiego.

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

## <a name="fposseekpos"></a><a name="seekpos"></a>fpos::seekpos

Ta metoda jest używana wewnętrznie tylko przez bibliotekę standardową języka C++. Nie należy wywoływać tej metody z kodu.

```cpp
fpos_t seekpos() const;
```

## <a name="fposstate"></a><a name="state"></a>fpos::stan

Ustawia lub zwraca stan konwersji.

```cpp
Statetype state() const;

void state(Statetype _State);
```

### <a name="parameters"></a>Parametry

*_state*\
Nowy stan konwersji.

### <a name="return-value"></a>Wartość zwracana

Stan konwersji.

### <a name="remarks"></a>Uwagi

Funkcja pierwszego elementu członkowskiego zwraca `St` wartość przechowywaną w obiekcie członkowskim. Druga funkcja elementu *_State* członkowskiego przechowuje `St` _State w obiekcie członkowskim.

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

## <a name="see-also"></a>Zobacz też

[Bezpieczeństwo gwintów w standardowej bibliotece języka C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[Programowanie iostream](../standard-library/iostream-programming.md)\
[Konwencje iostream](../standard-library/iostreams-conventions.md)
