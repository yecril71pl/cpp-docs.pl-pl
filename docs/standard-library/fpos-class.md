---
title: fpos — klasa | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- iosfwd/std::fpos
- iosfwd/std::fpos::seekpos
- iosfwd/std::fpos::state
- iosfwd/std::fpos::operator streamoff
dev_langs:
- C++
helpviewer_keywords:
- std::fpos [C++]
- std::fpos [C++], seekpos
- std::fpos [C++], state
ms.assetid: ffd0827c-fa34-47f4-b10e-5cb707fcde47
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ada959218c6a0a8b77fa04373ef8a17be63bd912
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="fpos-class"></a>fpos — Klasa

Klasa szablonu opisuje obiekt, który może przechowywać wszystkie informacje niezbędne do przywrócenia wskaźnik dowolnego położenie pliku w jakimkolwiek strumieniu. Obiekt fpos — klasa\< **St**> skutecznie przechowuje co najmniej dwa obiekty członek:

- Przesunięcie bajtów, typu [streamoff](../standard-library/ios-typedefs.md#streamoff).

- Stan konwersji, do użytku przez obiekt basic_filebuf — klasa, typu **St**, zwykle `mbstate_t`.

Można również przechowywać pozycji dowolnego pliku do użycia przez obiekt klasy [basic_filebuf —](../standard-library/basic-filebuf-class.md), typu `fpos_t`. W środowisku ograniczone pliku o rozmiarze, jednak `streamoff` i `fpos_t` czasami mogą być używane zamiennie. Dla środowiska nie strumieni, których kodowanie zależne od stanu `mbstate_t` faktycznie może być nieużywane. W związku z tym liczba obiektów przechowywane może się różnić.

## <a name="syntax"></a>Składnia

```cpp
template <class Statetype>
class fpos
```

### <a name="parameters"></a>Parametry

*Statetype* informacji o stanie.

### <a name="constructors"></a>Konstruktorów

|Konstruktor|Opis|
|-|-|
|[fpos —](#fpos)|Utwórz obiekt, który zawiera informacje o stanie (przesunięcie) w strumieniu.|

### <a name="member-functions"></a>Funkcje Członkowskie

|Funkcja członkowska|Opis|
|-|-|
|[seekpos](#seekpos)|Używane przez standardowa biblioteka C++ tylko wewnętrznie. Nie wywołuj tej metody w kodzie.|
|[state](#state)|Ustawia lub zwraca stan konwersji.|

### <a name="operators"></a>Operatory

|Operator|Opis|
|-|-|
|[operator!=](#op_neq)|Testy wskaźników położenia pliku pod kątem nierówności.|
|[operator +](#op_add)|Zwiększa wskaźnika położenia pliku.|
|[operator+=](#op_add_eq)|Zwiększa wskaźnika położenia pliku.|
|[operator-](#operator-)|Wskaźnik zmniejsza położenie pliku.|
|[operator-=](#operator-_eq)|Wskaźnik zmniejsza położenie pliku.|
|[operator==](#op_eq_eq)|Testy wskaźników położenia pliku pod kątem równości.|
|[streamoff — operator](#op_streamoff)|Typ obiektu rzutowania `fpos` na obiekt typu `streamoff`.|

## <a name="requirements"></a>Wymagania

**Nagłówek:** \<systemu ios >

**Namespace:** Standard

## <a name="fpos"></a>  fpos::fpos

Utwórz obiekt, który zawiera informacje o stanie (przesunięcie) w strumieniu.

```cpp
fpos(streamoff _Off = 0);

fpos(Statetype _State, fpos_t _Filepos);
```

### <a name="parameters"></a>Parametry

`_Off` Przesunięcie do strumienia.

`_State` Początkowy stan `fpos` obiektu.

*_Filepos* przesunięcie do strumienia.

### <a name="remarks"></a>Uwagi

Pierwszy Konstruktor przechowuje przesunięcie `_Off`względnych na początku pliku i jest w stanie początkowej konwersji (Jeśli który ma znaczenie). Jeśli `_Off` wynosi -1, wynikowy obiekt reprezentuje pozycji nieprawidłowy strumień.

Drugi Konstruktor przechowuje przesunięcia o wartości zero i obiekt `_State`.

## <a name="op_neq"></a>  fpos::operator! =

Testy wskaźników położenia pliku pod kątem nierówności.

```cpp
bool operator!=(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parametry

`right` Wskaźnik położenia pliku za pomocą którego chcesz porównać.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wskaźników położenia pliku nie są takie same, w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zwraca funkcję elementu członkowskiego `!(*this == right)`.

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

Zwiększa wskaźnika położenia pliku.

```cpp
fpos<Statetype> operator+(streamoff _Off) const;
```

### <a name="parameters"></a>Parametry

`_Off` Przesunięcie, w którym mają być zwiększane wskaźnika położenia pliku.

### <a name="return-value"></a>Wartość zwracana

Pozycja w pliku.

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca **fpos — (\*to) +=** `_Off`.

### <a name="example"></a>Przykład

Zobacz [operator! =](#op_neq) przykładowe przy użyciu `operator+`.

## <a name="op_add_eq"></a>  fpos::operator +=

Zwiększa wskaźnika położenia pliku.

```cpp
fpos<Statetype>& operator+=(streamoff _Off);
```

### <a name="parameters"></a>Parametry

`_Off` Przesunięcie, w którym mają być zwiększane wskaźnika położenia pliku.

### <a name="return-value"></a>Wartość zwracana

Pozycja w pliku.

### <a name="remarks"></a>Uwagi

Dodaje funkcję elementu członkowskiego `_Off` przechowywane przesunięcia obiektu, a następnie zwraca  **\*to**. Pozycjonowanie w pliku, aby uzyskać wynik jest zwykle prawidłowe tylko dla danych binarnych strumieni, które nie mają kodowanie zależne od stanu.

### <a name="example"></a>Przykład

Zobacz [operator! =](#op_neq) przykładowe przy użyciu `operator+=`.

## <a name="fpos__operator-"></a>  fpos::operator-

Wskaźnik zmniejsza położenie pliku.

```cpp
streamoff operator-(const fpos<Statetype>& right) const;

fpos<Statetype> operator-(streamoff _Off) const;
```

### <a name="parameters"></a>Parametry

`right` Położenie pliku.

`_Off` Przesunięcia strumienia.

### <a name="return-value"></a>Wartość zwracana

Zwraca pierwszy funkcji członkowskiej `(streamoff)*this - (streamoff) right`. Zwraca drugie funkcji członkowskiej `fpos(*this) -= _Off`.

### <a name="example"></a>Przykład

Zobacz [operator! =](#op_neq) przykładowe przy użyciu `operator-`.

## <a name="fpos__operator-_eq"></a>  fpos::operator-=

Wskaźnik zmniejsza położenie pliku.

```cpp
fpos<Statetype>& operator-=(streamoff _Off);
```

### <a name="parameters"></a>Parametry

`_Off` Przesunięcia strumienia.

### <a name="return-value"></a>Wartość zwracana

Zwraca funkcję elementu członkowskiego `fpos(*this) -= _Off`.

### <a name="remarks"></a>Uwagi

Pozycjonowanie w pliku, aby uzyskać wynik jest zwykle prawidłowe tylko dla danych binarnych strumieni, które nie mają kodowanie zależne od stanu.

### <a name="example"></a>Przykład

Zobacz [operator! =](#op_neq) przykładowe przy użyciu `operator-=`.

## <a name="op_eq_eq"></a>  fpos::operator ==

Testy wskaźników położenia pliku pod kątem równości.

```cpp
bool operator==(const fpos<Statetype>& right) const;
```

### <a name="parameters"></a>Parametry

`right` Wskaźnik położenia pliku za pomocą którego chcesz porównać.

### <a name="return-value"></a>Wartość zwracana

**wartość true,** Jeśli wskaźników położenia pliku są równe; w przeciwnym razie **false**.

### <a name="remarks"></a>Uwagi

Zwraca funkcję elementu członkowskiego `(streamoff)*this == (streamoff)right`.

### <a name="example"></a>Przykład

Zobacz [operator! =](#op_neq) przykładowe przy użyciu `operator+=`.

## <a name="op_streamoff"></a>  fpos::operator streamoff

Rzutowanie obiektu typu `fpos` na obiekt typu `streamoff`.

```cpp
operator streamoff() const;
```

### <a name="remarks"></a>Uwagi

Funkcja członkowska zwraca przechowywanych przesunięcia element członkowski obiektu i wszelkie dodatkowe przesunięcie przechowywane jako część `fpos_t` obiektu elementu członkowskiego.

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

Ta metoda jest używana wewnętrznie przez standardowa biblioteka C++ tylko. Nie wywołuj tej metody w kodzie.

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

`_State` Nowy stan konwersji.

### <a name="return-value"></a>Wartość zwracana

Stan konwersji.

### <a name="remarks"></a>Uwagi

Pierwszy funkcji członkowskiej zwraca wartość przechowywana we **St** obiektu elementu członkowskiego. Drugi magazynów funkcji Członkowskich `_State` w **St** obiektu elementu członkowskiego.

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
